resume
===========

이것은 PhoneGap 어플리케이션이 백그라운드에서 되돌아 오면서 발생하는 이벤트이다.

    document.addEventListener("resume", yourCallbackFunction, false);

Details
-------

PhoneGap은 두 개의 코드 기반으로 이루어진다. 네이티브와 자바스크립트이다. 네이티브 코드는 어플리케이션을 백그라운드에서 꺼내는 동안에 resume 에벤트가 발생된다.

일반적으로, 당신은 PhoneGap의 `deviceready` 이벤트를 받았을 때 `document.addEventListener`에 이벤트 리스너를 추가하기를 원할 것이다.

지원하는 플랫폼
-------------------

- Android
- BlackBerry WebWorks (OS 5.0 and higher)
- iPhone

빠른 예제
-------------

    document.addEventListener("resume", onResume, false);

    function onResume() {
        // resume 이벤트를 처리한다.
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
		    document.addEventListener("resume", onResume, false);
        }

        // resume 이벤트를 처리한다.
        //
        function onResume() {
        }
        
        </script>
      </head>
      <body>
      </body>
    </html>
