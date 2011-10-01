MediaFileData
=============

> 미디어 파일의 포멧 정보를 요약한다.

Properties
----------

- __codecs:__ 오디오와 비디오의 실제 포멧. (DOMString)
- __bitrate:__ 컨텐츠의 평균 bitrate. 이미지의 경우 이 속성은 0이다. (Number)
- __height:__ 이미지나 비디오의 픽셀단위의 높이. 오디오 클립의 경우 이 속성은 0이다. (Number)
- __width:__ 이미지나 비디오의 픽셀단위의 넓이. 오디오 클립의 경우 이 속성은 0이다. (Number)
- __duration:__ 비디오나 사운드 클립의 초단위의 길이. 이미지의 경우 이 속성은 0이다. (Number)

BlackBerry WebWorks Quirks
--------------------------
미디어 파일의 포멧 정보를 제공하는 API가 없다. 따라서 MediaFile.getFormatData 함수에 의해 반환되는 MediaFileData 객체는 다음의 기본값을 갖는다.

- __codecs:__ 지원되지 않는다. 이 속성은 항상 null이다.
- __bitrate:__ 지원되지 않는다. 이 속성은 항상 0이다.
- __height:__ 지원되지 않는다. 이 속성은 항상 0이다.
- __width:__ 지원되지 않는다. 이 속성은 항상 0이다.
- __duration:__ 지원되지 않는다. 이 속성은 항상 0이다.

Android Quirks
--------------
MediaFileData 속성을 다음과 같이 지원한다:

- __codecs:__ 지원되지 않는다. 이 속성은 항상 null이다.
- __bitrate:__ 지원되지 않는다. 이 속성은 항상 0이다.
- __height:__ 지원된다.  (이미지와 비디오 파일만).  
- __width:__ 지원된다.  (이미지와 비디오 파일만). 
- __duration:__ 지원된다.  (오디오와 비디오 파일만).

iOS Quirks
----------
MediaFileData 속성을 다음과 같이 지원한다:

- __codecs:__ 지원되지 않는다. 이 속성은 항상 null이다.
- __bitrate:__ iOS4 기기에서 오디오만 지원된다. 이 속성은 이미지와 비디오에서 항상 0이다.
- __height:__ 지원된다.  (이미지와 비디오 파일만).  
- __width:__ 지원된다.  (이미지와 비디오 파일만). 
- __duration:__ 지원된다.  (오디오와 비디오 파일만).
