DirectoryEntry
==============

이 객체는 파일 시스템의 디렉토리를 나타낸다. [W3C Directories and Systems](http://www.w3.org/TR/file-system-api/) 표준에 정의되어 있다.

Properties
----------

- __isFile:__ 항상 false. _(boolean)_
- __isDirectory:__ 항상 true. _(boolean)_
- __name:__ DirectoryEntry의 이름, excluding the path leading to it. _(DOMString)_
- __fullPath:__ root로부터 DirectoryEntry까지 전체 절대 경로. _(DOMString)_

NOTE: 다음의 속성들은 W3C 표준에 정의되어 있지만 PhoneGap은 지원하지 __not supported__ 않는다:

- __filesystem:__ DirectoryEntry가 위치하는 파일 시스템. _(FileSystem)_ 

Methods
-------

다음의 함수들은 DirectoryEntry 객체에서 호출 가능하다.

- __getMetadata__: 디렉토리에 대해 메타데이터를 찾아본다.
- __moveTo__: 디렉토리를 파일 시스템 상의 다른 위치로 이동한다.
- __copyTo__: 디렉토리를 파일 시스템 상의 다른 위치로 복사한다.
- __toURI__: 디렉토리를 위치하기위해 사용되는 URI를 반환한다.
Return a URI that can be used to locate a directory.
- __remove__: 디렉토리를 지운다. 디렉토리는 비어있어야 한다.
- __getParent__: 부모 디렉토리를 찾아본다.
- __createReader__: 디렉토리로부터 엔트리들을 읽을 수 있는 새로운 DirectoryReader를 생성한다.
- __getDirectory__: 디렉토리를 생성하거나 찾아본다.
- __getFile__: 파일을 생성하거나 찾아본다.
- __removeRecursively__: 디렉토리와 그 안의 모든 컨텐츠를 제거한다.

지원하는 플랫폼
-------------------

- Android
- BlackBerry WebWorks (OS 5.0 and higher)
- iOS

getMetadata
-----------

디렉토리에 대한 메타데이터를 찾아본다.

__Parameters:__

- __successCallback__ - 메타데이터 객체와 함께 호출되는 콜백. _(Function)_
- __errorCallback__ - 메타데이터를 검색하다가 에러가 발생하면 호출되는 콜백. FileError 객체와 함께 호출된다. _(Function)_


__빠른 예제__

    function success(metadata) {
        console.log("Last Modified: " + metadata.modificationTime);
    }

    function fail(error) {
        alert(error.code);
    }

    // 이 엔트리의 메타데이터 객체를 요청한다.
    entry.getMetadata(success, fail);	


moveTo
------

디렉토리를 파일 시스템의 다른 위치에 이동한다. 다음을 수행하면 에러이다:

- 어떤 디렉토리를 자신 안으로 또는 아래 위치의 자식으로 이동한다:
- 현재와 다른 이름으로 규정되지 않는 디렉토리를 자신의 부모로 이동한다.
- 다른 파일에 의해 사용되는 경로로 디렉토리를 이동한다;
- 비어있지 않은 디렉토리에 의해 사용되는 경로로 디렉토리를 이동한다.

추가적으로, 디렉토리를 기존의 빈 디렉토리로 이동하기 위한 시도는 반드시 그 디렉토리를 지우고 교체한다.

__Parameters:__

- __parent__ - 디렉토리를 이동하기 위한 부모 디렉토리. _(DirectoryEntry)_
- __newName__ - 디렉토리의 새 이름. 명시되어 있지 않으면 현재이름이 기본값이다. _(DOMString)_
- __successCallback__ - 새 디렉토리의 DirectoryEntry 객체와 함께 호출되는 콜백. _(Function)_
- __errorCallback__ - 디렉토리를 이동하다가 에러가 발생하면 호출되는 콜백. FileError 객체와 함께 발생한다. _(Function)_


__빠른 예제__

    function success(entry) {
        console.log("New Path: " + entry.fullPath);
    }

    function fail(error) {
        alert(error.code);
    }
	
	function moveDir(entry) {
        var parent = document.getElementById('parent').value,
            newName = document.getElementById('newName').value,
            parentEntry = new DirectoryEntry({fullPath: parent});

        // 디렉토리를 새 디렉토리로 이동하고 이름을 변경한다.
        entry.moveTo(parentEntry, newName, success, fail);
    }

copyTo
------

디렉토리를 파일시스템의 다른 위치에 복사한다. 다음을 수행하면 에러이다:

- 자기 자신안의 위치에 디렉토리를 복사한다:
- 현재와 다른 이름으로 규정되지 않는 디렉토리를 자신의 부모로 복사한다.

디렉토리 복사는 항상 재귀적이다 - 즉, 디렉토리의 모든 컨텐츠를 복사한다.

__Parameters:__

- __parent__ - 디렉토리를 복사하기 위한 부모 디렉토리. _(DirectoryEntry)_
- __newName__ - 디렉토리의 새 이름. 명시되어 있지 않으면 현재 이름을 기본값으로 사용한다. _(DOMString)_
- __successCallback__ - 새 디렉토리의 DirectoryEntry 객체와 함께 호출되는 콜백. _(Function)_
- __errorCallback__ - 밑에 있는 디렉토리를 복사하다가 에러가 발생하면 호출되는 콜백. FileError 객체와 함께 발생한다. _(Function)_


__빠른 예제__

	function win(entry) {
		console.log("New Path: " + entry.fullPath);
	}
	
	function fail(error) {
		alert(error.code);
	}
	
	function copyDir(entry) {
        var parent = document.getElementById('parent').value,
            newName = document.getElementById('newName').value,
            parentEntry = new DirectoryEntry({fullPath: parent});

        // 디렉토리를 새 디렉토리로 복사하고 이름을 바꾼다.
        entry.copyTo(parentEntry, newName, success, fail);
    }


toURI
-----

디렉토리의 정확한 위치를 찾기 위해 사용되는 URI를 반환한다.

__빠른 예제__
	
    // 이 디렉토리의 URI를 얻는다.
    var uri = entry.toURI();
    console.log(uri);


remove
------

디렉토리를 제거한다. 다음을 수행하면 에러이다:

- 비어있지 않은 디렉토리를 제거한다:
- 파일시스템의 root 디렉토리를 제거한다.

__Parameters:__

- __successCallback__ - 디렉토리가 지위지고 난 뒤 호출되는 콜백. 아무 인자 없이 호출된다. _(Function)_
- __errorCallback__ - 디렉토리를 제거하다가 에러가 발생하면 호출되는 콜백. FileError 객체와 함께 발생한다. _(Function)_

__빠른 예제__
	
    function success(entry) {
        console.log("Removal succeeded");
    }

    function fail(error) {
        alert('Error removing directory: ' + error.code);
    }

    // 이 디렉토리를 제거한다.
    entry.remove(success, fail);


getParent
---------

디렉토리를 담고있는 부모 DirectoryEntry를 검색한다.

__Parameters:__

- __successCallback__ - 디렉토리의 부모 DirectoryEntry와 함께 호출되는 콜백. _(Function)_
- __errorCallback__ - 부모 DirectoryEntry를 검색하다가 에러가 발생하면 호출되는 콜백. FileError 객체와 함께 발생한다. _(Function)_

__빠른 예제__
	
    function success(parent) {
        console.log("Parent Name: " + parent.name);
    }
 
    function fail(error) {
        alert('Failed to get parent directory: ' + error.code);
    }
	
	// 부모 DirectoryEntry를 얻는다.
	entry.getParent(success, fail);	


createReader
------------

디렉토리에서 엔트리들을 읽기 위해 새로운 DirectoryReader를 생성한다.

__빠른 예제__
	
    // 디렉토리 reader를 생성한다.
    var directoryReader = entry.createReader();	


getDirectory
------------

기존의 디렉토리를 생성하거나 검색한다. 다음을 수행하면 에러이다:

- 직속 부모가 아직 존재하지 않는 디렉토리를 생성한다. 

__Parameters:__

- __path__ - 생성되거나 검색된 디렉토리의 경로. 절대 경로이거나 이 DirectoryEntry부터의 상대 경로. _(DOMString)_
- __options__ - 디렉토리가 존재하지 않을 경우 생성되었는지를 명시하는 옵션. _(Flags)_
- __successCallback__ - DirecotyrEntry 객체와 함께 호출되는 콜백. _(Function)_
- __errorCallback__ - 디렉토리를 생성하거나 찾다가 에러가 발생하면 호출되는 콜백. FileError 객체와 함께 발생한다. _(Function)_

__빠른 예제__
	
    function success(parent) {
        console.log("Parent Name: " + parent.name);
    }

    function fail(error) {
        alert("Unable to create new directory: " + error.code);
    }

    // 기존의 디렉토리를 검색하거나, 존재하지 않는다면 생성한다.
    entry.getDirectory("newDir", {create: true, exclusive: false}, success, fail);	


getFile
-------

파일을 생성하거나 검색한다. 다음을 시도하면 에러이다:

- 직속 부모가 아직 없는 파일을 생성한다.

__Parameters:__

- __path__ - 생성되거나 검색되는 파일의 경로. 절대 경로이거나 이 DirectoryEntry로부터의 상대 경로. _(DOMString)_
- __options__ - Options to specify whether the file is created if it doesn't exist.  _(Flags)_
- __successCallback__ - FileEntry 객체와 함께 발생되는 콜백. _(Function)_
- __errorCallback__ - 파일을 생성하거나 찾다가 에러가 발생하면 호출되는 콜백. FileError 객체와 함께 발생한다. _(Function)_

__빠른 예제__
	
    function success(parent) {
        console.log("Parent Name: " + parent.name);
    }

    function fail(error) {
        alert("Failed to retrieve file: " + error.code);
    }

    // 파일을 검색하거나, 존재하지 않으면 생성한다.
    entry.getFile("newFile.txt", {create: true, exclusive: false}, success, fail);	


removeRecursively
-----------------

디렉토리와 그 안의 모든 컨텐츠를 제거한다. 에러 이벤트 가운데 (e.g. 지워질 수 없는 파일을 포함한 디렉토리를 지위기 위해 시도하는), 일부 디렉토리의 컨텐츠들은 아마 지워질 것이다. 다음을 수행하면 에러이다:

- 파일 시스템의 root 디레토리를 제거한다.

__Parameters:__

- __successCallback__ - DirectoryEntry가 지워진 뒤 호출되는 콜백
- __errorCallback__ - DirectoryEntry를 지울때 에러가 발생하면 호출되는 콜백. FileError 객체와 함께 호출된다. _(Function)_

__빠른 예제__
	
    function success(parent) {
        console.log("Remove Recursively Succeeded");
    }

    function fail(error) {
        alert("Failed to remove directory or it's contents: " + error.code);
    }

    // 디렉토리와 그 안의 모든 컨텐츠를 제거한다.
    entry.removeRecursively(success, fail);	
