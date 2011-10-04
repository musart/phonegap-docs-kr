Acceleration
============

특정 시간에 얻어진 `Accelerometer` 값을 담고 있다.

Properties
----------

- __x:__ x축의 모션 값. 범위 [0, 1] (`Number`)
- __y:__ y축의 모션 값. 범위 [0, 1] (`Number`)
- __z:__ z축의 모션 값. 범위 (`Number`)
- __timestamp:__ 1000분의 1초 단위로 생성된 timestamp (`DOMTimeStamp`)

설명
-----------

이 객체는 PhoneGap에 의해 생성되고 `Accelerometer` 메소드에 의해 반환된다.

지원하는 플랫폼
-------------------

- Android
- BlackBerry WebWorks (OS 5.0 and higher)
- iPhone

빠른 예제
-------------

    function onSuccess(acceleration) {
        alert('Acceleration X: ' + acceleration.x + '\n' +
              'Acceleration Y: ' + acceleration.y + '\n' +
              'Acceleration Z: ' + acceleration.z + '\n' +
              'Timestamp: '      + acceleration.timestamp + '\n');
    };

    function onError() {
        alert('onError!');
    };

    navigator.accelerometer.getCurrentAcceleration(onSuccess, onError);

전체 예제
------------

    <!DOCTYPE html>
    <html>
      <head>
        <title>Acceleration Example</title>

        <script type="text/javascript" charset="utf-8" src="phonegap.js"></script>
        <script type="text/javascript" charset="utf-8">

        // PhoneGap이 로드되기를 기다린다.
        //
        document.addEventListener("deviceready", onDeviceReady, false);

        // PhoneGap이 준비되면 호출된다.
        //
        function onDeviceReady() {
            navigator.accelerometer.getCurrentAcceleration(onSuccess, onError);
        }

        // onSuccess: 현재 가속도 정보를 얻는다.
        //
        function onSuccess() {
            alert('Acceleration X: ' + acceleration.x + '\n' +
                  'Acceleration Y: ' + acceleration.y + '\n' +
                  'Acceleration Z: ' + acceleration.z + '\n' +
                  'Timestamp: '      + acceleration.timestamp + '\n');
        }

        // onError: 가속도 정보를 얻는데 실패
        //
        function onError() {
            alert('onError!');
        }

        </script>
      </head>
      <body>
        <h1>Example</h1>
        <p>getCurrentAcceleration</p>
      </body>
    </html>
