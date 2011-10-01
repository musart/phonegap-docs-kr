ConfigurationData
=================

> 기기가 지원하는 미디어 캡쳐 인자들의 집합을 요약한다.

설명
-----------

이 객체는 기기가 지원하는 미디어 캡쳐 모드를 설명하기 위해 사용된다. 설정 데이타는 MIME 타입과 (비디오와 이미지의) 캡쳐 크기를 포함한다.

MIME 타입은 [RFC2046](http://www.ietf.org/rfc/rfc2046.txt)에 맞아야 한다. 예제:

- video/3gpp
- video/quicktime
- image/jpeg
- audio/amr
- audio/wav 

Properties
----------

- __type:__ 미디어 타입을 표시하는 소문자의 ASCII-encoded 문자열. (DOMString)
- __height:__ 이미지나 비디오의 픽셀 단위의 높이. 오디오 클립의 경우 이 속성은 0이다. (Number)
- __width:__ 이미지나 비디오의 픽셀 단위의 넓이. 오디오 클립의 경우 이 속성은 0이다. (Number)

빠른 예제
-------------

    // 지원하는 이미지 모드를 검색한다.
    var imageModes = navigator.device.capture.supportedImageModes;

    // 가장 넓은 수평 해상도를 가진 모드를 선택한다.
    var width = 0;
    var selectedmode;
    for each (var mode in imageModes) {
        if (mode.width > width) {
            width = mode.width;
            selectedmode = mode;
        }
    }


어떤 플랫폼도 지원하지 않는다. 모든 설정 데이터 배열은 비어있다.
