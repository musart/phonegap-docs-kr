ContactOrganization
===================

`Contact` 객체의 조직 속성을 포함한다.

Properties
----------
- __pref:__ 만약 `ContactOrganization` 이 사용자의 선호하는 변수를 포함할 경우 `true`로 설정한다. _(boolean)_
- __type:__ 이것이 어떤 타입의 필드인지 알려주는 문자열 (example: 'home'). _(DOMString)_
- __name:__ 조직의 이름 _(DOMString)_
- __department:__ 연락처가 일하는 부서. _(DOMString)_
- __title:__ 조직에서 연락처의 직함. _(DOMString)_

Details
-------

`ContactOrganization` 객체는 연락처의 조직 속성을 저장한다. `Contact` 객체는 하나 이상의 `ContactOrganization` 객체를 배열에 저장한다.

지원하는 플랫폼
-------------------

- Android
- BlackBerry WebWorks (OS 5.0 and higher)
- iOS

빠른 예제
-------------

    function onSuccess(contacts) {
		for (var i=0; i<contacts.length; i++) {
			for (var j=0; j<contacts[i].organizations.length; j++) {
				alert("Pref: " + contacts[i].organizations[j].pref + "\n" +
						"Type: " + contacts[i].organizations[j].type + "\n" +
						"Name: " + contacts[i].organizations[j].name + "\n" + 
						"Department: "  + contacts[i].organizations[j].department + "\n" + 
						"Title: "  + contacts[i].organizations[j].title);
			}
		}
    };

    function onError(contactError) {
        alert('onError!');
    };

    var options = new ContactFindOptions();
	options.filter="";
	filter = ["displayName","organizations"];
    navigator.contacts.find(filter, onSuccess, onError, options);

전체 예제
------------

    <!DOCTYPE html>
    <html>
      <head>
        <title>Contact Example</title>

        <script type="text/javascript" charset="utf-8" src="phonegap.js"></script>


        // PhoneGap이 로드되기를 기다린다.
        //
        document.addEventListener("deviceready", onDeviceReady, false);

        // PhoneGap이 준비되면 호출된다.
        //
        function onDeviceReady() {
			var options = new ContactFindOptions();
			options.filter="";
			filter = ["displayName","organizations"];
			navigator.contacts.find(filter, onSuccess, onError, options);
        }
    
        // onSuccess: 현재 contacts의 정보를 얻는다.
        //
		function onSuccess(contacts) {
			for (var i=0; i<contacts.length; i++) {
				for (var j=0; j<contacts[i].organizations.length; j++) {
					alert("Pref: " + contacts[i].organizations[j].pref + "\n" +
							"Type: " + contacts[i].organizations[j].type + "\n" +
							"Name: " + contacts[i].organizations[j].name + "\n" + 
							"Department: "  + contacts[i].organizations[j].department + "\n" + 
							"Title: "  + contacts[i].organizations[j].title);
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
	

Android 2.X Quirks
------------------

- __pref:__ 이 속성은 Android 2.X 기기에서 지원되지 않고 항상 `false`를 반환한다.

Android 1.X Quirks
------------------

- __pref:__ 이 속성은 Android 1.X 기기에서 지원되지 않고 항상 `false`를 반환한다.
- __type:__ 이 속성은 Android 1.X 기기에서 지원되지 않고 항상 `null`를 반환한다.
- __title:__ 이 속성은 Android 1.X 기기에서 지원되지 않고 항상 `false`를 반환한다.

BlackBerry WebWorks (OS 5.0 and higher) Quirks
--------------------------------------------
- __pref:__ 이 속성은 Blackberry 기기에서 지원되지 않고 항상 `false`를 반환한다.
- __type:__ 이 속성은 Blackberry 기기에서 지원되지 않고 항상 `null`를 반환한다.
- __name:__ 부분적으로 지원된다. 첫번째 조직이름은 BlackBerry의 __company__ 필드에 저장된 값.
- __department:__ 이 속서은 지원되지 않고, 항상 `null`을 반환한다.
- __title:__ 부분적으로 지원된다. 첫번째 조직의 직합은 BlackBerry의 __jobTitle__ 필드에 저장된 값.

iOS Quirks
-----------
- __pref:__ 이 속성은 iOS 기기에서 지원되지 않고 항상 `false`를 반환한다.
- __type:__ 이 속성은 iOS 기기에서 지원되지 않고 항상 `null`를 반환한다.
- __name:__ 부분적으로 지원된다. 첫번째 조직이름은 iOS의 __kABPersonOrganizationProperty__ 필드에 저장된다.
- __department__: 부분적으로 지원된다. 첫번째 부서이름은 iOS의 __kABPersonDepartmentProperty__ 필드에 저장된다.
- __title__: 부분적으로 지원된다. 첫번째 직함은 iOS의 __kABPersonJobTitleProperty__ 필드에 저장된다.


