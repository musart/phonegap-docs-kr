FileWriter
==========

FileWriter 는 파일을 쓰도록 가능하게 하는 객체이다.

Properties
----------

- __readyState:__ INIT, WRITING, DONE 가운데 writer가 될 수 있는 3가지 상태 중에 하나.
- __fileName:__ 쓰여진 파일 이름. _(DOMString)_
- __length:__ 쓰여진 파일 길이. _(long)_
- __position:__ 파일 포인터의 현재 위치. _(long)_
- __error:__ 에러를 가진 객체. _(FileError)_
- __onwritestart:__ 쓰기 시작하면 호출됨. _(Function)_
- __onprogress:__ 파일을 쓰는 동안에 호출되고 진행상태를 보고함 (progess.loaded/progress.total). _(Function)_ -NOT SUPPORTED
- __onwrite:__ 요청이 성공적으로 완료되었을 경우 호출됨. _(Function)_
- __onabort:__ 쓰기가 중단되었을 경우 호출됨. 예를 들면, abort() 함수가 호출될 경우. _(Function)_
- __onerror:__ 쓰기가 실패했을 경우 호출됨. _(Function)_
- __onwriteend:__ 요청이 완료되었을 경우 (또는 성공이나 실패시) 호출됨 _(Function)_

Methods
-------

- __abort__: 파일을 쓰는 것을 중단시킨다.
- __seek__: 파일 포인터를 지정된 바이트로 이동한다.
- __truncate__: 파일을 지정된 길이로 짧게한다.
- __write__: 파일에 데이터를 쓴다.

Details
-------

`FileWriter` 객체는 기기의 파일시스템으로부터 파일을 쓰는 방법이다. 사용자는 writestart, progress, write, writeend, error 그리고 abort 이벤트를 받기 위해 자신의 이벤트 리스터를 등록한다.

FileWriter 는 단일 파일을 위해 생성된다. 당신은 여러번 파일에 쓸수 있다. FileWriter는 파일의 position과 length 속성을 관리하기 때문에 파일안에서 자유롭게 검색하고 쓸 수 있다. 기본적으로 FileWriter 는 파일의 시작점에 (기존에 존자하는 데이터에 덮어)쓴다. FileWriter의 생성자에 optional append boolean을 true로 하면 파일의 끝에서부터 쓴다.

지원하는 플랫폼
-------------------

- Android
- BlackBerry WebWorks (OS 5.0 and higher)
- iOS

Seek 빠른 예제
------------------------------

	function win(writer) {
		// 파일포인터를 파일의 끝으로 이동한다.
		writer.seek(writer.length);	
	};

	var fail = function(evt) {
    	console.log(error.code);
	};
	
    entry.createWriter(win, fail);

Truncate 빠른 예제
--------------------------

	function win(writer) {
		writer.truncate(10);	
	};

	var fail = function(evt) {
    	console.log(error.code);
	};
	
    entry.createWriter(win, fail);

Write 빠른 예제
-------------------	

	function win(writer) {
		writer.onwrite = function(evt) {
        	console.log("write success");
        };
		writer.write("some sample text");
	};

	var fail = function(evt) {
    	console.log(error.code);
	};
	
    entry.createWriter(win, fail);

Append 빠른 예제
--------------------	

	function win(writer) {
		writer.onwrite = function(evt) {
        	console.log("write success");
        };
        writer.seek(writer.length);
		writer.write("appended text");
	};

	var fail = function(evt) {
    	console.log(error.code);
	};
	
    entry.createWriter(win, fail);
	
Abort 빠른 예제
-------------------

	function win(writer) {
		writer.onwrite = function(evt) {
        	console.log("write success");
        };
		writer.write("some sample text");
		writer.abort();
	};

	var fail = function(evt) {
    	console.log(error.code);
	};
	
    entry.createWriter(win, fail);

전체 예제
------------
    <!DOCTYPE html>
    <html>
      <head>
        <title>FileWriter Example</title>

        <script type="text/javascript" charset="utf-8" src="phonegap.0.9.4.js"></script>
        <script type="text/javascript" charset="utf-8">

        // PhoneGap이 로드되기를 기다린다
        //
        document.addEventListener("deviceready", onDeviceReady, false);

        // PhoneGap이 준비되면 호출된다
        //
        function onDeviceReady() {
			window.requestFileSystem(LocalFileSystem.PERSISTENT, 0, gotFS, fail);
        }
		
		function gotFS(fileSystem) {
			fileSystem.root.getFile("readme.txt", {create: true}, gotFileEntry, fail); 
		}
		
		function gotFileEntry(fileEntry) {
			fileEntry.createWriter(gotFileWriter, fail);
		}
		
		function gotFileWriter(writer) {
	        writer.onwrite = function(evt) {
                console.log("write success");
            };
            writer.write("some sample text");
			// 파일의 내용은 이제 'some sample text' 이다.
			writer.truncate(11);
			// 파일의 내용은 이제 'some sample' 이다.
			writer.seek(4);
			// 파일의 내용은 여전히 'some sample' 이지만 파일 포인터는 'some'의 'e' 다음이다.
			writer.write(" different text");
			// 파일의 내용은 이제 'some different text' 이다.
		}
        
        function fail(error) {
            console.log(error.code);
        }
        
        </script>
      </head>
      <body>
        <h1>Example</h1>
        <p>Write File</p>
      </body>
    </html>
