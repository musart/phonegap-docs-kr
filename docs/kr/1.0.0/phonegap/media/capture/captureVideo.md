capture.captureVideo
====================

> 비디오 녹화 어플리케이션을 시작하고, 기록된 비디오 클립 파일(들)의 정보를 반환한다.

    navigator.device.capture.captureVideo( 
	    CaptureCB captureSuccess, CaptureErrorCB captureError, [CaptureVideoOptions options]
	);

설명
-----------

이 함수는 기기의 비디오 녹화 어플리케이션을 사용하여 비디오 녹화를 하기 위한 비동기 동작을 시작한다. 이 동작은 기기 사용자에게 하나의 세션에서 다중 녹화를 기록하도록 제공한다.

사용자가 비디오 녹화 어플리케이션을 나가거나 CaptureVideoOptions의 __limit__ 인자에 의해 정의된 녹화의 최대 개수에 도달하면 기록이 끝난다. 만약 __limit__ 인자에 아무런 값도 제공되지 않는다면, 1이 기본값으로 사용되고, capture 동작은 사용자가 하나의 비디오 클립이 녹화된 후 종료될 것이다.

capture 동작이 끝났을 때, 각각의 기록된 비디오 클립 파일들을 설명하는 MediaFile 객체 배열을 담은 CaptureCB 콜백을 호출한다. 만약 동작이 비디오 클립이 기록되기 전에 사용자에 의해 종료되면, CaptureErrorCB 콜백은 CaptureError 객체를 담아 호출된다. 'CAPTURE_NO_MEDIA_FILES' 에러 코드이다.

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

    // capture error 콜백
    var captureError = function(error) {
        navigator.notification.alert('Error code: ' + error.code, null, 'Capture Error');
    };

    // 비디오 캡쳐를 시작한다.
    navigator.device.capture.captureVideo(captureSuccess, captureError, {limit:2});

전체 예제
------------

    <!DOCTYPE html>
    <html>
      <head>
        <title>Capture Video</title>

        <script type="text/javascript" charset="utf-8" src="phonegap.js"></script>
        <script type="text/javascript" charset="utf-8" src="json2.js"></script>
        <script type="text/javascript" charset="utf-8">

        // 캡쳐 동작이 완료되면 호출된다.
        //
        function captureSuccess(mediaFiles) {
            var i, len;
            for (i = 0, len = mediaFiles.length; i < len; i += 1) {
                uploadFile(mediaFiles[i]);
            }	    
        }

        // 만약 무언가 나쁜일이 발생되면 호출된다.
        // 
        function captureError(error) {
	        var msg = 'An error occurred during capture: ' + error.code;
            navigator.notification.alert(msg, null, 'Uh oh!');
        }

        // 버튼은 이 함수를 호출할 것이다.
        //
        function captureVideo() {
            // 기기의 비디오 녹화 어플리케이션을 실행한다.
            // 사용자에게 2개의 비디오 클립을 기록하도록 한다.
            navigator.device.capture.captureVideo(captureSuccess, captureError, {limit: 2});
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
            <button onclick="captureVideo();">Capture Video</button> <br>
        </body>
    </html>

BlackBerry WebWorks Quirks
--------------------------

- PhoneGap for BlackBerry WebWorks는 비디오 녹화를 위해 RIM에서 제공한 __Video Recorder__ 어플리케이션을 실행하기를 시도한다. 어플리케이션이 디바이스에 설치되어 있지 않으면 개발자는 'CAPTURE_NOT_SUPPORTED'라는 에러코드의 CaptureError를 받는다.
