deviceready
===========

이것은 PhoneGap이 완전히 로드될때 발생하는 이벤트이다.

    document.addEventListener("deviceready", yourCallbackFunction, false);

Details
-------

이것은 모든 PhoneGap 어플리케이션이 반드시 사용하는 매우 중요한 이벤트이다.

PhoneGap은 두 개의 코드 기반으로 이루어진다. 네이티브와 자바스크립트이다. 네이티브 코드는 로딩될 때, 사용자 로딩 이미지는 표시된다. 하지만, 자바스크립트는 DOM이 로드할 때 한번 로드된다. 이것은 당신의 웹 어플리케이션이 잠제적으로 PhoneGap 자바스크립트가 로드되기 전에 이 함수를 호출할 수 있다는 것을 의미한다.

PhoneGap의 `deviceready` 이벤트는 PhoneGap이 완전히 로드될때 한번 발생한다. device가 발생한 이후에 당신은 안전하게 PhoneGap 함수를 호출할 수 있다.

일반적으로, 당신은 HTML 문서의 DOM이 로드될 때 `document.addEventListener`에 이벤트 리스너를 추가하고 싶을 것이다.

지원하는 플랫폼
-------------------

- Android
- BlackBerry WebWorks (OS 5.0 and higher)
- iPhone

빠른 예제
-------------

    document.addEventListener("deviceready", onDeviceReady, false);

    function onDeviceReady() {
        // 이제 안전하게 PhoneGap API를 사용한다.
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

        // PhoneGap은 로드되고 PhoneGap 함수를 안전하게 호출한다.
        //
        function onDeviceReady() {
            // 이제 안전하게 PhoneGap API를 사용한다.
        }

        </script>
      </head>
      <body>
      </body>
    </html>
    
BlackBerry (OS 4.6) Quirks
--------------------------

사용자 이벤트들은 RIM BrowserField(web browser view)에서 지원되지 않으므로, `deviceready` 이벤트는 절대로 발생하지 않는다.

다른 해결책으로 PhoneGap이 완전히 로드될때 까지 `PhoneGap.available`을 수동적으로 쿼리하는 것이다.

    function onLoad() {
        // BlackBerry OS 4 브라우저는 이벤트를 지원하지 않는다.
        // 따라서, 수동적으로 PhoneGap이 사용 가능할 때까지 기다린다.
        //
        var intervalID = window.setInterval(
          function() {
              if (PhoneGap.available) {
                  window.clearInterval(intervalID);
                  onDeviceReady();
              }
          },
          500
        );
    }

    function onDeviceReady() {
        // 이제 안전하게 PhoneGap API를 사용한다.
    }
