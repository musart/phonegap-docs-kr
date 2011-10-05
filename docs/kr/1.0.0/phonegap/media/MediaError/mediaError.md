MediaError
==========

`MediaError` 객체는 에러가 발생했을 때 `mediaError` 콜백 함수를 반환한다.

Properties
----------

- __code:__ 아래 나열된 미리 정의된 에러 코드 중 하나.
- __message:__ 에러의 상세 설명을 묘사한 에러 메세지.

Constants
---------

- `MediaError.MEDIA_ERR_ABORTED`
- `MediaError.MEDIA_ERR_NETWORK`
- `MediaError.MEDIA_ERR_DECODE`
- `MediaError.MEDIA_ERR_NONE_SUPPORTED`


설명
-----------

`MediaError` 객체는 에러가 발생했을 때 사용자에게 `mediaError` 콜백 함수를 통해 반환한다.

