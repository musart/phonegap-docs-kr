accelerometerSuccess
====================

가속도 정보를 제공하는 onSuccess 콜백 함수.

    function(acceleration) {
        // Do something
    }

Parameters
----------

- __acceleration:__ 특정한 순간의 가속도. (Acceleration)

Example
-------

    function onSuccess(acceleration) {
        alert('Acceleration X: ' + acceleration.x + '\n' +
              'Acceleration Y: ' + acceleration.y + '\n' +
              'Acceleration Z: ' + acceleration.z + '\n' +
              'Timestamp: '      + acceleration.timestamp + '\n');
    };
