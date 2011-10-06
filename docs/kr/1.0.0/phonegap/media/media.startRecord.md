media.startRecord
=================

오디오 파일을 녹음하기 시작한다.

    media.startRecord();


설명
-----------

`media.startRecord` 함수는 오디오 파일을 녹음하기 시작하는 동기 함수이다. 

지원하는 플랫폼
-------------------

- Android
- iOS
    
빠른 예제
-------------

    // 오디오를 녹음한다.
    // 
    function recordAudio() {
        var src = "myrecording.mp3";
        var mediaRec = new Media(src,
            // 성공 콜백
            function() {
                console.log("recordAudio():Audio Success");
            },
            
            // 에러 콜백
            function(err) {
                console.log("recordAudio():Audio Error: "+ err.code);
            });

        // 오디오를 녹음한다.
        mediaRec.startRecord();
    }


전체 예제
------------

    <!DOCTYPE html>
    <html>
      <head>
        <title>Device Properties Example</title>

        <script type="text/javascript" charset="utf-8" src="phonegap.js"></script>
        <script type="text/javascript" charset="utf-8">

        // PhoneGap이 로드되기를 기다린다
        //
        document.addEventListener("deviceready", onDeviceReady, false);

        // 오디오를 녹음한다.
        // 
        function recordAudio() {
            var src = "myrecording.mp3";
            var mediaRec = new Media(src, onSuccess, onError);

            // 오디오를 녹음한다.
            mediaRec.startRecord();

            // 10초뒤 녹음을 멈춘다.
            var recTime = 0;
            var recInterval = setInterval(function() {
                recTime = recTime + 1;
                setAudioPosition(recTime + " sec");
                if (recTime >= 10) {
                    clearInterval(recInterval);
                    mediaRec.stopRecord();
                }
            }, 1000);
        }

        // PhoneGap이 준비되면 호출된다
        //
        function onDeviceReady() {
            recordAudio();
        }
    
        // onSuccess Callback
        //
        function onSuccess() {
            console.log("recordAudio():Audio Success");
        }
    
        // onError Callback 
        //
        function onError(error) {
            alert('code: '    + error.code    + '\n' + 
                  'message: ' + error.message + '\n');
        }

        // 오디오 위치를 설정한다.
        // 
        function setAudioPosition(position) {
            document.getElementById('audio_position').innerHTML = position;
        }

        </script>
      </head>
      <body>
        <p id="media">Recording audio...</p>
        <p id="audio_position"></p>
      </body>
    </html>


iOS Quirks
----------

- 녹음을 위한 파일은 존재해야 하고, wav 타입이어야 한다. File API를 사용하여 파일을 생성할 수 있다.
