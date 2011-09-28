SQLError
========

`SQLError` 객체는 에러가 발생할 때 던져진다.

Properties
----------

- __code:__ 아래 열거된 미리 정의된 에러중에 하나.
- __message:__ 에러의 설명.

Constants
---------

- `SQLError.UNKNOWN_ERR`
- `SQLError.DATABASE_ERR`
- `SQLError.VERSION_ERR`
- `SQLError.TOO_LARGE_ERR`
- `SQLError.QUOTA_ERR`
- `SQLError.SYNTAX_ERR`
- `SQLError.CONSTRAINT_ERR`
- `SQLError.TIMEOUT_ERR`

설명
-----------

`SQLError` 객체는 database를 다루는 가운데 에러가 발생할 때 던져진다.

