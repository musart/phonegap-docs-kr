FileSystem
==========

이 객체는 파일 시스템을 나타낸다.

Properties
----------

- __name:__ 파일 시스템의 이름. _(DOMString)_
- __root:__ 파일 시스템의 root 디렉토리. _(DirectoryEntry)_

Details
-------

`FileSystem` 객체는 파일시스템 관련 정보를 나타낸다. 파일 시스템의 이름은 모든 노출된 파일시스템의 리스트에 유일하다. root 속성은 파일 시스템의 root 디렉토리를 나타내는 'DirectoryEntry' 객체를 포함한다.

지원하는 플랫폼
-------------------

- Android
- BlackBerry WebWorks (OS 5.0 and higher)
- iOS

File System 빠른 예제
-------------------------

	function onSuccess(fileSystem) {
		console.log(fileSystem.name);
		console.log(fileSystem.root.name);
	}
	
	// 지속되는 파일시스템을 요청한다.
	window.requestFileSystem(LocalFileSystem.PERSISTENT, 0, onSuccess, null);

전체 예제
------------

    <!DOCTYPE html>
    <html>
      <head>
        <title>File System Example</title>

        <script type="text/javascript" charset="utf-8" src="phonegap.js"></script>
        <script type="text/javascript" charset="utf-8">

        // PhoneGap이 로드되기를 기다린다
        //
        document.addEventListener("deviceready", onDeviceReady, false);

        // PhoneGap이 준비되면 호출된다
        //
        function onDeviceReady() {
			window.requestFileSystem(LocalFileSystem.PERSISTENT, 0, onFileSystemSuccess, fail);
        }

		function onFileSystemSuccess(fileSystem) {
			console.log(fileSystem.name);
			console.log(fileSystem.root.name);
		}
		
		function fail(evt) {
			console.log(evt.target.error.code);
		}
		
        </script>
      </head>
      <body>
        <h1>Example</h1>
        <p>File System</p>
      </body>
    </html>
