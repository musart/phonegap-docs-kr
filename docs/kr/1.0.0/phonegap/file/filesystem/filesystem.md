FileSystem
==========

This object represents a file system.

Properties
----------

- __name:__ The name of the file system. _(DOMString)_
- __root:__ The root directory of the file system. _(DirectoryEntry)_

Details
-------

The `FileSystem` object represents information about the file system. The name of the file system will be unique across the list of exposed file systems.  The root property contains a `DirectoryEntry` object which represents the root directory of the file system.

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
	
	// request the persistent file system
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
