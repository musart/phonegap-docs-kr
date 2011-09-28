accelerometer.getCurrentAcceleration
====================================

x, y 그리고 x축에 대한 현재 가속도를 얻는다.

    navigator.accelerometer.getCurrentAcceleration(accelerometerSuccess, accelerometerError);

설명
-----------

가속도계는 현재 가기의 방향에 관계있는 움직임의 변화(거리)를 감지하는 모션센서이다. 가속도계는 x, y, z축을 통해 3차원 움직임을 감지할 수 있다.

가속도는 accelerometerSuccess콜백 함수를 사용하여 리턴된다.

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
        function onSuccess(acceleration) {
            alert('Acceleration X: ' + acceleration.x + '\n' +
                  'Acceleration Y: ' + acceleration.y + '\n' +
                  'Acceleration Z: ' + acceleration.z + '\n' +
                  'Timestamp: '      + acceleration.timestamp + '\n');
        }
    
        // onError: Failed to get the acceleration
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
    
iPhone Quirks
-------------

- iPhone은 특정 위치의 현재 가속도를 얻어오는 컨셉을 갖고있지 않다.
- 반드시 가속도를 지켜보고 주어진 시간 간격으로 데이터를 가저와야 한다.
- 따라서, 'getCurrentAcceleration' 함수는 PhoneGap의 'watchAccelerometer' 호출로부터 제공된 가장 최근 값을 너에게 줄 것이다.
