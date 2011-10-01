LocalFileSystem
===============

이 객체는 root 파일 시스템을 얻는 방법을 제공한다.

Methods
----------

- __requestFileSystem:__ 파일시스템을 요청한다. _(Function)_
- __resolveLocalFileSystemURI:__ local URI를 사용하여 DirectoryEntry나 FileEntry 를 검색한다. _(Function)_

Constants
---------

- `LocalFileSystem.PERSISTENT`: 어플리케이션이나 사용자 권한 없이 삭제되지 않아야 하는 저장소를 위해 사용됨.
- `LocalFileSystem.TEMPORARY`: 지속성을 보장할 필요가 없는 저장소를 위해 사용됨.

Details
-------

`LocalFileSystem` 객체 함수는 __window__ 객체에 정의되어 있다.

지원하는 플랫폼
-------------------

- Android
- BlackBerry WebWorks (OS 5.0 and higher)
- iOS

Request File System 빠른 예제
---------------------------------

	function onSuccess(fileSystem) {
		console.log(fileSystem.name);
	}
	
	// 지속되는 파일 시스템을 요청한다.
	window.requestFileSystem(LocalFileSystem.PERSISTENT, 0, onSuccess, onError);

Resolve Local File System URI 빠른 예제
-------------------------------------------

	function onSuccess(fileEntry) {
		console.log(fileEntry.name);
	}

	window.resolveLocalFileSystemURI("file:///example.txt", onSuccess, onError);
	
전체 예제
------------


    <!DOCTYPE html>
    <html>
      <head>
        <title>Local File System Example</title>

        <script type="text/javascript" charset="utf-8" src="phonegap.js"></script>
        <script type="text/javascript" charset="utf-8">

        // PhoneGap이 로드되기를 기다린다
        //
        document.addEventListener("deviceready", onDeviceReady, false);

        // PhoneGap이 준비되면 호출된다
        //
        function onDeviceReady() {
			window.requestFileSystem(LocalFileSystem.PERSISTENT, 0, onFileSystemSuccess, fail);
			window.resolveLocalFileSystemURI("file:///example.txt", onResolveSuccess, fail);
        }

		function onFileSystemSuccess(fileSystem) {
			console.log(fileSystem.name);
		}

		function onResolveSuccess(fileEntry) {
			console.log(fileEntry.name);
		}
		
		function fail(evt) {
			console.log(evt.target.error.code);
		}
		
        </script>
      </head>
      <body>
        <h1>Example</h1>
        <p>Local File System</p>
      </body>
    </html>
