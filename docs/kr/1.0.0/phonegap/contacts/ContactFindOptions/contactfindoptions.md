ContactFindOptions
==================

`contacts.find` 동작의 결과를 거르기위해 사용되는 속성을 포함한다.

Properties
----------

- __filter:__ 연락처를 검색하기 위해 상용하는 문자열. _(DOMString)_ (기본값: "")
- __multiple:__ 만약 find 동작이 여러개의 연락처를 반환하면 설정된다. _(Boolean)_ (기본값: false)


지원하는 플랫폼
-------------------

- Android
- BlackBerry WebWorks (OS 5.0 and higher)
- iOS

빠른 예제
-------------

	// 성공 콜백
    function onSuccess(contacts) {
		for (var i=0; i<contacts.length; i++) {
			alert(contacts[i].displayName);
		}
    };

	// 실패 콜백
    function onError(contactError) {
        alert('onError!');
    };

	// 명시된 연락처 기준
    var options = new ContactFindOptions();
	options.filter="";			// 빈 문자열은 모든 연락처를 반환한다.
	options.multiple=true;		// 다중 결과값을 반환한다.
	filter = ["displayName"];	// contact.displayName 필드를 반환한다.
	
	// 연락처를 찾는다.
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
			// 명시된 연락처 기준
		    var options = new ContactFindOptions();
			options.filter="";			// 빈 문자열은 모든 연락처를 반환한다.
			options.multiple=true;		// 다중 결과값을 반환한다.
			filter = ["displayName"];	// contact.displayName 필드를 반환한다.

			// 연락처를 찾는다.
		    navigator.contacts.find(filter, onSuccess, onError, options);
        }
    
        // onSuccess: 현재 contacts의 정보를 얻는다.
        //
		function onSuccess(contacts) {
			for (var i=0; i<contacts.length; i++) {
				alert(contacts[i].displayName);
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

