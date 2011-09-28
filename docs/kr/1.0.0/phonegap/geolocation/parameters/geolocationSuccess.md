geolocationSuccess
==================

geolocation 위치가 이용할 수 있을 때 호출되는 사용자의 콜백 함수.

    function(position) {
        // 무언가 한다.
    }

Parameters
----------

- __position:__ 기기에 의해 반환되는 geolocation 위치. (`Position`)

Example
-------

    function geolocationSuccess(position) {
        alert('Latitude: '          + position.coords.latitude          + '\n' +
              'Longitude: '         + position.coords.longitude         + '\n' +
              'Altitude: '          + position.coords.altitude          + '\n' +
              'Accuracy: '          + position.coords.accuracy          + '\n' +
              'Altitude Accuracy: ' + position.coords.altitudeAccuracy  + '\n' +
              'Heading: '           + position.coords.heading           + '\n' +
              'Speed: '             + position.coords.speed             + '\n' +
              'Timestamp: '         + new Date(position.timestamp)      + '\n');
    }
