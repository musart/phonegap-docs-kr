capture.captureImage
====================

> 카메라 어플리케이션을 시작하고 기록된 이미지 파일(들)에 대한 정보를 반환한다.

    navigator.device.capture.captureImage( 
	    CaptureCB captureSuccess, CaptureErrorCB captureError, [CaptureImageOptions options]
	);

설명
-----------

이 함수는 기기의 카메라 어플리케여선을 사용하여 이미지를 캡쳐하기 위한 비동기 동작을 수행한다. 이 동작은 기기의 사용자에게 한 세션안에서 다중 이미지를 캡쳐 가능하게 한다.

캡쳐 동작은 사용자가 카메라 어플리케이션을 나가거나, CaptureImageOptions의 __limit__ 인자에 정의된 이미지의 최대 갯수에 도달했을 때 끝난다. 만약 __limit__ 인자에 아무값도 없을 경우, 기본값인 1이 사용되고, 캡쳐 동작은 사용자가 하나의 이미지를 켑쳐한 뒤 종료될 것이다.

캡쳐 동작이 끝났을 때, 각각의 캡쳐된 이미지 파일을 설명하는 MediaFile 객체의 배열을 담은 CaptureCB를 호출한다. 만약 이 동작이 이미지가 캡쳐되기 전에 사용자에 의해 종료될 경우, CaptureErrorCB 콜백은 CaptureError 객체를 담아 호출된다. `CAPTURE_NO_MEDIA_FILES` 에러코드이다.

지원하는 플랫폼
-------------------

- Android
- BlackBerry WebWorks (OS 5.0 and higher)
- iOS

빠른 예제
-------------

    // capture 콜백
    var captureSuccess = function(mediaFiles) {
        var i, path, len;
        for (i = 0, len = mediaFiles.length; i < len; i += 1) {
            path = mediaFiles[i].fullPath;
            // 파일 관련된 무언가를 한다.
        }
    };

    // capture 에러 콜백
    var captureError = function(error) {
        navigator.notification.alert('Error code: ' + error.code, null, 'Capture Error');
    };

    // 이미지 캡쳐를 시작한다.
    navigator.device.capture.captureImage(captureSuccess, captureError, {limit:2});

전체 예제
------------

    <!DOCTYPE html>
    <html>
      <head>
        <title>Capture Image</title>

        <script type="text/javascript" charset="utf-8" src="phonegap.js"></script>
        <script type="text/javascript" charset="utf-8" src="json2.js"></script>
        <script type="text/javascript" charset="utf-8">

        // 캡처 동작이 끝났을 때 불린다.
        //
        function captureSuccess(mediaFiles) {
            var i, len;
            for (i = 0, len = mediaFiles.length; i < len; i += 1) {
                uploadFile(mediaFiles[i]);
            }	    
        }

        // 만약 나쁜일이 발생하면 호출된다.
        // 
        function captureError(error) {
	        var msg = 'An error occurred during capture: ' + error.code;
            navigator.notification.alert(msg, null, 'Uh oh!');
        }

        // 버튼은 이 함수를 호출할 것이다.
        //
        function captureImage() {
            // 기기의 카메라 어플리케이션을 실행한다.
            // 사용자에게 2개의 이미지를 캡쳐 가능하게 한다.
            navigator.device.capture.captureImage(captureSuccess, captureError, {limit: 2});
        }

        // 파일을 서버에 업로드 한다.
        function uploadFile(mediaFile) {
            var ft = new FileTransfer(),
                path = mediaFile.fullPath,
                name = mediaFile.name;

            ft.upload(path,
                "http://my.domain.com/upload.php",
                function(result) {
                    console.log('Upload success: ' + result.responseCode);
                    console.log(result.bytesSent + ' bytes sent');
                },
                function(error) {
                    console.log('Error uploading file ' + path + ': ' + error.code);
                },
                { fileName: name });   
        }

        </script>
        </head>
        <body>
            <button onclick="captureImage();">Capture Image</button> <br>
        </body>
    </html>


