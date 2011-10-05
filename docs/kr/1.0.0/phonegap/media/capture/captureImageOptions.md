CaptureImageOptions
===================

> 이미지 캡쳐 설정 옵션을 요약한다.

Properties
----------

- __limit:__ 기기 사용자가 한번의 capture 동작에 캡쳐할 수 있는 이미지의 최대 개수. 이 값은 1 이상이어야 한다.(기본값은 1이다.)
- __mode:__ 선택된 이미지 모드. 이 값은 `capture.supportedImageModes`안에 요소 중 하나와 일치해야 한다.

빠른 예제
-------------

    // capture 동작을 3개의 이미지로 제한한다.
    var options = { limit: 3 };

    navigator.device.capture.captureImage(captureSuccess, captureError, options);

Android Quirks
--------------

- __mode__ 인자는 지원되지 않는다. 이미지 크기와 포멧은 프로그래밍으로 바뀌지 않는다. 이미지들은 JPEG 포멧으로 저장된다. (image/jpeg).

BlackBerry WebWorks Quirks
--------------------------

- __mode__ 인자는 지원되지 않는다. 이미지 크기와 포멧은 프로그래밍으로 바뀌지 않는다. 하지만, 이미지 크기는 기기 사용자에 의해 바뀔 수 있다. 이미지는 JPEG 포멧으로 저장된다. (image/jpeg).

iOS Quirks
----------

- __limit__ 인자는 지원되지 않는다. 하나의 이미지는 각 호출에 의해 얻어진다.
- __mode__ 인자는 지원되지 않는다. 이미지 크기와 포멧은 프로그래밍으로 바뀌지 않는다. 이미지는 JPEG 포멧으로 저장된다. (image/jpeg).
