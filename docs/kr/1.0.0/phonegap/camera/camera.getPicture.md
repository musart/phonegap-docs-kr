camera.getPicture
=================

카메라를 사용하여 사진을 찍거나 기기의 앨범으로부터 사진을 검색한다. 이미지는 base64로 인코딩된 문자열이나 이미지 파일의 URI로 반환된다.

    navigator.camera.getPicture( cameraSuccess, cameraError, [ cameraOptions ] );

설명
-----------

'camera.getPicture' 함수는 기기의 기본 카메라 어플리케이션을 열고, 사용자는 사진을 찍을 수 있다(만약 'Camera.sourceType = Camera.PictureSourceType.CAMERA'일 경우, 디폴트값). 사진이 찍히면, 카메라 어플리케이션은 종료되고 당신의 어플리케이션이 복원된다.

만약 `Camera.sourceType = Camera.PictureSourceType.PHOTOLIBRARY`이나 `Camera.PictureSourceType.SAVEDPHOTOALBUM`이면, 사진 선택 다이얼로그가 나타나고, 앨범내에 사진을 선택할 수 있다.

결과 값은 당신이 정한 'cameraOptions'에 따른 다음 포멧중에 하나에서 `cameraSuccess`함수로 보내질 것이다. 
The return value will be sent to the `cameraSuccess` function, in one of the following formats, depending on the `cameraOptions` you specify:

- - A `String` containing the Base64 encoded photo image (default). 
- A `String` representing the image file location on local storage.  

You can do whatever you want with the encoded image or URI, for example:

- Render the image in an `<img>` tag _(see example below)_
- Save the data locally (`LocalStorage`, [Lawnchair](http://brianleroux.github.com/lawnchair/), etc)
- Post the data to a remote server

Note: The image quality of pictures taken using the camera on newer devices is quite good.  _Encoding such images using Base64 has caused memory issues on some of these devices (iPhone 4, BlackBerry Torch 9800)._  Therefore, using FILE_URI as the 'Camera.destinationType' is highly recommended.

지원하는 플랫폼
-------------------

- Android
- Blackberry WebWorks (OS 5.0 and higher)
- iPhone

빠른 예제
-------------

Take photo and retrieve Base64-encoded image:

    navigator.camera.getPicture(onSuccess, onFail, { quality: 50 }); 

    function onSuccess(imageData) {
        var image = document.getElementById('myImage');
        image.src = "data:image/jpeg;base64," + imageData;
    }

    function onFail(message) {
        alert('Failed because: ' + message);
    }

Take photo and retrieve image file location: 

    navigator.camera.getPicture(onSuccess, onFail, { quality: 50, 
        destinationType: Camera.DestinationType.FILE_URI }); 

    function onSuccess(imageURI) {
        var image = document.getElementById('myImage');
        image.src = imageURI;
    }

    function onFail(message) {
        alert('Failed because: ' + message);
    }


전체 예제
------------

    <!DOCTYPE html>
    <html>
      <head>
        <title>Capture Photo</title>

        <script type="text/javascript" charset="utf-8" src="phonegap.js"></script>
        <script type="text/javascript" charset="utf-8">

        var pictureSource;   // picture source
        var destinationType; // sets the format of returned value 
        
        // Wait for PhoneGap to connect with the device
        //
        document.addEventListener("deviceready",onDeviceReady,false);
    
        // PhoneGap이 준비되면 호출된다 to be used!
        //
        function onDeviceReady() {
            pictureSource=navigator.camera.PictureSourceType;
            destinationType=navigator.camera.DestinationType;
        }

        // Called when a photo is successfully retrieved
        //
        function onPhotoDataSuccess(imageData) {
          // Uncomment to view the base64 encoded image data
          // console.log(imageData);
      
          // Get image handle
          //
          var smallImage = document.getElementById('smallImage');
      
          // Unhide image elements
          //
          smallImage.style.display = 'block';
      
          // Show the captured photo
          // The inline CSS rules are used to resize the image
          //
          smallImage.src = "data:image/jpeg;base64," + imageData;
        }

        // Called when a photo is successfully retrieved
        //
        function onPhotoURISuccess(imageURI) {
          // Uncomment to view the image file URI 
          // console.log(imageURI);
      
          // Get image handle
          //
          var largeImage = document.getElementById('largeImage');
      
          // Unhide image elements
          //
          largeImage.style.display = 'block';
      
          // Show the captured photo
          // The inline CSS rules are used to resize the image
          //
          largeImage.src = imageURI;
        }

        // A button will call this function
        //
        function capturePhoto() {
          // Take picture using device camera and retrieve image as base64-encoded string
          navigator.camera.getPicture(onPhotoDataSuccess, onFail, { quality: 50 });
        }

        // A button will call this function
        //
        function capturePhotoEdit() {
          // Take picture using device camera, allow edit, and retrieve image as base64-encoded string  
          navigator.camera.getPicture(onPhotoDataSuccess, onFail, { quality: 20, allowEdit: true }); 
        }
    
        // A button will call this function
        //
        function getPhoto(source) {
          // Retrieve image file location from specified source
          navigator.camera.getPicture(onPhotoURISuccess, onFail, { quality: 50, 
            destinationType: destinationType.FILE_URI,
            sourceType: source });
        }

        // Called if something bad happens.
        // 
        function onFail(message) {
          alert('Failed because: ' + message);
        }

        </script>
      </head>
      <body>
        <button onclick="capturePhoto();">Capture Photo</button> <br>
        <button onclick="capturePhotoEdit();">Capture Editable Photo</button> <br>
        <button onclick="getPhoto(pictureSource.PHOTOLIBRARY);">From Photo Library</button><br>
        <button onclick="getPhoto(pictureSource.SAVEDPHOTOALBUM);">From Photo Album</button><br>
        <img style="display:none;width:60px;height:60px;" id="smallImage" src="" />
        <img style="display:none;" id="largeImage" src="" />
      </body>
    </html>
