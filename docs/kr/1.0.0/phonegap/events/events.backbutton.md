backbutton
===========

이것은 사용자가 안드로이드에서 이전 버튼을 눌렀을 때 발생하는 이벤트이다.

    document.addEventListener("backbutton", yourCallbackFunction, false);

Details
-------

만약 당신이 안드로이드에서 기본 이전 버튼의 동작보다 우선하는 동작을 하고 싶다면 'backbutton' 이벤트를 위한 이벤트 리스너를 등록할 수 있다. 이전 버튼의 동작보다 우선하기 위해 더 이상 다른 함수를 호출할 필요가 없다. 이제, 당신은 단지 'backbutton'을 위한 이벤트 리스너를 등록하기만 하면 된다.

일반적으로, 당신은 PhoneGap의 'deviceready' 이벤트를 받았을 때 'document.addEventListener'에 이벤트 리스너를 추가하기를 원할 것이다.

지원하는 플랫폼
-------------------

- Android

빠른 예제
-------------

    document.addEventListener("backbutton", onBackKeyDown, false);

    function onBackKeyDown() {
        // 이번 버튼을 처리한다.
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
        // 'deviceready' 이벤트를 호출할 것이다.
        //
        function onDeviceReady() {
            // 이벤트 리스너를 등록한다.
            document.addEventListener("backbutton", onBackKeyDown, false);
        }
        
        // 이전 버튼을 처리한다.
        //
        function onBackKeyDown() {
        }

        </script>
      </head>
      <body>
      </body>
    </html>
