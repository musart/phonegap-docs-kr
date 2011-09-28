notification.confirm
====================

사용자 조정 가능한 확인창을 보여준다.

    navigator.notification.confirm(message, confirmCallback, [title], [buttonLabels])

- __message:__ 다이얼로그 메세지 (`String`)
- __confirmCallback:__ - 선택된 버튼의 색인을 호출하는 콜백 (1, 2 or 3). (`Number`)
- __title:__ 다이얼로그 제목 (`String`) (선택적인 변수, 기본값: "Confirm")
- __buttonLabels:__ 버튼 이름에 대한 쉽표로 분리된 문자열 (`String`) (선택적인 변수, 기본값: "OK,Cancel")
    
설명
-----------

`notification.confirm` 함수는 브라우저의 'confirm' 함수대신 더 사용자 설정가능한 네이티브 다이얼로그 박스를 표시한다.

지원하는 플랫폼
-------------------

- Android
- BlackBerry WebWorks (OS 5.0 and higher)
- iPhone

빠른 예제
-------------

	// 확인창의 결과를 처리한다.
	function onConfirm(button) {
		alert('You selected button ' + button);
	}

    // 사용자 확인 창을 보여준다.
    //
    function showConfirm() {
        navigator.notification.confirm(
	        'You are the winner!',  // message
			onConfirm,				// 선택된 버튼의 색인을 호출하는 콜백
	        'Game Over',            // title
	        'Restart,Exit'          // buttonLabels
        );
    }
        
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
    
		// 확인창의 결과를 처리한다.
		function onConfirm(button) {
			alert('You selected button ' + button);
		}

        // 사용자 확인 창을 보여준다.
        //
        function showConfirm() {
            navigator.notification.confirm(
		        'You are the winner!',  // message
				onConfirm,				// 선택된 버튼의 색인을 호출하는 콜백
		        'Game Over',            // title
		        'Restart,Exit'          // buttonLabels
            );
        }
    
        </script>
      </head>
      <body>
        <p><a href="#" onclick="showConfirm(); return false;">Show Confirm</a></p>
      </body>
    </html>
