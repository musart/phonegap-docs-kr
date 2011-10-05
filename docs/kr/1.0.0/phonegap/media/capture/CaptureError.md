CaptureError
============

> 실패한 media capture 동작으로부터의 에러 코드를 요약한다.

Properties
----------

- __code:__ 아래 나열된 미리 정의한 에러 코드들 중 하나.

Constants
---------

- CaptureError.`CAPTURE_INTERNAL_ERR`: 카메라나 마이크로 폰이 이미지나 오디오를 켑쳐하기 실패했을 경우.
- CaptureError.`CAPTURE_APPLICATION_BUSY`: 카메라 어플리케이션이나 오디오 켑처 어플리케이션이 현재 다른 캡처 요청을 지원하고 있을 경우.
- CaptureError.`CAPTURE_INVALID_ARGUMENT`: API의 잘못된 사용일 경우 (예를 들면, limit 인자는 1보다 작어야 한다.
- CaptureError.`CAPTURE_NO_MEDIA_FILES`: 사용자가 캡처 중에 카메라 어플리케이션이나 오디오 캡처 어플리케이션을 종료한 경우.
- CaptureError.`CAPTURE_NOT_SUPPORTED`: 요청된 capture 동작이 지원 안될 경우.
