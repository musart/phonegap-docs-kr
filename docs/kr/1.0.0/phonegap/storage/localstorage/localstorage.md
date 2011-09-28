localStorage
===============

W3C Storage interface에 접근을 제공한다. (http://dev.w3.org/html5/webstorage/#the-localstorage-attribute)

    var storage = window.localStorage;

Methods
-------

- __key__: 명시된 위치에 있는 key 이름을 반환한다.
- __getItem__: 제공된 key에 의해 확인된 아이템을 반환한다.
- __setItem__: 제공된 key에 아이템을 저장한다.
- __removeItem__: 제공된 key에 의해 확인된 아이템을 제거한다.
- __clear__: 모든 key-value 쌍을 제거한다.

Details
-----------

localStorage 는 W3C Storage 인터페이스를 제공한다. 키-벨류 쌍의 데이터를 저정하는 것을 허락한다.

지원하는 플랫폼
-------------------

- Android
- BlackBerry WebWorks (OS 6.0 and higher)
- iPhone

Key 빠른 예제
-------------

    var keyName = window.localStorage.key(0);

Set Item 빠른 예제
-------------

    window.localStorage.setItem("key", "value");

Get Item 빠른 예제
-------------

	var value = window.localStorage.getItem("key");
	// value는 이제 "value"와 같다.

Remove Item 빠른 예제
-------------

	window.localStorage.removeItem("key");

Clear 빠른 예제
-------------

	window.localStorage.clear();

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
			window.localStorage.setItem("key", "value");
			var keyname = window.localStorage.key(i);
			// keyname은 이제 "key"와 같다.
			var value = window.localStorage.getItem("key");
			// value는 이제 "value"와 같다.
			window.localStorage.removeItem("key");
			window.localStorage.setItem("key2", "value2");
			window.localStorage.clear();
			// localStorage는 비어있지 않다.
        }
    

        </script>
      </head>
      <body>
        <h1>Example</h1>
        <p>localStorage</p>
      </body>
    </html>
