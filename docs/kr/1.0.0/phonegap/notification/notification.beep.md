notification.beep
=================

기기는 삑하는 소리를 재생한다.

    navigator.notification.beep(times);

- __times:__ 삑하는 소리의 반복하는 횟수 (`Number`)

지원하는 플랫폼
-------------------

- Android
- BlackBerry (OS 4.6)
- BlackBerry WebWorks (OS 5.0 and higher)
- iPhone

빠른 예제
-------------

    // 2번 삑 한다!
    navigator.notification.beep(2);

전체 예제
------------

    <!DOCTYPE html>
    <html>
      <head>
        <title>Notification Example</title>

        <script type="text/javascript" charset="utf-8" src="phonegap.js"></script>
        <script type="text/javascript" charset="utf-8">

        // PhoneGap이 로드되기를 기다린다
        //
        document.addEventListener("deviceready", onDeviceReady, false);

        // PhoneGap이 준비되면 호출된다
        //
        function onDeviceReady() {
            // Empty
        }

        // 사용자 경고창을 보여준다
        //
        function showAlert() {
		    navigator.notification.alert(
		        'You are the winner!',  // message
		        'Game Over',            // title
		        'Done'                  // buttonName
		    );
        }

        // 3번 삑한다
        //
        function playBeep() {
            navigator.notification.beep(3);
        }

        // 2초간 진동한다
        //
        function vibrate() {
            navigator.notification.vibrate(2000);
        }

        </script>
      </head>
      <body>
        <p><a href="#" onclick="showAlert(); return false;">Show Alert</a></p>
        <p><a href="#" onclick="playBeep(); return false;">Play Beep</a></p>
        <p><a href="#" onclick="vibrate(); return false;">Vibrate</a></p>
      </body>
    </html>

Android Quirks
--------------

- 안드로이드는 "Settings/Soudn & Display" 메뉴에 지정된 기본 "Notification ringtone"을 재생한다.

iPhone Quirks
-------------

- 삑소리 횟수 관련 변수를 무시한다.
- iPhone에는 네이티브 삑소리 API가 없다.
  - PhoneGap은 media API를 통해 오디오 파일을 재생하여 삑소리를 구현한다.
  - 사용자는 원하는 삑소리 음의 파일을 반드시 제공해야 한다.
  - 이 파일은 30초 안의 파일이어야 하고, 위치는 www/ 의 최상위에 위치하고, 이름은 'beep.wav' 여야 한다.
