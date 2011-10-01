SQLResultSet
=======

SQLTransaction의 executeSql 함수가 호출될 때, 그것은 SQLResultSet을 갖는 그것의 콜백을 호출할 것이다.

Properties
-------

- __insertId__: SQLResultSet 객체의 SQL 구문이 database에 삽입하는 열의 row ID.
- __rowAffected__: SQL 구문에 의해 변경된 열들(rows)의 개수. 만약 구문이 어떤 열들(rows)에도 영향을 주지 않았다면 0으로 설정된다.
- __rows__: SQLResultSetRowList는 반환된 열들(rows)을 나타낸다. 만약 아무 열(row)도 반환되지 않는다면 이 객체는 비어있을 것이다.

Details
-------

당신이 SQLTransaction executeSql 함수를 호출할 때, 해당 콜백 함수는 SQLResultSet 객체와 함께 호출될 것이다. 결과 객체는 3개의 속성을 가진다. 첫번째는 성공적인 SQL insert 구문의 열 번호를 반환하는 'insertId'이다. 만약 SQL 구문이 삽입되지 않았다면 'insertId'는 설정되지 않는다. 'rowAffected'는 SQL select 구문을 위해 항상 0이다. insert나 update 구문을 위헤 그것은 수정된 열의 개수를 반환한다. 마지막 속성은 SQLResultSetList 타입이고, 그것은 SQL select 구문으로부터 반환된 데이터를 포함한다.

지원하는 플랫폼
-------------------

- Android
- BlackBerry WebWorks (OS 6.0 and higher)
- iPhone

Execute SQL 빠른 예제
------------------

	function queryDB(tx) {
		tx.executeSql('SELECT * FROM DEMO', [], querySuccess, errorCB);
	}

	function querySuccess(tx, results) {
		// 아무 열들도 삽입되지 않았기 때문에 비어있다.
		console.log("Insert ID = " + results.insertId);
		// select 구문때문에 0일 것이다.
		console.log("Rows Affected = " + results.rowAffected);
		// select 구문에 의해 반환되는 열들의 개수.
		console.log("Insert ID = " + results.rows.length);
	}
	
	function errorCB(err) {
		alert("Error processing SQL: "+err.code);
	}
	
	var db = window.openDatabase("Database", "1.0", "PhoneGap Demo", 200000);
	db.transaction(queryDB, errorCB);

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

		// database를 채운다.
		//
		function populateDB(tx) {
			tx.executeSql('DROP TABLE IF EXISTS DEMO');
			tx.executeSql('CREATE TABLE IF NOT EXISTS DEMO (id unique, data)');
			tx.executeSql('INSERT INTO DEMO (id, data) VALUES (1, "First row")');
			tx.executeSql('INSERT INTO DEMO (id, data) VALUES (2, "Second row")');
		}

		// database를 조회한다.
		//
		function queryDB(tx) {
			tx.executeSql('SELECT * FROM DEMO', [], querySuccess, errorCB);
		}

		// Query the success callback
		//
		function querySuccess(tx, results) {
			// 아무 열들도 삽입되지 않았기 때문에 비어있다.
			console.log("Insert ID = " + results.insertId);
			// select 구문때문에 0일 것이다.
			console.log("Rows Affected = " + results.rowAffected);
			// select 구문에 의해 반환되는 열들의 개수.
			console.log("Insert ID = " + results.rows.length);
		}

		// error callback 처리
		//
		function errorCB(err) {
			console.log("Error processing SQL: "+err.code);
		}

		// success callback 처리
		//
		function successCB() {
			var db = window.openDatabase("Database", "1.0", "PhoneGap Demo", 200000);
			db.transaction(queryDB, errorCB);
		}

		// PhoneGap이 준비되면 호출된다
		//
		function onDeviceReady() {
			var db = window.openDatabase("Database", "1.0", "PhoneGap Demo", 200000);
			db.transaction(populateDB, errorCB, successCB);
		}
	
        </script>
      </head>
      <body>
        <h1>Example</h1>
        <p>Database</p>
      </body>
    </html>
