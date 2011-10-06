connection.type
===================

사용되고 있는 유효한 네트워크 연결을 점검한다.

설명
-----------

이 프로퍼티는 기기의 네트워크 연결 상태와 연결 타입을 알아내기 위한 빠른 방법이다.


지원하는 플랫폼
-------------------

- iOS
- Android
- BlackBerry WebWorks (OS 5.0 and higher)

빠른 예제
-------------

    function checkConnection() {
        var networkState = navigator.network.connection.type;
        
        var states = {};
        states[Connection.UNKNOWN]	= 'Unknown connection';
        states[Connection.ETHERNET]	= 'Ethernet connection';
        states[Connection.WIFI]   	= 'WiFi connection';
        states[Connection.CELL_2G]	= 'Cell 2G connection';
        states[Connection.CELL_3G]	= 'Cell 3G connection';
        states[Connection.CELL_4G]	= 'Cell 4G connection';
        states[Connection.NONE]   	= 'No network connection';
    
        alert('Connection type: ' + states[networkState]);
    }
    
    checkConnection();


전체 예제
------------

    <!DOCTYPE html>
    <html>
      <head>
        <title>navigator.network.connection.type Example</title>
        
        <script type="text/javascript" charset="utf-8" src="phonegap.js"></script>
        <script type="text/javascript" charset="utf-8">
            
        // PhoneGap이 로드되기를 기다린다
        // 
        document.addEventListener("deviceready", onDeviceReady, false);
        
        // PhoneGap이 로드되고 PhoneGap 함수를 호출하는데 안전하다.
        //
        function onDeviceReady() {
            checkConnection();
        }
        
	    function checkConnection() {
	        var networkState = navigator.network.connection.type;

	        var states = {};
	        states[Connection.UNKNOWN]	= 'Unknown connection';
	        states[Connection.ETHERNET]	= 'Ethernet connection';
	        states[Connection.WIFI]   	= 'WiFi connection';
	        states[Connection.CELL_2G]	= 'Cell 2G connection';
	        states[Connection.CELL_3G]	= 'Cell 3G connection';
	        states[Connection.CELL_4G]	= 'Cell 4G connection';
	        states[Connection.NONE]   	= 'No network connection';

	        alert('Connection type: ' + states[networkState]);
	    }
        
        </script>
      </head>
      <body>
        <p>A dialog box will report the network state.</p>
      </body>
    </html>
