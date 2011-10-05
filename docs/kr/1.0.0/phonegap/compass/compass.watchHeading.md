compass.watchHeading
====================

규칙적인 시간간격에서, 각도에 따른 나침반의 가리키는 방향을 얻는다.

    var watchID = navigator.compass.watchHeading(compassSuccess, compassError, [compassOptions]);
                                                           
설명
-----------

나침반은 이동 방향이나 기기가 가리키는 방향을 감지하는 센서이다. 이것은 가리키는 방향을 0도에서 359.99도까지 측정한다.

`compass.watchHeading`은 기기의 현재 가리키는 방향을 규칙적인 시간간격으로 얻는다. 각 시간간격마다 가리키는 방향을 얻을 때, `headingSuccess`콜백 함수는 실행된다. `compassOptions`객체 안에 `frequency`변수를 통해 1000분의 1초 단위의 간격을 명시한다.

반환된 watch ID는 compass watch 시간 간격을 참고한다. watch ID는 나참반을 지켜보는 것을 멈추기 위해 `compass.clearWatch`와 함께 사용된다.

지원하는 플랫폼
-------------------

- Android
- iPhone


빠른 예제
-------------

    function onSuccess(heading) {
        var element = document.getElementById('heading');
        element.innerHTML = 'Heading: ' + heading;
    };

    function onError() {
        alert('onError!');
    };

    var options = { frequency: 3000 };  // 매 3초간 갱신한다.
    
    var watchID = navigator.compass.watchHeading(onSuccess, onError, options);

전체 예제
------------

    <!DOCTYPE html>
    <html>
      <head>
        <title>Compass Example</title>

        <script type="text/javascript" charset="utf-8" src="phonegap.js"></script>
        <script type="text/javascript" charset="utf-8">

        // The watch id references the current `watchHeading`
        var watchID = null;
        
        // PhoneGap이 로드되기를 기다린다
        //
        document.addEventListener("deviceready", onDeviceReady, false);

        // PhoneGap이 준비되면 호출된다
        //
        function onDeviceReady() {
            startWatch();
        }

        // 나침반을 지켜보기를 시작한다.
        //
        function startWatch() {
            
            // 매 3초간 나참반을 갱신한다.
            var options = { frequency: 3000 };
            
            watchID = navigator.compass.watchHeading(onSuccess, onError, options);
        }
        
        // 나침반을 지켜보기를 멈춘다.
        //
        function stopWatch() {
            if (watchID) {
                navigator.compass.clearWatch(watchID);
                watchID = null;
            }
        }
        
        // onSuccess: 현재 가리키는 방향을 얻는다.
        //
        function onSuccess(heading) {
            var element = document.getElementById('heading');
            element.innerHTML = 'Heading: ' + heading;
        }

        // onError: 가리키는 방향을 얻기 실패할 경우
        //
        function onError() {
            alert('onError!');
        }

        </script>
      </head>
      <body>
        <div id="heading">Waiting for heading...</div>
        <button onclick="startWatch();">Start Watching</button>
        <button onclick="stopWatch();">Stop Watching</button>
      </body>
    </html>
    
