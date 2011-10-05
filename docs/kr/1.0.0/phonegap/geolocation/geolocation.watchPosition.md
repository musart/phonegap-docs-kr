geolocation.watchPosition
=========================

기기의 현재 위치의 변화를 감지한다.

    var watchId = navigator.geolocation.watchPosition(geolocationSuccess,
                                                      [geolocationError],
                                                      [geolocationOptions]);

Parameters
----------

- __geolocationSuccess__: 현재 위치와 함께 호출되는 콜백.
- __geolocationError__: (선택적인 변수) 만약 에러가 있다면 호출되는 콜백.
- __geolocationOptions__: (선택적인 변수) geolocation 옵션들.

Returns
-------

- __String__: 위치 감시 시간 간격을 참조하는 watch id를 반환한다. watch id는 위치 변화를 감지하는 것을 멈추기 위한 `geolocation.clearWatch`와 함께 사용될 수 있다.

설명
-----------

`geolocation.watchPosition`은 비동기 함수이다. 위치의 변화가 감지되었을 때 기기의 현재 위치를 반환한다. 기기가 새로운 위치를 검색할 때, `geolocationSuccess`콜백은 `Position`겍체를 파라미터로 하여 호출된다. 만약 에러가 있다면, `geolocationError`콜백이 `PositionError`객체와 함께 호출된다.

지원하는 플랫폼
-------------------

- Android
- BlackBerry (OS 4.6)
- BlackBerry WebWorks (OS 5.0 and higher)
- iPhone

빠른 예제
-------------

    // onSuccess Callback
    //   이 함수는 현재 GPS의 좌표를 담고있는 'Position' 객채를 받는다.
    //
    function onSuccess(position) {
        var element = document.getElementById('geolocation');
        element.innerHTML = 'Latitude: '  + position.coords.latitude      + '<br />' +
                            'Longitude: ' + position.coords.longitude     + '<br />' +
                            '<hr />'      + element.innerHTML;
    }

    // onError 콜백은 PositionError 객체를 받는다.
    //
    function onError(error) {
        alert('code: '    + error.code    + '\n' +
              'message: ' + error.message + '\n');
    }

    // Options: 3초마다 위치를 검색한다.
    //
    var watchID = navigator.geolocation.watchPosition(onSuccess, onError, { frequency: 3000 });
    

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
      </body>
    </html>
