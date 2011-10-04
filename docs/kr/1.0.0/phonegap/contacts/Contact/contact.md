Contact
=======

사용자의 개인적이거나 업무적인 연락처와 같이, 연락처를 설명하는 속성을 포함한다.

Properties
----------

- __id:__ 전역적인 unique 식별자. _(DOMString)_
- __displayName:__ 최종사용자에게 표시되기 적합한 이 연락처의 이름. _(DOMString)_
- __name:__ 사람 이름의 모든 컴포넌트를 포함하는 객체. _(ContactName)_
- __nickname:__ 연착처의 일상적인 이름. _(DOMString)_
- __phoneNumbers:__ 연락처의 모든 전화번호 배열. _(ContactField[])_
- __emails:__ 연락처의 모든 이메일 주소의 배열. _(ContactField[])_
- __addresses:__ 연락처의 모든 주소의 배열. _(ContactAddresses[])_
- __ims:__ 연락처의 모든 IM 주소의 배열. _(ContactField[])_
- __organizations:__ 연락처의 모든 조직의 배열. _(ContactOrganization[])_
- __birthday:__ 연락처의 생일. _(Date)_
- __note:__ 연락처에 대한 메모. _(DOMString)_
- __photos:__ 연락처의 사진 배열. _(ContactField[])_
- __categories:__  연락처의 사용자 정의된 모든 범주의 배열. _(ContactField[])_
- __urls:__  연락처와 관련된 웹 페이지의 배열. _(ContactField[])_

Methods
-------

- __clone__: 호출하는 객체의 완전한 복사본으로 id 속성은 `null`로 설정되는 새로운 Contact 객체를 반환한다.
- __remove__: 연락처를 기기의 연락처 database에서 제거한다. 제거가 성공적이지 않으면 에러 콜백이 `ContactError` 객체를 담아 호출된다
- __save__: 새로운 연락처를 기기의 연락처 database에 저장하거나 __id__ 가 있는 기존의 연락처에 갱신한다.


Details
-------

`Contact` 객체는 사용자 연락처를 표현한다. Contacts는 기기의 연락처 database에 생성되거나, 저장되거나 제거된다. Contacts는 기기의 연락처 database에서 `contacts.find` 함수에 의해 (개별적으로 또는 묶음으로) 검색된다.

_Note: 위의 모든 연락처 필드들은 모든 기기 플랫폼에서 다 지원되지 않는다. 어느 필드가 지원되지 않는지에 대한 정보를 각각의 플랫폼의 Quirk 섹션에서 확인하기 바란다._

지원하는 플랫폼
-------------------

- Android
- BlackBerry WebWorks (OS 5.0 and higher)
- iOS

저장하는 빠른 예제
------------------

	function onSuccess(contact) {
		alert("Save Success");
	};

	function onError(contactError) {
		alert("Error = " + contactError.code);
	};

	// 새로운 연락처 객체를 생성한다.
    var contact = navigator.contacts.create();
	contact.displayName = "Plumber";
	contact.nickname = "Plumber"; 		//모든 기기를 지원하기 위해 양쪽 다 명시한다.
	
	// 특정 필드를 채운다.
	var name = new ContactName();
	name.givenName = "Jane";
	name.familyName = "Doe";
	contact.name = name;
	
	// 기기에 저장한다.
	contact.save(onSuccess,onError);

복제하는 빠른 예제
-------------------

	// 연락처 객체를 복제한다.
	var clone = contact.clone();
	clone.name.givenName = "John";
	console.log("Original contact name = " + contact.name.givenName);
	console.log("Cloned contact name = " + clone.name.givenName); 

삭제하는 빠른 예제
--------------------

    function onSuccess() {
        alert("Removal Success");
    };

    function onError(contactError) {
        alert("Error = " + contactError.code);
    };

	// 기기로부터 연락처를 제거한다.
	contact.remove(onSuccess,onError);

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
		    // 생성한다.
		    var contact = navigator.contacts.create();
			contact.displayName = "Plumber";
			contact.nickname = "Plumber"; 		//모든 기기를 지원하기 위해 양쪽 다 명시한다.

			var name = new ContactName();
			name.givenName = "Jane";
			name.familyName = "Doe";
			contact.name = name;

			// 저장한다.
			contact.save(onSaveSuccess,onSaveError);
			
			// 복제한다.
			var clone = contact.clone();
			clone.name.givenName = "John";
			console.log("Original contact name = " + contact.name.givenName);
			console.log("Cloned contact name = " + clone.name.givenName); 
			
			// 제거한다.
			contact.remove(onRemoveSuccess,onRemoveError);
        }
        
        // onSaveSuccess: 헌재 연락처의 스넵샷을 얻는다.
        //
        function onSaveSuccess(contact) {
			alert("Save Success");
        }
    
        // onSaveError: 연락처 얻기를 실패했을 경우
        //
        function onSaveError(contactError) {
			alert("Error = " + contactError.code);
        }
        
        // onRemoveSuccess: 현재 연락처의 스텝샷을 얻는다.
        //
        function onRemoveSuccess(contacts) {
			alert("Removal Success");
        }
    
        // onRemoveError: 연락처 얻기를 실패했을 경우
        //
        function onRemoveError(contactError) {
			alert("Error = " + contactError.code);
        }

        </script>
      </head>
      <body>
        <h1>Example</h1>
        <p>Find Contacts</p>
      </body>
    </html>

