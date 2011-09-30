CaptureCB
=========

> Invoked upon a successful media capture operation.

    function captureSuccess( MediaFile[] mediaFiles ) { ... };

설명
-----------

이 함수는 성공적으로 캡쳐 동작이 완료된 후에 호출된다. 이것은 media 파일이 캡쳐되었다는 의미이고, 사용자는 media 캡처 어플리케이션을 종료하거나 캡쳐 제한에 다다를 수 있다.
This function is invoked after a successful capture operation has completed.  This means a media file has been captured, and either the user has exited the media capture application, or the capture limit has been reached.

Each MediaFile object describes a captured media file.  

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
