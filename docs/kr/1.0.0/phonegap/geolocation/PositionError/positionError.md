PositionError
========

`PositionError` 객체는 에러가 발생할 때 geolocationError 콜백으로 반환된다.

Properties
----------

- __code:__ 아래 열거된 미리 정의된 에러 코드 중 하나.
- __message:__ 에러가 발생했을 때의 상세한 정보를 설명하는 에러 메세지.

Constants
---------

- `PositionError.PERMISSION_DENIED`
- `PositionError.POSITION_UNAVAILABLE`
- `PositionError.TIMEOUT`

설명
-----------

`PositionError` 객체는 geolocation에서 에러가 발생햇을 때 사용자에게 'geolocationError' 콜백함수를 통해 반환된다.

