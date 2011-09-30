CaptureAudioOptions
===================

> 오디오 캡처 설정 옵션을 요악한다.

Properties
----------

- __limit:__ 기기 사용자가 한번의 capture 동작에 녹음할 수 있는 오디오 클립의 최대 갯수. 이 값은 1 이상이어야 한다.(기본값은 1이다.)
- __duration:__ 초 단위의 오디오 사운드 클립의 최대 시간.
- __mode:__ 선택된 오디오 모드. 이 값은 'capture.supportedAudioModes'안에 요소 중 하나와 일치해야 한다.

빠른 예제
-------------

    // capture 동작을 3개의 미디어 파일로 각각은 10초로 제한한다.
    var options = { limit: 3, duration: 10 };

    navigator.device.capture.captureAudio(captureSuccess, captureError, options);

Android Quirks
--------------

- __duration__ 인자는 지원되지 않는다. 녹음 길이는 프로그래밍으로 제한할 수 없다.
- __mode__ 인자는 지원되지 않는다. 오디오 녹음 포멧은 프로그래밍으로 바뀌지 않는다. 녹음은 AMR(Adaptive Multi-Rate) 포멧으로 인코딩된다. (audio/amr).

BlackBerry WebWorks Quirks
--------------------------

- __duration__ 인자는 지원되지 않는다. 녹음 길이는 프로그래밍으로 제한할 수 없다.
- __mode__ 인자는 지원되지 않는다. 오디오 녹음 포멧은 프로그래밍으로 바뀌지 않는다. 녹음은 AMR(Adaptive Multi-Rate) 포멧으로 인코딩된다. (audio/amr).

iOS Quirks
----------

- __limit__ 인자는 지원되지 않는다. 하나의 녹음은 각 호출에 의해 실행된다.
- __mode__ 인자는 지원되지 않는다. 오디오 녹음 포멧은 프로그래밍으로 바뀌지 않는다. 녹음은 WAV(Waveform Audio) 포멧으로 인코딩된다. (audio/wav).
