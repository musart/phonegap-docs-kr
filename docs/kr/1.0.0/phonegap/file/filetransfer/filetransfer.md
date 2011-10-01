FileTransfer
==========

FileTransfer 는 당신이 서버에 파일을 업로드하는 것을 가능하게 하는 객체이다.

Properties
----------

N/A

Methods
-------

- __upload__: 파일을 서버에 보낸다.

Details
-------

`FileTransfer` 객체는 원격서버에 HTTP multi-part POST request를 사용한 파일을 업로드하는 방법을 제공한다. HTTP와 HTTPS 프로토콜 모두 지원한다. 선택적인 인자들은 FileUploadOptions 객체를 upload 함수로 전달할 때 지정된다. 성공적으로 업로드 되면, 성공 콜백이 FileUploadResult 객체를 담아 호출된다. 에러가 발생하면, 에러 콜백이 FileTransferError 객체와 함께 발생한다.

지원하는 플랫폼
-------------------

- Android
- BlackBerry WebWorks (OS 5.0 and higher)
- iOS

빠른 예제
------------------------------
	
	// !! 기기의 text 파일의 유효한 URI를 가진 다양한 fileURI를 가정하라. 
	
  	var win = function(r) {
        console.log("Code = " + r.responseCode);
        console.log("Response = " + r.response);
        console.log("Sent = " + r.bytesSent);
	}
	
    var fail = function(error) {
        alert("An error has occurred: Code = " = error.code);
    }
	
	var options = new FileUploadOptions();
	options.fileKey="file";
	options.fileName=fileURI.substr(fileURI.lastIndexOf('/')+1);
	options.mimeType="text/plain";

    var params = new Object();
	params.value1 = "test";
	params.value2 = "param";
		
	options.params = params;
	
	var ft = new FileTransfer();
    ft.upload(fileURI, "http://some.server.com/upload.php", win, fail, options);
    
전체 예제
------------

    <!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN" "http://www.w3.org/TR/html4/strict.dtd">
    <html>
    <head>
        <title>File Transfer Example</title>
    
        <script type="text/javascript" charset="utf-8" src="phonegap.0.9.4.min.js"></script>
        <script type="text/javascript" charset="utf-8">
            
            // PhoneGap이 로드되기를 기다린다
            //
            document.addEventListener("deviceready", onDeviceReady, false);
            
            // PhoneGap이 준비되면 호출된다
            //
            function onDeviceReady() {
                
                // 지정된 장소로부터 이미지 파일 위치를 얻는다.
                navigator.camera.getPicture(uploadPhoto,
                                            function(message) { alert('get picture failed'); },
                                            { quality: 50, 
                                            destinationType: navigator.camera.DestinationType.FILE_URI,
                                            sourceType: navigator.camera.PictureSourceType.PHOTOLIBRARY }
                                            );
                
            }
            
            function uploadPhoto(imageURI) {
                var options = new FileUploadOptions();
                options.fileKey="file";
                options.fileName=imageURI.substr(imageURI.lastIndexOf('/')+1);
                options.mimeType="image/jpeg";
                
                var params = new Object();
                params.value1 = "test";
                params.value2 = "param";
                
                options.params = params;
                
                var ft = new FileTransfer();
                ft.upload(imageURI, "http://some.server.com/upload.php", win, fail, options);
            }
            
            function win(r) {
                console.log("Code = " + r.responseCode);
                console.log("Response = " + r.response);
                console.log("Sent = " + r.bytesSent);
            }
            
            function fail(error) {
                alert("An error has occurred: Code = " = error.code);
            }
            
            </script>
    </head>
    <body>
        <h1>Example</h1>
        <p>Upload File</p>
    </body>
    </html>

