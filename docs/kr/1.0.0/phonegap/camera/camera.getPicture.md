camera.getPicture
=================

카메라를 사용하여 사진을 찍거나 기기의 앨범으로부터 사진을 검색한다. 이미지는 base64로 인코딩된 문자열이나 이미지 파일의 URI로 반환된다.

    navigator.camera.getPicture( cameraSuccess, cameraError, [ cameraOptions ] );

설명
-----------

'camera.getPicture' 함수는 기기의 기본 카메라 어플리케이션을 열고, 사용자는 사진을 찍을 수 있다(만약 'Camera.sourceType = Camera.PictureSourceType.CAMERA'일 경우, 디폴트값). 사진이 찍히면, 카메라 어플리케이션은 종료되고 당신의 어플리케이션이 복원된다.

만약 `Camera.sourceType = Camera.PictureSourceType.PHOTOLIBRARY`이나 `Camera.PictureSourceType.SAVEDPHOTOALBUM`이면, 사진 선택 다이얼로그가 나타나고, 앨범내에 사진을 선택할 수 있다.

당신이 정한 'cameraOptions'에 따라, 결과값은 다음 중 하나가 `cameraSuccess` 함수로 보내질 것이다. 

- Base64로 암호화된 사진 이미지를 담은 'String'(기본값).
- LocalStorage에 이미지 파일을 나타내는 'String'.

당신이 원하는 암호화된 이미지나 URI로 어떤 것도 할 수 있다, 예를 들면:

- '<img>' 태그 안에서 이미지를 그린다. _(아래 예제 참조)_
- 데이터를 저장한다. ('LocalStorage', [Lawnchair](http://brianleroux.github.com/lawnchair/), 등)
- 데이터를 원격 서버에 게시한다.

Note: 최신 기기의 카메라를 사용하여 찍힌 사진의 이미지 품질은 아주 좋다. _이러한 이미지들을 Base64를 사용하여 임호화하면 일부 기기(iPhone 4, BlackBerry Torch 9800)에서 메모리 이슈를 야기한다. 따라서, 'Camera.destinationType'으로 FILE_URI 사용을 강력하게 권한다.

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
        
        // 기기와 연결하기 위해 PhoneGap을 기다린다.
        //
        document.addEventListener("deviceready",onDeviceReady,false);
    
        // PhoneGap이 준비되면 호출된다.
        //
        function onDeviceReady() {
            pictureSource=navigator.camera.PictureSourceType;
            destinationType=navigator.camera.DestinationType;
        }

        // 사진 데이터가 성공적으로 얻어지면 호출된다.
        //
        function onPhotoDataSuccess(imageData) {
          // base64로 암호화된 이미지를 보려면 주석해제
          // console.log(imageData);
      
          // image handle을 얻는다.
          //
          var smallImage = document.getElementById('smallImage');
      
          // Unhide image elements 
          //
          smallImage.style.display = 'block';
      
          // 캡처된 사진을 보여준다.
          // 이 inline CSS rules 은 이미지 크기를 변경하는데 사용된다.`
          //
          smallImage.src = "data:image/jpeg;base64," + imageData;
        }

        // 사진이 성공적으로 얻어지면 호출된다.
        //
        function onPhotoURISuccess(imageURI) {
          // 파일 URI를 보려면 주석해제
          // console.log(imageURI);
      
          // image handle을 얻는다.
          //
          var largeImage = document.getElementById('largeImage');
      
          // Unhide image elements
          //
          largeImage.style.display = 'block';
      
          // 캡처된 사진을 보여준다.
          // 이 inline CSS rules 은 이미지 크기를 변경하는데 사용된다.`
          //
          largeImage.src = imageURI;
        }

        // 버튼은 이 함수를 호출한다.
        //
        function capturePhoto() {
          // 기기의 카메라를 이용하여 사진을 찍고, base64로 암호화된 문자열의 이미지를 얻는다.
          navigator.camera.getPicture(onPhotoDataSuccess, onFail, { quality: 50 });
        }

        // 버튼은 이 함수를 호출한다.
        //
        function capturePhotoEdit() {
          // 기기의 카메라를 이용하여 사진을 찍고, 수정을 하고, base64로 암호화된 문자열의 이미지를 얻는다.
          navigator.camera.getPicture(onPhotoDataSuccess, onFail, { quality: 20, allowEdit: true }); 
        }
    
        // 버튼은 이 함수를 호출한다.
        //
        function getPhoto(source) {
          // 지정된 위치의 이미지 파일 경로를 얻는다.
          navigator.camera.getPicture(onPhotoURISuccess, onFail, { quality: 50, 
            destinationType: destinationType.FILE_URI,
            sourceType: source });
        }

        // 무언가 잘못되면 호출된다.
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
