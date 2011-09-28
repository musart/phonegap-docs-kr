compass.clearWatch
========================

watch ID 변수에 의해 참조되는 나침반을 관찰하기를 멈춘다.
Stop watching the compass referenced by the watch ID parameter.

    navigator.compass.clearWatch(watchID);

- __watchID__: `compass.watchHeading`에 의해 반환되는 ID.

지원하는 플랫폼
-------------------

- Android
- iPhone

빠른 예제
-------------

    var watchID = navigator.compass.watchHeading(onSuccess, onError, options);
    
    // ... 나중에 ...
    
    navigator.compass.clearWatch(watchID);
    
전체 예제
------------

    <!DOCTYPE html>
    <html>
      <head>
        <title>Compass Example</title>

        <script type="text/javascript" charset="utf-8" src="phonegap.js"></script>
        <script type="text/javascript" charset="utf-8">

        // 현재 `watchHeading`에 의해 참조되는 watch id
        var watchID = null;
        
        // PhoneGap이 로드되기를 기다린다
        //
        document.addEventListener("deviceready", onDeviceReady, false);

        // PhoneGap이 준비되면 호출된다
        //
        function onDeviceReady() {
            startWatch();
        }

        // 나침반을 지커보기를 시작한다.
        //
        function startWatch() {
            
            // 매 3초간 나침반을 갱신한다.
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
        
        // onSuccess: 현재 가리키는 방향을 얻어온다.
        //
        function onSuccess(heading) {
            var element = document.getElementById('heading');
            element.innerHTML = 'Heading: ' + heading;
        }

        // onError: 가리키는 방향을 얻어오는데 실패할 경우
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
