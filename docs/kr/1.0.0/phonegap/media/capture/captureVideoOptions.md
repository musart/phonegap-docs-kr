CaptureVideoOptions
===================

> 비디오 캡쳐 설정 옵션을 요약한다.

Properties
----------

- __limit:__ 기기 사용자가 한번의 capture 동작에 녹화할 수 있는 비디오 클립의 최대 개수. 이 값은 1 이상이어야 한다.(기본값은 1이다.)
- __duration:__ 초 단위의 비디오 클립의 최대 시간.
- __mode:__ 선택된 비디오 캡쳐 모드. 이 값은 `capture.supportedVideoModes`안에 요소 중 하나와 일치해야 한다.

빠른 예제
-------------

    // capture 동작을 3개의 비디오 클립으로 제한한다.
    var options = { limit: 3 };

    navigator.device.capture.captureVideo(captureSuccess, captureError, options);

Android Quirks
--------------

- __duration__ 인자는 지원되지 않는다. 녹화의 길이는 프로그래밍으로 제한할 수 없다.
- __mode__ 인자는 지원되지 않는다. 비디오 크기와 포멧은 프로그래밍으로 바꿀 수 없다; 하지만, 이 인자들은 기기 사용자에 의해 바뀐다. 자동적으로 비디오들은 3GPP(video/3gpp) 포멧으로 녹화된다.

BlackBerry WebWorks Quirks
--------------------------

- __duration__ 인자는 지원되지 않는다. 녹화의 길이는 프로그래밍으로 제한되지 않는다.
- __mode__ 인자는 지원되지 않는다. 비디오 길이와 포멧은 프로그래밍으로 바뀌지 않는다: 하지만, 이 인자들은 기기 사용자에 의해 바뀐다. 자동적으로 비디오들은 3GPP (video/3gpp) 포멧으로 녹화된다.

iOS Quirks
----------

- __limit__ 인자는 지원되지 않는다. 하나의 비디오는 각 호출에 의해 실행된다.
- __duration__ 인자는 지원되지 않는다. 녹화 길이는 프로그래밍으로 제한되지 않는다.
- __mode__ 인는 지원되지 않는다. 비디오 크기와 포멧은 프로그래밍으로 제한되지 않는다. 자동적으로 비디오들은 (video/quicktime) 포멧으로 녹화된다.

