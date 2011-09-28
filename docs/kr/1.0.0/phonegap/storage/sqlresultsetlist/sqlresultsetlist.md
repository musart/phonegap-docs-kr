SQLResultSetList
=======

SQL ¿¿¿¿¿ ¿¿¿¿ ¿¿¿ ¿¿¿¿ SQLResultSet¿ ¿¿¿ ¿¿.

Properties
-------

- __length__: SQL ¿¿¿ ¿¿ ¿¿¿¿ ¿¿ ¿¿.

Methods
-------

- __item__: ¿¿¿¿¿¿ ¿¿¿ ¿¿ ¿¿¿¿ ¿¿¿ ¿¿¿¿ ¿¿ ¿¿¿¿.

Details
-------

SQLResultSetList¿ SQL select ¿¿¿ ¿¿ ¿¿¿¿ ¿¿¿¿ ¿¿¿¿. ¿ ¿¿¿ ¿¿¿ ¿¿ select ¿¿¿ length ¿¿¿ ¿¿¿¿.
The SQLResultSetList contains the data returned from a SQL select statement.  The object contains a length property letting you know how many rows the select statement has been returned.  To get a row of data you would call the `item` method specifing an index.  The item method returns a JavaScript Object who's properties are the columns of the database the select statement was executed against.

¿¿¿¿ ¿¿¿
-------------------

- Android
- BlackBerry WebWorks (OS 6.0 and higher)
- iPhone

Execute SQL ¿¿ ¿¿
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

¿¿ ¿¿
------------

    <!DOCTYPE html>
    <html>
      <head>
        <title>Contact Example</title>

        <script type="text/javascript" charset="utf-8" src="phonegap.js"></script>
        <script type="text/javascript" charset="utf-8">

        // PhoneGap¿ ¿¿¿¿¿ ¿¿¿¿.
        //
        document.addEventListener("deviceready", onDeviceReady, false);

		// database¿ ¿¿¿.
		//
		function populateDB(tx) {
			tx.executeSql('DROP TABLE IF EXISTS DEMO');
			tx.executeSql('CREATE TABLE IF NOT EXISTS DEMO (id unique, data)');
			tx.executeSql('INSERT INTO DEMO (id, data) VALUES (1, "First row")');
			tx.executeSql('INSERT INTO DEMO (id, data) VALUES (2, "Second row")');
		}

		// database ¿¿¿¿.
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

		// error callback ¿¿
		//
		function errorCB(err) {
			console.log("Error processing SQL: "+err.code);
		}

		// success callback ¿¿
		//
		function successCB() {
			var db = window.openDatabase("Database", "1.0", "PhoneGap Demo", 200000);
			db.transaction(queryDB, errorCB);
		}

		// PhoneGap¿ ¿¿¿¿ ¿¿¿¿.
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
