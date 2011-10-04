ContactField
============

`Contact` 객체의 포괄적인 필드를 지원한다. 일부 속성은 email 주소들, 전화번호, URL등을 포함하는 `ContactField` 객체로 저장된다.

Properties
----------

- __type:__ 어떤 타입의 필드인지 알려주는 문자열 (예제: 'home'). _(DOMString)_
- __value:__ 필드 값 (전화번호나 이메일 주소와 같은). _(DOMString)_
- __pref:__ 만약 `ContactField` 가 사용자의 선호하는 값이 포함되어 있을 경우 `true`를 설정한다. _(boolean)_

Details
-------

`ContactField` 객채는 일반적으로 연락처 필드를 지원하기위해 사용되는 재사용 가능한 컴포넌트이다. 각각의 `ContactField` 객체는 value, type 그리고 pref 속성을 포함한다. `Contact` 객체는 전화번호나 이메일 주소와 같은 여러 개의 속성을 `ContactField[]` 배열에 저장한다.

대개의 경우에는, `ContactField` 객체의 __type__ 속성을 위해 미리 결정된 value가 없다. 예를 들면, 전화번호는 'home', 'work', 'mobile', 'iPhone' 또는 특정 기기 플랫폼의 연락처 database에서 지원되는 이름의 __type__ 값을 가질 수 있다. 하지만 `Contact`의 __photos__ 필드의 경우에, PhoneGap은 반환되는 이미지의 포멧을 나타내기 위해 __type__ 필드를 사용한다. PhoneGap은 __value__ 속성이 사진 이미지를 위한 URL을 포함할때 __type: 'url'__을 반환하고, 또는 반환된 __value__ 속성이 Base64로 인코딩된 이미지 문자열일 경우 __type: 'base64'__를 반환한다. 

지원하는 플랫폼
-------------------

- Android
- BlackBerry WebWorks (OS 5.0 and higher)
- iOS

빠른 예제
-------------

	// 새로운 contact을 생성한다.
	var contact = navigator.contacts.create();
	
	// 연락처 전화번호를 ContactField[]에 저장한다.
	var phoneNumbers = [3];
	phoneNumbers[0] = new ContactField('work', '212-555-1234', false);
	phoneNumbers[1] = new ContactField('mobile', '917-555-5432', true); // 선호하는 번호
	phoneNumbers[2] = new ContactField('home', '203-555-7890', false);
	contact.phoneNumbers = phoneNumbers;
	
	// 연락처를 저장한다.
	contact.save();

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
			// 새로운 contact을 생성한다.
			var contact = navigator.contacts.create();

			// 연락처 전화번호를 ContactField[]에 저장한다.
			var phoneNumbers = [3];
			phoneNumbers[0] = new ContactField('work', '212-555-1234', false);
			phoneNumbers[1] = new ContactField('mobile', '917-555-5432', true); // preferred number
			phoneNumbers[2] = new ContactField('home', '203-555-7890', false);
			contact.phoneNumbers = phoneNumbers;

			// 연락처를 저장한다.
			contact.save();

			// search contacts, returning display name and phone numbers
			var options = new ContactFindOptions();
			options.filter="";
			filter = ["displayName","phoneNumbers"];
			navigator.contacts.find(filter, onSuccess, onError, options);
        }
    
        // onSuccess: 현재 contacts의 정보를 얻는다.
        //
		function onSuccess(contacts) {
			for (var i=0; i<contacts.length; i++) {
				// 전화번호를 표시한다.
				for (var j=0; j<contacts[i].phoneNumbers.length; j++) {
					alert("Type: " + contacts[i].phoneNumbers[j].type + "\n" + 
							"Value: "  + contacts[i].phoneNumbers[j].value + "\n" + 
							"Preferred: "  + contacts[i].phoneNumbers[j].pref);
				}
			}
		};
    
        // onError: contacts를 얻기 실패
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

Android Quirks
--------------

- __pref:__ 이 속성은 Android 기기에서 지원되지 않고, 항상 `false`를 반환한다.

BlackBerry WebWorks (OS 5.0 and higher) Quirks
--------------------------------------------

- __type:__ 부분적으로 지원된다. 전화번호로 사용된다.
- __value:__ 지원된다.
- __pref:__ 이 속성은 지원되지 않고, 항상 `false`를 반환한다.

iOS Quirks
-----------
- __pref:__ 이 속성은 iOS 기기에서 지원되지 않고, 항상 `false`를 반환한다.
