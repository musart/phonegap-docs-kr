geolocation.clearWatch
======================

`watchID` 변수에 의해 참조되는 기기의 위치 변화를 감지하는 것을 멈춘다.

    navigator.geolocation.clearWatch(watchID);

Parameters
----------

- __watchID:__ `watchPosition` 시간 간격을 지우기 위한 id. (String)

설명
-----------

`geolocation.clearWatch` 함수는 `watchID`에 의해 참조되는 `geolocation.watchPosition`을 지움으로써 기기의 위치 변화를 감지하는 것을 멈춘다.

지원하는 플랫폼
-------------------

- Android
- BlackBerry (OS 4.6)
- BlackBerry WebWorks (OS 5.0 and higher)
- iPhone

빠른 예제
-------------

    // Options: 매 3초 마다 위치를 검색한다.
    //
    var watchID = navigator.geolocation.watchPosition(onSuccess, onError, { frequency: 3000 });

    // ...이후에...

    navigator.geolocation.clearWatch(watchID);


전체 예제
------------

    <!DOCTYPE html>
    <html>
      <head>
        <title>Device Properties Example</title>

        <script type="text/javascript" charset="utf-8" src="phonegap.js"></script>
        <script type="text/javascript" charset="utf-8">

        // PhoneGap이 로드되기를 기다린다
        //
        document.addEventListener("deviceready", onDeviceReady, false);

        var watchID = null;

        // PhoneGap이 준비되면 호출된다
        //
        function onDeviceReady() {
            // 매 3초간 업데이트 한다.
            var options = { frequency: 3000 };
            watchID = navigator.geolocation.watchPosition(onSuccess, onError, options);
        }
    
        // onSuccess Geolocation
        //
        function onSuccess(position) {
            var element = document.getElementById('geolocation');
            element.innerHTML = 'Latitude: '  + position.coords.latitude      + '<br />' +
                                'Longitude: ' + position.coords.longitude     + '<br />' +
                                '<hr />'      + element.innerHTML;
        }

        // 이전에 시작된 관찰을 지운다.
        // 
        function clearWatch() {
            if (watchID != null) {
                navigator.geolocation.clearWatch(watchID);
                watchID = null;
            }
        }
    
	    // onError 콜백은 PositionError 객체를 받는다.
	    //
	    function onError(error) {
	      alert('code: '    + error.code    + '\n' +
	            'message: ' + error.message + '\n');
	    }

        </script>
      </head>
      <body>
        <p id="geolocation">Watching geolocation...</p>
    	<button onclick="clearWatch();">Clear Watch</button>     
      </body>
    </html>
