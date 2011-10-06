ContactAddress
==============

`Contact` 객체의 주소 속성을 담는다.

Properties
----------
- __pref:__ 만약 `ContactAddress`가 사용자의 선호 값이 포함되어 있다면 `true`로 설정된다. _(boolean)_
- __type:__ 이것이 어떤 타입의 필드인지 알려주는 문자열 (예제: 'home'). _(DOMString)_
- __formatted:__ 표시하기 위한 구성된 전체 주소. _(DOMString)_
- __streetAddress:__ 전체 street 주소. _(DOMString)_
- __locality:__ 도시나 주택지구. _(DOMString)_
- __region:__ state나 region. _(DOMString)_
- __postalCode:__ zip code나 postal code. _(DOMString)_
- __country:__ 나라 이름. _(DOMString)_

Details
-------

`ContactAddress` 객체는 연락처의 단일 주소 속성들을 저장한다. `Conatact` 객체는 `ContactAddress[]` 배열안에 하나 이상의 주소를 가질 수 있다.

지원하는 플랫폼
-------------------

- Android
- BlackBerry WebWorks (OS 5.0 and higher)
- iOS

빠른 예제
-------------

	// 모든 contacts의 주소 정보를 표시한다.
    function onSuccess(contacts) {
		for (var i=0; i<contacts.length; i++) {
			for (var j=0; j<contacts[i].addresses.length; j++) {
				alert("Pref: " + contacts[i].addresses[j].pref + "\n" +
						"Type: " + contacts[i].addresses[j].type + "\n" +
						"Formatted: " + contacts[i].addresses[j].formatted + "\n" + 
						"Street Address: "  + contacts[i].addresses[j].streetAddress + "\n" + 
						"Locality: "  + contacts[i].addresses[j].locality + "\n" + 
						"Region: "  + contacts[i].addresses[j].region + "\n" + 
						"Postal Code: "  + contacts[i].addresses[j].postalCode + "\n" + 
						"Country: "  + contacts[i].addresses[j].country);
			}
		}
    };

    function onError(contactError) {
        alert('onError!');
    };

    // 모든 연락처를 찾는다.
    var options = new ContactFindOptions();
	options.filter=""; 
	var filter = ["displayName","addresses"];
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
		    // 모든 연락처를 찾는다.
		    var options = new ContactFindOptions();
			options.filter=""; 
			var filter = ["displayName","addresses"];
		    navigator.contacts.find(filter, onSuccess, onError, options);
        }
    
        // onSuccess: 현재 contacts의 정보를 얻는다.
        //
		function onSuccess(contacts) {
			// 모든 contacts의 주소 정보를 표시한다.
			for (var i=0; i<contacts.length; i++) {
				for (var j=0; j<contacts[i].addresses.length; j++) {
					alert("Pref: " + contacts[i].addresses[j].pref + "\n" +
							"Type: " + contacts[i].addresses[j].type + "\n" +
							"Formatted: " + contacts[i].addresses[j].formatted + "\n" + 
							"Street Address: "  + contacts[i].addresses[j].streetAddress + "\n" + 
							"Locality: "  + contacts[i].addresses[j].locality + "\n" + 
							"Region: "  + contacts[i].addresses[j].region + "\n" + 
							"Postal Code: "  + contacts[i].addresses[j].postalCode + "\n" + 
							"Country: "  + contacts[i].addresses[j].country);
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
- __streetAddress:__ 이 속성은 Android 1.X 기기에서 지원되지 않고 항상 `null`를 반환한다.
- __locality:__ 이 속성은 Android 1.X 기기에서 지원되지 않고 항상 `null`를 반환한다.
- __region:__ 이 속성은 Android 1.X 기기에서 지원되지 않고 항상 `null`를 반환한다.
- __postalCode:__ 이 속성은 Android 1.X 기기에서 지원되지 않고 항상 `null`를 반환한다.
- __country:__ 이 속성은 Android 1.X 기기에서 지원되지 않고 항상 `null`를 반환한다.

BlackBerry WebWorks (OS 5.0 and higher) Quirks
--------------------------------------------
- __pref:__ 이 속성은 Blackberry 기기에서 지원되지 않고 항상 `false`를 반환한다.
- __type:__ 부분적으로 지원된다. 연락처당 각각 "Work"와 "Home" 타입의 주소만 저장된다. 
- __formatted:__ 부분적으로 지원된다. 모든 BlackBerry 주소 필드의 연속을 반환한다.
- __streetAddress:__ 지원된다. BlackBerry의 __address1__ 과 __address2__ 주소 필드의 연속을 반환한다.
- __locality:__ 지원된다.  BlackBerry의 __city__ 주소 필드에 저장된 값.
- __region:__ 지원된다.  BlackBerry의 __stateProvince__ 주소 필드에 저장된 값.
- __postalCode:__ 지원된다.  BlackBerry의 __zipPostal__ 주소 필드에 저장된 값.
- __country:__ 지원된다.

iOS Quirks
----------
- __pref:__ 이 속성은 iOS 기기에서 지원되지 않고 항상 `false`를 반환한다.
- __formatted:__ 현재 지원되지 않는다.
