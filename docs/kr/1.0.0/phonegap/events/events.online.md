online
===========

이것은 PhoneGap 어플리케이션이 온라인(인터넷에 연결된 상태)일 경우 발생하는 이벤트이다.

    document.addEventListener("online", yourCallbackFunction, false);

Details
-------

어플리케이션의 네트워크 연결이 온라인으로 변경될 때, online 이벤트는 발생된다.

일반적으로, 당신은 PhoneGap의 `deviceready` 이벤트를 받았을 때 `document.addEventListener`에 이벤트 리스너를 추가하기를 원할 것이다.

지원하는 플랫폼
-------------------

- iOS
- Android
- BlackBerry WebWorks (OS 5.0 and higher)

빠른 예제
-------------

    document.addEventListener("online", onOnline, false);

    function onOnline() {
        // 온라인 이벤트를 처리한다.
    }

전체 예제
------------

    <!DOCTYPE html>
    <html>
      <head>
        <title>PhoneGap Device Ready Example</title>

        <script type="text/javascript" charset="utf-8" src="phonegap.js"></script>
        <script type="text/javascript" charset="utf-8">

        // PhoneGap이 로드되면 onDeviceReady를 호출한다.
        //
        // 이 때, document는 로드되지만 phonegap.js는 로드되지 않는다.
        // PhoneGap이 로드되고 네이티브와 정보를 교환할 때,
        // 'deviceready' 이벤트는 호출된다.
        // 
        document.addEventListener("deviceready", onDeviceReady, false);

        // PhoneGap은 로드되고 PhoneGap 함수들을 호출하기에 안전하다.
        //
        function onDeviceReady() {
		    document.addEventListener("online", onOnline, false);
        }

        // 온라인 이벤트를 처리한다.
        //
        function onOnline() {
        }
        
        </script>
      </head>
      <body>
      </body>
    </html>

iOS Quirks
--------------------------
초기의 startup 중에, 첫 online 이벤트는 (만약 해당한다면,) 발생하는데 적어도 1초정도 걸릴 것이다.
