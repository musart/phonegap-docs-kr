Coordinates
===========

position의 지리적인 좌표를 표한한 속성 세트.

Properties
----------

* __latitude__: 소수값의 위도. _(Number)_
* __longitude__: 소수값의 경도. _(Number)_
* __altitude__: 지표면 위의 미터 단위의 위치의 높이. _(Number)_
* __accuracy__: 미터 단위로 위도와 경도 좌표의 정확도 수준. _(Number)_
* __altitudeAccuracy__: 미터 단위로 고도 좌표의 정확도 수준. _(Number)_
* __heading__: 진북 방향과 비교하여 시계방향으로 계산된 각도로 명시된 이동의 방향. _(Number)_
* __speed__: 초당 미터 단위로 지정된 기기의 현재 대지 속도. _(Number)_

설명
-----------

`Coordinates` 객체는 PhoneGap에 의해 생성되고 채워진다. 또 `Position` 객체가 추가된다. `Position` 객체는 콜백 함수를 통해 사용자에게 반환된다.

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

    // onError Callback
    //
    var onError = function() {
        alert('onError!');
    };

    navigator.geolocation.getCurrentPosition(onSuccess, onError);

전체 예제
------------

    <!DOCTYPE html>
    <html>
      <head>
        <title>Geolocation Position Example</title>
        <script type="text/javascript" charset="utf-8" src="phonegap.js"></script>
        <script type="text/javascript" charset="utf-8">

        // PhoneGap이 로드되기를 기다리기 위해 이벤트를 등록한다.
        //
        document.addEventListener("deviceready", onDeviceReady, false);

        // PhoneGap이 로드되고 준비된다.
        //
        function onDeviceReady() {
            navigator.geolocation.getCurrentPosition(onSuccess, onError);
        }
    
        // geolocation으로부터의 `Position` 속성을 표시한다.
        //
        function onSuccess(position) {
            var div = document.getElementById('myDiv');
        
            div.innerHTML = 'Latitude: '             + position.coords.latitude  + '<br/>' +
                            'Longitude: '            + position.coords.longitude + '<br/>' +
                            'Altitude: '             + position.coords.altitude  + '<br/>' +
                            'Accuracy: '             + position.coords.accuracy  + '<br/>' +
                            'Altitude Accuracy: '    + position.coords.altitudeAccuracy  + '<br/>' +
                            'Heading: '              + position.coords.heading   + '<br/>' +
                            'Speed: '                + position.coords.speed     + '<br/>';
        }
    
        // 만약 geolocation을 얻는데 문제가 있으면 알림창을 보여준다.
        //
        function onError() {
            alert('onError!');
        }

        </script>
      </head>
      <body>
        <div id="myDiv"></div>
      </body>
    </html>
    
Android Quirks
-------------

__altitudeAccuracy:__ 이 속성은 안드로이드 기기에서 지원되지 않고, 항상 null을 반환한다.
