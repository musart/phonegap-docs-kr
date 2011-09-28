notification.vibrate
====================

지정된 시간동안 기기를 진동한다.

    navigator.notification.vibrate(milliseconds)

- __time:__ 기기를 진동하기 위한 1000분의 1초 단위 시간. 1000 milliseconds 은 1 초와 같다. (`Number`)

지원하는 플랫폼
-------------------

- Android
- BlackBerry (OS 4.6)
- BlackBerry WebWorks (OS 5.0 and higher)
- iPhone

빠른 예제
-------------

    // 2.5초간 진동한다.
    //
    navigator.notification.vibrate(2500);

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
    
        // 사용자 알림창을 보여준다.
        //
        function showAlert() {
		    navigator.notification.alert(
		        'You are the winner!',  // message
		        'Game Over',            // title
		        'Done'                  // buttonName
		    );
        }
    
        // 3번 삑소리낸다.
        //
        function playBeep() {
            navigator.notification.beep(3);
        }
    
        // 2초동안 진동한다.
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

iPhone Quirks
-------------

- __time:__ time을 무시하고 미리 정의된 시간 동안 진동한다.

        navigator.notification.vibrate();
        navigator.notification.vibrate(2500);   // 2500 is ignored
