Database
=======

사용자에게 Database를 다루도록 가능하게 하는 함수들이 들어있다.

Methods
-------

- __transaction__: database 트렌젝션을 실행한다. 
- __changeVersion__: 버전 값을 자동으로 검증하고 동시에 스키마 업데이트 하는 것과 같이 버전값을 변경하기 위한 스크립트를 가능하게 하는 함수 

Details
-------

'window.openDatabase()' 호출로부터 반환되는 Database 객체

지원하는 플랫폼
-------------------

- Android
- BlackBerry WebWorks (OS 6.0 and higher)
- iPhone

Transaction 빠른 예제
------------------
	function populateDB(tx) {
		 tx.executeSql('DROP TABLE IF EXISTS DEMO');
		 tx.executeSql('CREATE TABLE IF NOT EXISTS DEMO (id unique, data)');
		 tx.executeSql('INSERT INTO DEMO (id, data) VALUES (1, "First row")');
		 tx.executeSql('INSERT INTO DEMO (id, data) VALUES (2, "Second row")');
	}
	
	function errorCB(err) {
		alert("Error processing SQL: "+err.code);
	}
	
	function successCB() {
		alert("success!");
	}
	
	var db = window.openDatabase("Database", "1.0", "PhoneGap Demo", 200000);
	db.transaction(populateDB, errorCB, successCB);

Change Version 빠른 예제
-------------------

	var db = window.openDatabase("Database", "1.0", "PhoneGap Demo", 200000);
	db.changeVersion("1.0", "1.1");

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
			var db = window.openDatabase("Database", "1.0", "PhoneGap Demo", 200000);
			db.transaction(populateDB, errorCB, successCB);
        }
		
		// database를 채운다
		//
		function populateDB(tx) {
			 tx.executeSql('DROP TABLE IF EXISTS DEMO');
			 tx.executeSql('CREATE TABLE IF NOT EXISTS DEMO (id unique, data)');
			 tx.executeSql('INSERT INTO DEMO (id, data) VALUES (1, "First row")');
			 tx.executeSql('INSERT INTO DEMO (id, data) VALUES (2, "Second row")');
		}
		
		// error callback 처리
		//
		function errorCB(tx, err) {
			alert("Error processing SQL: "+err);
		}
		
		// success callback 처리
		//
		function successCB() {
			alert("success!");
		}
	
        </script>
      </head>
      <body>
        <h1>Example</h1>
        <p>Database</p>
      </body>
    </html>

Android 1.X Quirks
------------------

- __changeVersion:__ 이 함수는 안드로이드 1.X 기기들에서 지원되지 않는다.
