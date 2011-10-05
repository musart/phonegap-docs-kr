Position
========

geolocation API에 의해 생성된 `Position` 좌표를 포함한다.

Properties
----------

- __coords:__ 지리적인 좌표 세트. _(Coordinates)_
- __timestamp:__ 1000분의 1초 단위의 `coords`위한 생성된 timestamp. _(DOMTimeStamp)_

설명
-----------

`Position` 객체는 PhoneGap에 의해 생성되고 채워지고, 콜백함수를 통해 사용자에게 반환된다.

지원하는 플랫폼
-------------------

- Android
- BlackBerry (OS 4.6)
- BlackBerry WebWorks (OS 5.0 and higher)
- iPhone

빠른 예제
-------------

    // onSuccess Callback
    //
    var onSuccess = function(position) {
        alert('Latitude: '          + position.coords.latitude          + '\n' +
              'Longitude: '         + position.coords.longitude         + '\n' +
              'Altitude: '          + position.coords.altitude          + '\n' +
              'Accuracy: '          + position.coords.accuracy          + '\n' +
              'Altitude Accuracy: ' + position.coords.altitudeAccuracy  + '\n' +
              'Heading: '           + position.coords.heading           + '\n' +
              'Speed: '             + position.coords.speed             + '\n' +
              'Timestamp: '         + new Date(position.timestamp)      + '\n');
    };

    // PositionError 객체를 받은 onError 콜백
    //
    function onError(error) {
        alert('code: '    + error.code    + '\n' +
              'message: ' + error.message + '\n');
    }

    navigator.geolocation.getCurrentPosition(onSuccess, onError);

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

        // PhoneGap이 준비되면 호출된다
        //
        function onDeviceReady() {
            navigator.geolocation.getCurrentPosition(onSuccess, onError);
        }
    
        // onSuccess Geolocation
        //
        function onSuccess(position) {
            var element = document.getElementById('geolocation');
            element.innerHTML = 'Latitude: '           + position.coords.latitude              + '<br />' +
                                'Longitude: '          + position.coords.longitude             + '<br />' +
                                'Altitude: '           + position.coords.altitude              + '<br />' +
                                'Accuracy: '           + position.coords.accuracy              + '<br />' +
                                'Altitude Accuracy: '  + position.coords.altitudeAccuracy      + '<br />' +
                                'Heading: '            + position.coords.heading               + '<br />' +
                                'Speed: '              + position.coords.speed                 + '<br />' +
                                'Timestamp: '          + new Date(position.timestamp)          + '<br />';
        }
    
	    // PositionError 객체를 받은 onError 콜백
	    //
	    function onError(error) {
	        alert('code: '    + error.code    + '\n' +
	              'message: ' + error.message + '\n');
	    }

        </script>
      </head>
      <body>
        <p id="geolocation">Finding geolocation...</p>
      </body>
    </html>

iPhone Quirks
-------------

- __timestamp:__ 1000분의 1초 대신 1초를 사용한다.

대안은 수동으로 타임스템프를 1000분의 1초로 변경한다 (x 1000):

        var onSuccess = function(position) {
            alert('Latitude: '  + position.coords.latitude             + '\n' +
                  'Longitude: ' + position.coords.longitude            + '\n' +
                  'Timestamp: ' + new Date(position.timestamp * 1000)  + '\n');
        };
