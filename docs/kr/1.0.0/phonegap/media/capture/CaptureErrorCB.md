CaptureErrorCB
==============

> media capture 동작 중에 에러가 발생할 경우 호출된다.

    function captureError( CaptureError error ) { ... };

설명
-----------

이 함수는 media capture 동작을 실행하기 위한 시도를 했는데 캡쳐 어플리케이션이 바쁠 경우, capture 동작이 자리를 잡는 동안 에러가 발생할 경우, 또는 미디어 파일이 캡쳐되기 전에 capture 동작이 사용자에 의해 취소되었을 경우 발생한다.

이 함수는 적절한 에러 코드를 포함한 CaptureError 객체를 가지고 발생된다.

빠른 예제
-------------

    // capture error 콜백
    var captureError = function(error) {
        navigator.notification.alert('Error code: ' + error.code, null, 'Capture Error');
    };
