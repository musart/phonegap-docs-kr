File
====

이 객체는 단일 파일의 속성들을 담는다.

Properties
----------

- __name:__ 파일의 이름. _(DOMString)_
- __fullPath:__ 파일이름을 포함한 파일의 모든 경로. _(DOMString)_
- __type:__ 파일의 mime type. _(DOMString)_
- __lastModifiedDate:__ 파일이 수정된 최종 시간. _(Date)_
- __size:__ 바이트 단위의 파일 크기. _(long)_

Details
-------

`File` 객체는 단일 파일의 속성들을 담는다. 당신은 File 객체의 인스턴스를 `FileEntry`객체의 __file__ 함수를 호출함으로써 얻을 수 있다.

지원하는 플랫폼
-------------------

- Android
- BlackBerry WebWorks (OS 5.0 and higher)
- iOS
