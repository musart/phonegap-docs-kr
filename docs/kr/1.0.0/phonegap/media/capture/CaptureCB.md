CaptureCB
=========

> 성공적인 media capture 동작을 기반으로 발생된다.

    function captureSuccess( MediaFile[] mediaFiles ) { ... };

설명
-----------

이 함수는 성공적으로 capture 동작이 완료된 후에 호출된다. 이것은 media 파일이 캡쳐되었다는 의미이고, 사용자가 media 캡처 어플리케이션을 종료했거나 캡쳐 제한에 도달했을 경우이다.

각각의 MediaFile 객체는 캡쳐된 미디어 파일을 설명한다.

빠른 예제
-------------

    // 캡처 콜백
    function captureSuccess(mediaFiles) {
        var i, path, len;
        for (i = 0, len = mediaFiles.length; i < len; i += 1) {
            path = mediaFiles[i].fullPath;
            // 파일 관련된 무언가를 한다.
        }
    };
