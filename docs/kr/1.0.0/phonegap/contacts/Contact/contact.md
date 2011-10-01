Contact
=======

사용자의 개인적이거나 업무적인 연락처와 같이, 연락처를 설명하는 속성을 포함한다.

Properties
----------

- __id:__ 전역적인 unique 식별자. _(DOMString)_
- __displayName:__ 최종사용자에게 표시되기 적합한 이 연락처의 이름. _(DOMString)_
- __name:__ 사람 이름의 모든 컴포넌트를 포함하는 객체. _(ContactName)_
- __nickname:__ A casual name to address the contact by. _(DOMString)_
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

- __clone__: Returns a new Contact object that is a deep copy of the calling object, with the id property set to `null`. 
- __remove__: Removes the contact from the device contacts database.  An error callback is called with a `ContactError` object if the removal is unsuccessful.
- __save__: Saves a new contact to the device contacts database, or updates an existing contact if a contact with the same __id__ already exists.


Details
-------

The `Contact` object represents a user contact.  Contacts can be created, saved to, or removed from the device contacts database.  Contacts can also be retrieved (individually or in bulk) from the database by invoking the `contacts.find` method.

_Note: Not all of the above contact fields are supported on every device platform.  Please check each platform's Quirks section for information about which fields are supported._

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

- __categories:__  This property is not support by Android 2.X devices, and will always be returned as `null`.

Android 1.X Quirks
------------------

- __name:__ This property is not support by Android 1.X devices, and will always be returned as `null`.
- __nickname:__ This property is not support by Android 1.X devices, and will always be returned as `null`.
- __birthday:__ This property is not support by Android 1.X devices, and will always be returned as `null`.
- __photos:__ This property is not support by Android 1.X devices, and will always be returned as `null`.
- __categories:__  This property is not support by Android 1.X devices, and will always be returned as `null`.
- __urls:__  This property is not support by Android 1.X devices, and will always be returned as `null`.


BlackBerry WebWorks (OS 5.0 and higher) Quirks
---------------------------------------------

- __id:__ Supported.  Assigned by device when contact is saved.
- __displayName:__ Supported.  Stored in BlackBerry __user1__ field.
- __nickname:__ This property is not supported, and will always be returned as `null`. 
- __phoneNumbers:__ Partially supported.  Phone numbers will be stored in BlackBerry fields __homePhone1__ and __homePhone2__ if _type_ is 'home', __workPhone1__ and __workPhone2__ if _type_ is 'work', __mobilePhone__ if _type_ is 'mobile', __faxPhone__ if _type_ is 'fax', __pagerPhone__ if _type_ is 'pager', and __otherPhone__ if _type_ is none of the above.
- __emails:__ Partially supported.  The first three email addresses will be stored in the BlackBerry __email1__, __email2__, and __email3__ fields, respectively.
- __addresses:__ Partially supported.  The first and second addresses will be stored in the BlackBerry __homeAddress__ and __workAddress__ fields, respectively.
- __ims:__ This property is not supported, and will always be returned as `null`. 
- __organizations:__ Partially supported.  The __name__ and __title__ of the first organization are stored in the BlackBerry __company__ and __title__ fields, respectively.
- __photos:__ - Partially supported.  A single thumbnail-sized photo is supported.  To set a contact's photo, pass in a either a Base64 encoded image, or a URL pointing to the image.  The image will be scaled down before saving to the BlackBerry contacts database.   The contact photo is returned as a Base64 encoded image.
- __categories:__  Partially supported.  Only 'Business' and 'Personal' categories are supported. 
- __urls:__  Partially supported. The first url is stored in BlackBerry __webpage__ field.

iOS Quirks
----------
- __displayName:__ This property is not supported by iOS and will be returned as `null` unless there is no ContactName specified.  If there is no ContactName, then composite name, __nickame__ or "" is returned for __displayName__, respectively. 
- __birthday:__ For input, this property must be provided as a JavaScript Date object. It is returned as a JavaScript Date object.
- __photos:__ Returned Photo is stored in the application's temporary directory and a File URL to photo is returned.  Contents of temporary folder is deleted when application exits. 
- __categories:__  This property is not currently supported and will always be returned as `null`.
