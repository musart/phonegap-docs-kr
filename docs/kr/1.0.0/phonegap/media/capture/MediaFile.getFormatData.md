MediaFile.getFormatData
=======================

> 미디어 캡쳐 파일에 대한 포멧 정보를 검색한다.

    mediaFile.getFormatData( 
        MediaFileDataSuccessCB successCallback, 
        [MediaFileDataErrorCB errorCallback]
    );

설명
-----------

이 함수는 비동기로 미디어 파일의 포멧 정보를 검색하기를 시도한다. 만약 성공일 경우 MediaFileData 객체와 함께 MeidaFileDataSuccessCB 콜백을 발생한다. 만약 시도가 실패하면, 이 함수는 MediaFileDataErrorCB 콜백을 발생한다.


지원하는 플랫폼
-------------------

- Android
- BlackBerry WebWorks (OS 5.0 and higher)
- iOS

BlackBerry WebWorks Quirks
--------------------------
미디어 파일의 포멧정보를 제공하는 API가 없다. 따라서, 모든 MediaFileData 객체는 기본값들을 반환한다. MediaFileData 문서를 보라.

Android Quirks
--------------
미디어 파일 포멧 정보를 검색하는 API는 제한된다. 따라서, 모든 MediaFileData 속성은 다 지원하지 않는다. MediaFileData 문서를 보라.

iOS Quirks
----------
미디어 파일 포멧 정보를 검색하는 API는 제한된다. 따라서, 모든 MediaFileData 속성을 다 지원하지 않는다. MediaFileData 문서를 보라.
