ContactName
===========

'Contact' 객체의 이름 속성을 담는다.

Properties
----------

- __formatted:__ 연락처의 완변한 이름. _(DOMString)_
- __familyName:__ 연락처의 family name. _(DOMString)_
- __givenName:__ 연락처의 given name. _(DOMString)_
- __middleName:__ 연락처의 iddle name. _(DOMString)_
- __honorificPrefix:__ 연락처의 prefix (example Mr. or Dr.) _(DOMString)_
- __honorificSuffix:__ 연락처의 suffix (example Esq.). _(DOMString)_

Details
-------

`ContactName` 객체는 연락처의 이름 속성을 저장한다.

지원하는 플랫폼
-------------------

- Android 2.X
- BlackBerry WebWorks (OS 5.0 and higher)
- iOS

빠른 예제
-------------

    function onSuccess(contacts) {
		for (var i=0; i<contacts.length; i++) {
			alert("Formatted: " + contacts[i].name.formatted + "\n" + 
					"Family Name: "  + contacts[i].name.familyName + "\n" + 
					"Given Name: "  + contacts[i].name.givenName + "\n" + 
					"Middle Name: "  + contacts[i].name.middleName + "\n" + 
					"Suffix: "  + contacts[i].name.honorificSuffix + "\n" + 
					"Prefix: "  + contacts[i].name.honorificSuffix);
		}
    };

    function onError(contactError) {
        alert('onError!');
    };

    var options = new ContactFindOptions();
	options.filter="";
	filter = ["displayName","name"];
    navigator.contacts.find(filter, onSuccess, onError, options);

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
			var options = new ContactFindOptions();
			options.filter="";
			filter = ["displayName","name"];
			navigator.contacts.find(filter, onSuccess, onError, options);
        }
    
        // onSuccess: 현재 contacts의 정보를 얻는다
        //
		function onSuccess(contacts) {
			for (var i=0; i<contacts.length; i++) {
				alert("Formatted: " + contacts[i].name.formatted + "\n" + 
						"Family Name: "  + contacts[i].name.familyName + "\n" + 
						"Given Name: "  + contacts[i].name.givenName + "\n" + 
						"Middle Name: "  + contacts[i].name.middleName + "\n" + 
						"Suffix: "  + contacts[i].name.honorificSuffix + "\n" + 
						"Prefix: "  + contacts[i].name.honorificPrefix);
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
------------
- __formatted:__ 부분적으로 지원된다. 앞에 붙는 존칭, givenName, middleName, familyName 그리고 뒤에 붙는 존칭의 연속을 반환한다. 하지만 저장되지는 않는다. 

BlackBerry WebWorks (OS 5.0 and higher) Quirks
---------------------------------------------

- __formatted:__ 부분적으로 지원된다. BlackBerry의 __firstName__ 과 __lastName__ 필드의 연속을 반환한다.
- __familyName:__ 지원된다. BlackBerry에 저장된 __lastName__ 필드.
- __givenName:__ 지원된다. BlackBerry에 저장된 __firstName__ 필드.
- __middleName:__ 이 속성은 지원되지 않고, 항상 'null'을 반환한다.
- __honorificPrefix:__ 이 속성은 지원되지 않고, 항상 'null'을 반환한다.
- __honorificSuffix:__ 이 속성은 지원되지 않고, 항상 'null'을 반환한다.

iOS Quirks
------------
- __formatted:__ 부분적으로 지원되나. iOS의 Composite Name을 반환하지만 저장하지 않는다.
