FileError
========

File API 함수들 중에 에러가 발생했을 경우 `FileError` 객체는 설정된다. 

Properties
----------

- __code:__ 아래 열거된 미리 정의된 에러 코드 중 하나.

Constants
---------

- `FileError.NOT_FOUND_ERR`
- `FileError.SECURITY_ERR`
- `FileError.ABORT_ERR`
- `FileError.NOT_READABLE_ERR`
- `FileError.ENCODING_ERR`
- `FileError.NO_MODIFICATION_ALLOWED_ERR`
- `FileError.INVALID_STATE_ERR`
- `FileError.SYNTAX_ERR`
- `FileError.INVALID_MODIFICATION_ERR`
- `FileError.QUOTA_EXCEEDED_ERR`
- `FileError.TYPE_MISMATCH_ERR`
- `FileError.PATH_EXISTS_ERR`

설명
-----------

`FileError` 객체는 File API의 에러 콜백들의 유일한 인자이다. 개발자는 에러의 종류를 결정하기 위해 반드시 코드 속성을 읽어야 한다.
