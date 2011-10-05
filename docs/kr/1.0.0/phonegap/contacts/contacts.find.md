contacts.find
=============

기기의 연락처 저장소를 쿼리하고, 명시된 필드들을 포함하는 하나 이상의 `Contact` 객체를 반환한다.

    navigator.contacts.find(contactFields, contactSuccess, contactError, contactFindOptions);

설명
-----------

contacts.find 는 기기의 연락처 저장소를 쿼리하고 `Contact` 객체의 배열을 반환하는 비동기 함수이다. 결과 객체는 __contactSuccess__ 변수에 의해 명시된 `contactSuccess` 콜백 함수로 전달된다.

사용자는 __contactFields__ 변수안의 검색 식별자로 쓰이는 연락처 필드를 반드시 명시한다. __contactFields__ 인자에 명시된 필드만 __contactSuccess__ 콜백 함수로 전달되는 `Contact` 객체의 속성으로 반환된다. 길이가 없는 __contactFields__ 인자는 `id` 속성만 채워진 `Contact` 객체로 반환한다. ["*"]의 __contactFields__ 값은 모든 연락처 필드들을 반환한다.

__contactFindOptions.filter__ 문자열은 연락처 저장소를 쿼리 할 때 검색 필터로 사용될 수 있다. 만약 이 문자열이 제공되어 지면, 대소문자 구분 없이 부분적인 값 메치가 __contactFields__ 인자에 명기된 각 필드에 적용된다. 만약 매치가 명기된 필드와 비교하여 발견되면 연락처는 반환된다.

Parameters
----------

- __contactFields:__ 검색 식별자로 사용되는 연락처 필드. 이 필드들은 반환되는 `Contact` 객체안의 변수들 만을 갖게 될 것이다. _(DOMString[])_ [필수]
- __contactSuccess:__ 연락처 DB로부터 반환된 연락처와 함께 작동되는 성공 콜백 함수. [필수] 
- __contactError:__ 실패 콜백 함수. 에러가 발생할 경우 호출된다. [선택]
- __contactFindOptions:__ 연락처를 걸러내기 위한 검색 옵션. [선택]

지원하는 플랫폼
-------------------

- Android
- BlackBerry WebWorks (OS 5.0 and higher)
- iOS

빠른 예제
-------------

    function onSuccess(contacts) {
        alert('Found ' + contacts.length + ' contacts.');
    };

    function onError(contactError) {
        alert('onError!');
    };

    // 이름 필드에서 'Bob'를 가진 모든 연락처를 검색한다.
    var options = new ContactFindOptions();
	options.filter="Bob"; 
	var fields = ["displayName", "name"];
    navigator.contacts.find(fields, onSuccess, onError, options);

전체 예제
------------

    <!DOCTYPE html>
    <html>
      <head>
        <title>Contact Example</title>

        <script type="text/javascript" charset="utf-8" src="phonegap.js"></script>
        <script type="text/javascript" charset="utf-8">

        // PhoneGap이 로드되기를 기다린다
        //
        document.addEventListener("deviceready", onDeviceReady, false);

        // PhoneGap이 준비되면 호출된다
        //
        function onDeviceReady() {
		    // 이름 필드에서 'Bob'를 가진 모든 연락처를 검색한다.
		    var options = new ContactFindOptions();
			options.filter="Bob"; 
			var fields = ["displayName", "name"];
		    navigator.contacts.find(fields, onSuccess, onError, options);
        }
    
        // onSuccess: 현재 연락처의 스냅샷을 얻는다.
        //
        function onSuccess(contacts) {
			for (var i=0; i<contacts.length; i++) {
				console.log("Display Name = " + contacts[i].displayName);
			}
        }
    
        // onError: 연락처를 얻기 실패한 경우
        //
        function onError(contactError) {
            alert('onError!');
        }

        </script>
      </head>
      <body>
        <h1>Example</h1>
        <p>Find Contacts</p>
      </body>
    </html>
    

