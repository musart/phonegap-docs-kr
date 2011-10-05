FileReader
==========

FileReader 는 파일을 읽도록 가능하게 하는 객체이다.

Properties
----------

- __readyState:__ EMPTY, LOADING, DONE 가운데 reader가 될 수 있는 3가지 상태 중에 하나.
- __result:__ 파일의 읽혀진 내용. _(DOMString)_
- __error:__ 에러를 담은 객체. _(FileError)_
- __onloadstart:__ 읽기 시작하면 호출됨. _(Function)_
- __onprogress:__ 파일을 읽는 동안에 호출되고 진행상태를 보고함 (progess.loaded/progress.total). _(Function)_ -NOT SUPPORTED
- __onload:__ 읽기가 성공적으로 완료되었을 경우 호출됨. _(Function)_
- __onabort:__ 읽기가 중단되었을 경우 호출됨. 예를 들면, abort() 함수 호출될 경우. _(Function)_
- __onerror:__ 읽기가 실패했을 경우 호출됨. _(Function)_
- __onloadend:__ 요청이 완료되었을 경우 (또는 성공이나 실패시) 호출됨. _(Function)_

Methods
-------

- __abort__: 파일을 읽는 것을 중단시킨다.
- __readAsDataURL__: 파일을 읽고 base64로 함호화된 데이터 url을 반환한다.
- __readAsText__: text 파일을 읽는다.

Details
-------

`FileReader` 객체는 기기의 파일시스템으로부터 파일들을 읽는 방법이다. 파일들은 text로 읽히거나 base64로 암호화된 문자열로 읽힌다. 사용자들은 loadstart, progress, load, loadend, error 그리고 abort 에벤트를 받기 위해 자신의 이벤트 리스너를 등록한다.

지원하는 플랫폼
-------------------

- Android
- BlackBerry WebWorks (OS 5.0 and higher)
- iOS

Read As Data URL 
----------------

__Parameters:__

- file - 읽기 위한 file 객체


빠른 예제
-------------

	function win(file) {
		var reader = new FileReader();
		reader.onloadend = function(evt) {
        	console.log("read success");
            console.log(evt.target.result);
        };
		reader.readAsDataURL(file);
	};

	var fail = function(evt) {
    	console.log(error.code);
	};
	
    entry.file(win, fail);

Read As Text
------------

__Parameters:__

- file - 읽기 위한 file 객체
- encoding - file의 컨텐츠를 암호화 하기 위해 사용되는 암호 코드. 기본값은 UTF8이다.

빠른 예제
-------------

	function win(file) {
		var reader = new FileReader();
		reader.onloadend = function(evt) {
        	console.log("read success");
            console.log(evt.target.result);
        };
		reader.readAsText(file);
	};

	var fail = function(evt) {
    	console.log(error.code);
	};
	
    entry.file(win, fail);

Abort 빠른 예제
-------------------

	function win(file) {
		var reader = new FileReader();
		reader.onloadend = function(evt) {
        	console.log("read success");
            console.log(evt.target.result);
        };
		reader.readAsText(file);
		reader.abort();
	};

    function fail(error) {
    	console.log(error.code);
    }
	
    entry.file(win, fail);

전체 예제
------------

    <!DOCTYPE html>
    <html>
      <head>
        <title>FileReader Example</title>

        <script type="text/javascript" charset="utf-8" src="phonegap.js"></script>
        <script type="text/javascript" charset="utf-8">

        // PhoneGap이 로드되기를 기다린다
        //
        function onLoad() {
            document.addEventListener("deviceready", onDeviceReady, false);
        }

        // PhoneGap이 준비되면 호출된다
        //
        function onDeviceReady() {
			window.requestFileSystem(LocalFileSystem.PERSISTENT, 0, gotFS, fail);
        }
		
		function gotFS(fileSystem) {
			fileSystem.root.getFile("readme.txt", {create: true}, gotFileEntry, fail);
		}
		
		function gotFileEntry(fileEntry) {
			fileEntry.file(gotFile, fail);
		}
		
        function gotFile(file){
			readDataUrl(file);
			readAsText(file);
		}
        
        function readDataUrl(file) {
            var reader = new FileReader();
            reader.onloadend = function(evt) {
                console.log("Read as data URL");
                console.log(evt.target.result);
            };
            reader.readAsDataURL(file);
        }
        
        function readAsText(file) {
            var reader = new FileReader();
            reader.onloadend = function(evt) {
                console.log("Read as text");
                console.log(evt.target.result);
            };
            reader.readAsText(file);
        }
        
        function fail(evt) {
            console.log(evt.target.error.code);
        }
        
        </script>
      </head>
      <body>
        <h1>Example</h1>
        <p>Read File</p>
      </body>
    </html>

iOS Quirks
----------
- __encoding__ 인자는 지원되지 않는다. UTF8 인코딩이 항상 사용된다.
