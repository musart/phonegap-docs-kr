Media
=====

> `Media` 객체는 기기의 오디오 파일들을 녹음하고 제생하는 기능을 제공한다.

    var media = new Media(src, mediaSuccess, [mediaError], [mediaStatus]);


Note: 현재 구현은 media capture관련 W3C 표준과 맞지 않고, 편의를 위해서만 제공된다. 미래의 구현은 최신 W3C 스펙에 맞을 것이고 현재 API들은 제거될 것이다.

Parameters
----------

- __src__: 오디오 컨텐츠를 담는 URI. _(DOMString)_
- __mediaSuccess__: (선택적인 변수) Media 객체가 현재 재생/녹음 또는 정지 동작이 완료되었을 때 불리는 콜백. _(Function)_
- __mediaError__: (선택적인 변수) 만약 에러가 발생하면 발생하는 콜백. _(Function)_
- __mediaStatus__: (선택적인 변수) 상태 변화를 나타내기 위해 발생하는 콜백. _(Function)_

Methods
-------

- media.getCurrentPosition: 오디오 파일의 현재 위치를 반환한다.
- media.getDuration: 오디오 파일의 지속시간을 반환한다.
- media.play: 오디오 파일을 재생하는 것을 시작하거나 재개한다.
- media.pause: 오디오 파일을 재생하는 것을 멈춘다.
- media.release: 근본적인 OS들의 오디오 리소스를 릴리즈한다.
- media.seekTo: 오디오 파일 안의 위치를 이동한다.
- media.startRecord: 오디오 파일을 녹음하는 것을 시작한다.
- media.stopRecord: 오디오 파일을 녹음하는 것을 멈춘다.
- media.stop: 오디오 파일을 재생하는 것을 멈춘다.

Additional ReadOnly Parameters
---------------------

- ___position__: 초 단위의 오디오 재생의 위치. 재생중에 자동적으로 갱신되지 않는다. 갱신하기 위해서는 getCurrentPosition을 호출한다.
- ___duration__: 초 단위의 미디어의 지속 기간.

지원하는 플랫폼
-------------------

- Android
- iOS

