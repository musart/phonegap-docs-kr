contacts.create
===============

새로운 Contact 객체를 반환한다.

    var contact = navigator.contacts.create(properties);

설명
-----------

contacts.create 는 새로운 `Contact` 객체를 반환하는 동기 함수이다.

이 함수는 Contact 객체를 기기의 연락처 저장소에 유지하지 않는다. Contact 객체를 기기에 유지하기 위해서는 `Contact.save` 함수를 호출한다.

지원하는 플랫폼
-------------------

- Android
- BlackBerry WebWorks (OS 5.0 and higher)
- iOS

빠른 예제
-------------

    var myContact = navigator.contacts.create({"displayName": "Test User"});

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
			var myContact = navigator.contacts.create({"displayName": "Test User"});
			myContact.gender = "male";
			console.log("The contact, " + myContact.displayName + ", is of the " + myContact.gender + " gender");
        }
    

        </script>
      </head>
      <body>
        <h1>Example</h1>
        <p>Create Contact</p>
      </body>
    </html>
