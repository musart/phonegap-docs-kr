FileUploadResult
========

`FileUploadResult` 객체는 FileTransfer의 upload 함수의 성공 콜백을 통해 반환된다.

Properties
----------

- __bytesSent:__ upload의 일부로써 서버로 보내진 바이트 개수. (long)
- __responseCode:__ 서버에 의해 반환된 HTTP response 코드. (long)
- __response:__ 서버에 의해 반환된 HTTP response. (DOMString)

설명
-----------

`FileUploadResult` 객체는 FileTransfer의 upload 함수의 성공 콜백을 통해 반환된다.

iOS Quirks
----------
- iOS는 responseCode와 bytesSent를 성공 콜백의 FileUploadResult 객체에 포함하지 않는다.

