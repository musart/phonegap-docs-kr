SQLResultSetList
=======

SQL 쿼리로부터 반환된 rows를 포함하는 SQLResultSet의 속성 중 하나.

Properties
-------

- __length__: SQL 쿼리로부터 반환된 rows의 개수

Methods
-------

- __item__: 자바스크립트 객체에 의해 표현된 특정 인텍스에 있는 row를 반환한다.

Details
-------

SQLResultSetList 는 SQL select 구문으로부터 반환된 데이터를 포함한다. 이 객체는 얼마나 많은 rows가 select 구문에 의해 반환되었는지를 알려주는 length 속성을 담고있다. 데이터의 row를 얻기 위해서는 인텍스를 명기하여 'item' 함수를 호출한다. item 함수는 select 구문이 실행된 이후 database의 columns 속성인 자바스크립트 객체를 반환한다. 

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
                var len = results.rows.length;
                console.log("DEMO table: " + len + " rows found.");
                for (var i=0; i<len; i++){
                console.log("Row = " + i + " ID = " + results.rows.item(i).id + " Data =  " + results.rows.item(i).data);
                }
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

        // PhoneGap이 로드되기를 기다린다.
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
                        var len = results.rows.length;
                        console.log("DEMO table: " + len + " rows found.");
                        for (var i=0; i<len; i++){
                                console.log("Row = " + i + " ID = " + results.rows.item(i).id + " Data =  " + results.rows.item(i).data);
                        }
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

                // PhoneGap이 준비된다.
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
