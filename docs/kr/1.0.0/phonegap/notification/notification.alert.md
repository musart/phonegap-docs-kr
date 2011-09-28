notification.alert
==================

사용자 경고창이나 다이얼로그 박스를 보여준다.

    navigator.notification.alert(message, alertCallback, [title], [buttonName])

- __message:__ 다이얼로그 메세지 (`String`)
- __alertCallback:__ 경고창이 사라질때 불리는 콜백. (`Function`)
- __title:__ 다이얼로그 타이틀 (String`) (선택적인 변수, 기본값: "Alert")
- __buttonName:__ 버튼 이름 (`String`) (선택적인 변수, 기본값: "OK")
    
설명
-----------

대부분의 PhoneGap 구현들은 이 기능을 위해 네이티브 다이얼로그 박스를 사용한다. 하지만 일부 플랫폼은 일반적으로 사용자가 바꾸기 힘든 브라우저의 'alert' 함수를 사용한다.

지원하는 플랫폼
-------------------

- Android
- BlackBerry (OS 4.6)
- BlackBerry WebWorks (OS 5.0 and higher)
- iPhone

빠른 예제
-------------

    // Android / BlackBerry WebWorks (OS 5.0 and higher) / iPhone
    //
    function alertDismissed() {
        // 무언가 한다.
    }

    navigator.notification.alert(
        'You are the winner!',  // message
        alertDismissed,         // callback
        'Game Over',            // title
        'Done'                  // buttonName
    );

    // BlackBerry (OS 4.6) / webOS
    //
    navigator.notification.alert('You are the winner!');
        
전체 예제
------------

    <!DOCTYPE html>
    <html>
      <head>
        <title>Notification Example</title>

        <script type="text/javascript" charset="utf-8" src="phonegap.js"></script>
        <script type="text/javascript" charset="utf-8">

        // PhoneGap이 로드되기를 기다린다
        //
        document.addEventListener("deviceready", onDeviceReady, false);

        // PhoneGap이 준비되면 호출된다
        //
        function onDeviceReady() {
            // Empty
        }
    
        // 경고창이 사라진다.
	    function alertDismissed() {
	        // 무언가 한다.
	    }

        // 사용자 경고창을 보여준다.
        //
        function showAlert() {
		    navigator.notification.alert(
		        'You are the winner!',  // message
		        alertDismissed,         // callback
		        'Game Over',            // title
		        'Done'                  // buttonName
		    );
        }
    
        </script>
      </head>
      <body>
        <p><a href="#" onclick="showAlert(); return false;">Show Alert</a></p>
      </body>
    </html>
