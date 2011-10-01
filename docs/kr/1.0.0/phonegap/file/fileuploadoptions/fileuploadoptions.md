FileUploadOptions
========

`FileUploadOptions` 객체는 추가적인 인자들을 upload script에 명시하기 위해 FileTransfer 객체의 upload 함수에 건내준다.

Properties
----------

- __fileKey:__ form 엘리먼트 이름. 설정되어 있지 않으면 디폴트 값으로 "file"을 설정한다. (DOMString)
- __fileName:__ 당신이 서버에 저장되길 원하는 파일 이름. 설정되어 있지 않으면 디폴트 값으로 "image.jpg"를 설정한다. (DOMString)
- __mimeType:__ 당신이 업로드하는 데이터의 mime 타입. 설정되어 있지 않으면 디폴트 값으로 "image/jpeg"를 설정한다. (DOMString)
- __params:__ HTTP 요청시 전달하기 위한 선택적인 key/value 쌍의 집합. (Object)


설명
-----------

`FileUploadOptions` 객체는 추가적인 인자들을 upload script에 명시하기 위해 FileTransfer 객체의 upload 함수에 건내준다.
