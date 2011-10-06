accelerometer.watchAcceleration
===============================

규칙적인 기간동안의 x, y, z축의 가속도를 얻는다.

    var watchID = navigator.accelerometer.watchAcceleration(accelerometerSuccess,
                                                           accelerometerError,
                                                           [accelerometerOptions]);
                                                           
설명
-----------

가속도계는 현재 위치와 관련된 움직임속에서 변화를 감지하는 모션센서이다. 가속도계는 x, y, z 축의 3D 움직임을 감지할 수 있다.

`accelerometer.watchAcceleration`는 기기의 현재 가속도를 규칙적인 시간간격으로 얻는다. 각 시간마다 `Acceleration`이 검색될 때, `accelerometerSuccess` 콜백 함수는 실행된다. `acceleratorOptions` 객체 안에 `frequency` 변수를 통해 1000분의 1초 단위의 간격을 명시한다.

반환된 watch ID는 가속도계 주시 간격을 참고한다. watch ID는 가속도를 지켜보는 것을 멈추기 위해 `accelerometer.clearWatch`와 함께 사용된다.

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

    var options = { frequency: 3000 };  // 매 3초마다 갱신
    
    var watchID = navigator.accelerometer.watchAcceleration(onSuccess, onError, options);

전체 예제
------------

    <!DOCTYPE html>
    <html>
      <head>
        <title>Acceleration Example</title>

        <script type="text/javascript" charset="utf-8" src="phonegap.js"></script>
        <script type="text/javascript" charset="utf-8">

        // watch id는 현재 'watchAcceleration'을 참고한다.
        var watchID = null;
        
        // PhoneGap이 로드되기를 기다린다
        //
        document.addEventListener("deviceready", onDeviceReady, false);

        // PhoneGap이 준비되면 호출된다.
        //
        function onDeviceReady() {
            startWatch();
        }

        // 가속도 관찰을 시작한다.
        //
        function startWatch() {
            
            // 가속도를 매 3초마다 갱신
            var options = { frequency: 3000 };
            
            watchID = navigator.accelerometer.watchAcceleration(onSuccess, onError, options);
        }
        
        // 가속도를 지켜보는 것을 엄춘다.
        //
        function stopWatch() {
            if (watchID) {
                navigator.accelerometer.clearWatch(watchID);
                watchID = null;
            }
        }
        
        // onSuccess: 현재 가속도의 정보를 얻는다.
        //
        function onSuccess(acceleration) {
            var element = document.getElementById('accelerometer');
            element.innerHTML = 'Acceleration X: ' + acceleration.x + '<br />' +
                                'Acceleration Y: ' + acceleration.y + '<br />' +
                                'Acceleration Z: ' + acceleration.z + '<br />' +
                                'Timestamp: '      + acceleration.timestamp + '<br />';
        }

        // onError: 가속도 얻기를 실패했을 경우
        //
        function onError() {
            alert('onError!');
        }

        </script>
      </head>
      <body>
        <div id="accelerometer">Waiting for accelerometer...</div>
      </body>
    </html>
    
 iPhone Quirks
-------------

- 시간간격이 요청될 때, PhoneGap은 성공 콜백 함수를 호출하고, 가속도계 결과를 전달한다.
- 하지만, 기기에 요청할 경우 PhoneGap은 최소 매 40ms와 최대 1000ms의 시간 간격을 제한한다.
  - 예를 들면, 만약 당신이 3초의 시간간격(3000ms)을 요청하면, PhoneGap은 기기로부터 1초의 시간간격을 요청할 것이지만 3초의 요청한 시간 간격으로 성공 콜백을 작동시킬 것이다.