Android 2.X Quirks
------------------

- __categories:__ 이 속성은 Android 2.X 기기에서 지원되지 않고, 항상 `null`을 반환한다.

Android 1.X Quirks
------------------

- __name:__ 이 속성은 Android 1.X 기기에서 지원되지 않고 항상 `null`를 반환한다.
- __nickname:__ 이 속성은 Android 1.X 기기에서 지원되지 않고 항상 `null`를 반환한다.
- __birthday:__ 이 속성은 Android 1.X 기기에서 지원되지 않고 항상 `null`를 반환한다.
- __photos:__ 이 속성은 Android 1.X 기기에서 지원되지 않고 항상 `null`를 반환한다.
- __categories:__ 이 속성은 Android 1.X 기기에서 지원되지 않고 항상 `null`를 반환한다.
- __urls:__ 이 속성은 Android 1.X 기기에서 지원되지 않고 항상 `null`를 반환한다.


BlackBerry WebWorks (OS 5.0 and higher) Quirks
---------------------------------------------

- __id:__ 지원된다. 연락처가 저장될때 기기에 의해 할당된다.
- __displayName:__ 지원된다. BlackBerry의 __user1__ 필드에 저장된다.
- __nickname:__ 이 속성은 지원되지 않고, 항상 `null`을 반환한다.
- __phoneNumbers:__ 부분적으로 지원된다. 전화번호는 _type_이 `home`이면 BlackBerry의 __homePhone1__과 __homePhone2__에 저장되고, _type_이 `work`이면 __workPhone1__과 __workPhone2__에 저장되고, _type_이 `mobile`이면 __mobilePhone__에 저장되고, _type_이 `fax`이면 __faxPhone__에 저장되고, _type_이 `pager`이면 __pagerPhone__에 저장되고, _type_이 위의 어떤 것도 아니면 __otherPhone__에 저장된다.
- __emails:__ 부분적으로 지원된다. 첫번째 3개의 이메일 주소는 BlackBerry의 __email1__, __email2__, __email3__ 필드에 각각 저장된다.
- __addresses:__ 부분적으로 지원된다. 첫번째와 두번째 주소는 BlackBerry의 __homeAddress__와 __workAddress__ 필드에 각각 저장된다.
- __ims:__ 이 속성은 지원되지 않고, 항상 `null`을 반환한다.
- __organizations:__ 부분적으로 지원된다. 첫번째 조직의 __name__과 __title__은 BlackBerry의 __company__와 __title__ 필드에 각각 저장된다.
- __photos:__ - 부분적으로 지원된다. 단일 섬네일크기의 사진이 지원된다. 연락처의 사진을 설정하기 위해 Base64로 암호화된 사진이나 해당 이미지를 가리키는 URL를 전달한다. 이미지는 BlackBerry 연락처 이미지에 저장될 떼 축소된다. 연락처 사진은 Base64로 암호화된 이미지를 반환한다.
- __categories:__ 부분적으로 지원된다. `Business`와 `Personal` 카테고리만이 지원된다.
- __urls:__  부분적으로 지원된다. 첫번재 url은 BlackBerry의 __webpage__ 필드에 저장된다.

iOS Quirks
----------
- __displayName:__ 이 속성은 iOS에서 지원되지 않고, ContactName이 명시되어 있지 않으면 `null`을 반환한다. ContactName이 없으면, 합성 이름, __nickname__ 또는 ""이 제각기 __displayName__에 반환된다.
- __birthday:__ 입력을 위해 이 속성은 자바스크립트 Date 객체로 제공되어야 한다. 이 속성은 자바스크립트 Date 객체 형태로 반환된다.
- __photos:__ 반환된 사진은 어플리케이션의 임시 디렉토리에 저장되고, 사진의 File URL이 반환된다. 입시 디렉토리의 사진은 어플리케이션이 종료될 경우 삭제된다.
- __categories:__  이 속서은 현재 지원되지 않고, 항상 `null`이 반환된다.
