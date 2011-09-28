openDatabase
===============

새로운 Database 객체를 반환한다.

    var dbShell = window.openDatabase(name, version, display_name, size);

설명
-----------

window.openDatabase 는 새로운 Database 객체를 반환한다.

이 함수는 새로운 SQL Lite Database를 생성하고 Database 객체를 반환한다. 데이터를 다루기 위해서 Database 객체를 사용한다.

지원하는 플랫폼
-------------------

- Android
- BlackBerry WebWorks (OS 6.0 and higher)
- iPhone

빠른 예제
-------------

    var db = window.openDatabase("test", "1.0", "Test DB", 1000000);

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
			var db = window.openDatabase("test", "1.0", "Test DB", 1000000);
        }
		
        </script>
      </head>
      <body>
        <h1>Example</h1>
        <p>Open Database</p>
      </body>
    </html>
