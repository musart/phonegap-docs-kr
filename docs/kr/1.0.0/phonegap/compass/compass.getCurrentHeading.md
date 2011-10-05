compass.getCurrentHeading
=========================

현재 나침반의 가리키는 방향을 얻어온다.

    navigator.compass.getCurrentHeading(compassSuccess, compassError, compassOptions);

설명
-----------

나침반은 이동 방향이나 기기가 가리키는 방향을 얻어오는 센서이다. 이것은 0도부터 359.99도까지 가리키는 방향을 측정한다.

나침반 heading은 `compassSuccess` 콜백 함수에 의해 반환된다. 

지원하는 플랫폼
-------------------

- Android
- iPhone

빠른 예제
-------------

    function onSuccess(heading) {
        alert('Heading: ' + heading);
    };

    function onError() {
        alert('onError!');
    };

    navigator.compass.getCurrentHeading(onSuccess, onError);

전체 예제
------------

    <!DOCTYPE html>
    <html>
      <head>
        <title>Compass Example</title>

        <script type="text/javascript" charset="utf-8" src="phonegap.js"></script>
        <script type="text/javascript" charset="utf-8">

        // PhoneGap이 로드되기를 기다린다
        //
        document.addEventListener("deviceready", onDeviceReady, false);

        // PhoneGap이 준비되면 호출된다
        //
        function onDeviceReady() {
            navigator.compass.getCurrentHeading(onSuccess, onError);
        }
    
        // onSuccess: 현재의 가리키는 방향을 얻는다.
        //
        function onSuccess(heading) {
            alert('Heading: ' + heading);
        }
    
        // onError: 가리키는 방향을 얻기 실패했을 시
        //
        function onError() {
            alert('onError!');
        }

        </script>
      </head>
      <body>
        <h1>Example</h1>
        <p>getCurrentHeading</p>
      </body>
    </html>
    
