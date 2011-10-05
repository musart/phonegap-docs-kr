SQLTransaction
=======

사용자가 database에 대해 SQL 구문을 수행하도록 가능하게 하는 함수를 포함한다.

Methods
-------

- __executeSql__: SQL 구문을 실행한다.

Details
-------

당신이 database 객체에 트랜젝션 함수를 호출할 때 콜백 함수는 SQLTransaction 객체와 함께 호출된다. 사용자는 database executeSql 함수를 여러번 호출하면서 트렌젝션을 개발할 수 있다.

지원하는 플랫폼
-------------------

- Android
- BlackBerry WebWorks (OS 6.0 and higher)
- iPhone

Execute SQL 빠른 예제
------------------

	function populateDB(tx) {
		 tx.executeSql('DROP TABLE IF EXISTS DEMO');
		 tx.executeSql('CREATE TABLE IF NOT EXISTS DEMO (id unique, data)');
		 tx.executeSql('INSERT INTO DEMO (id, data) VALUES (1, "First row")');
		 tx.executeSql('INSERT INTO DEMO (id, data) VALUES (2, "Second row")');
	}
	
	function errorCB(err) {
		alert("Error processing SQL: "+err);
	}
	
	function successCB() {
		alert("success!");
	}
	
	var db = window.openDatabase("Database", "1.0", "PhoneGap Demo", 200000);
	db.transaction(populateDB, errorCB, successCB);

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
		
		// database를 채운다.
		//
		function populateDB(tx) {
			 tx.executeSql('DROP TABLE IF EXISTS DEMO');
			 tx.executeSql('CREATE TABLE IF NOT EXISTS DEMO (id unique, data)');
			 tx.executeSql('INSERT INTO DEMO (id, data) VALUES (1, "First row")');
			 tx.executeSql('INSERT INTO DEMO (id, data) VALUES (2, "Second row")');
		}
		
		// error callback 처리
		//
		function errorCB(err) {
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
        <p>SQLTransaction</p>
      </body>
    </html>
