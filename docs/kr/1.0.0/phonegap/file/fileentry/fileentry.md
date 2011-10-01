FileEntry
==========

이 객체는 파일 시스템의 파일을 나타낸다. [W3C Directories and Systems](http://www.w3.org/TR/file-system-api/) 표준에 정의되어 있다.

Properties
----------

- __isFile:__ 항상 true이다. _(boolean)_
- __isDirectory:__ 항상 false이다. _(boolean)_
- __name:__ FileEntry의 이름, excluding the path leading to it. _(DOMString)_
- __fullPath:__ root부터 FileEntry까지 전체 절대 경로. _(DOMString)_

NOTE: 다음의 속성은 W3C 표준에 정의되어 있지만, PhoneGap은 지원되지 __not supported__ 않는다:

- __filesystem:__ FileEntry가 위치하는 파일 시스템. _(FileSystem)_


Methods
-------

- __getMetadata__: 파일의 metadata를 찾아본다. 
- __moveTo__: 파일을 파일 시스템 상의 다른 위치로 이동한다.
- __copyTo__: 파일을 파일 시스템 상의 다른 위치로 복사한다.
- __toURI__: 파일의 위치를 찾아내기 위해 사용되는 URI를 반환한다.
- __remove__: 파일을 삭제한다.
- __getParent__: 부모 디렉토리를 찾아본다.
- __createWriter__: 파일을 쓰기위해 사용되는 FileWriter 객체를 생성한다.
- __file__: 파일 속성들을 담고 있는 File 객체를 생성한다.


지원하는 플랫폼
-------------------

- Android
- BlackBerry WebWorks (OS 5.0 and higher)
- iOS


getMetadata
----------------

파일의 메타데이터를 찾아본다.

__Parameters:__

- __successCallback__ - 메타데이터 객체와 함께 호출되는 콜백.. _(Function)_
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

파일을 파일 시스템의 다른 위치에 이동한다. 다음을 수행하면 에러이다:

- 현재와 다른 이름으로 규정되지 않은 파일을 자신의 부모로 이동한다;
- 다른 디렉토리에 의해 사용되는 경로로 파일을 이동한다;

추가적으로, 파일을 기존의 파일로 이동하기 위한 시도는 반드시 그 파일을 지우고 교체한다.

__Parameters:__

- __parent__ - 파일을 이동하기 위한 부모 디렉토리. _(DirectoryEntry)_
- __newName__ - 파일의 새 이름. 명시되어 있지 않으면 현재 이름이 기본값이다. _(DOMString)_
- __successCallback__ - 새 파일의 FileEntry 객체와 함께 호출되는 콜백. _(Function)_
- __errorCallback__ - 파일을 이동하다가 에러가 발생하면 호출되는 콜백. FileError 객체와 함깨 발생한다. _(Function)_


__빠른 예제__

    function success(entry) {
        console.log("New Path: " + entry.fullPath);
    }

    function fail(error) {
        alert(error.code);
    }

    function moveFile(entry) {
        var parent = document.getElementById('parent').value,
            parentEntry = new DirectoryEntry({fullPath: parent});

        // 파일을 새 디렉토리로 이동하고 이름을 변경한다.
        entry.moveTo(parentEntry, "newFile.txt", success, fail);
    }
	

copyTo
------

파일을 파일 시스템상의 새 위치로 복사한다. 다음을 수행하면 에러이다:

- 현재와 다른 이름으로 규정되지 않은 파일을 자신의 부모로 복사한다.

__Parameters:__

- __parent__ - 파일을 복사하기 위한 부모 디렉토리. _(DirectoryEntry)_
- __newName__ - 파일의 새 이름. 명시되어 있지 않으면 현재 이름을 기본값으로 사용한다. _(DOMString)_
- __successCallback__ - 새 파일의 FileEntry 객체와 함께 호출되는 콜백. _(Function)_
- __errorCallback__ - 파일을 복사하다가 에러가 발생하면 호출되는 콜백. FileError 객체와 함께 발생한다. _(Function)_


__빠른 예제__

    function win(entry) {
	    console.log("New Path: " + entry.fullPath);
    }

    function fail(error) {
	    alert(error.code);
    }

    function copyFile(entry) {
        var parent = document.getElementById('parent').value,
            parentEntry = new DirectoryEntry({fullPath: parent});

        // 파일을 새 디렉토리로 복사하고 이름을 바꾼다.
        entry.copyTo(parentEntry, "file.copy", success, fail);
    }

	
toURI
-----

파일의 정확한 위치를 찾기 위해 사용되는 URI를 반환한다.

__빠른 예제__
	
    // 이 entry의 URI를 얻는다.
    var uri = entry.toURI();
    console.log(uri);


remove
------

파일을 제거한다. 

__Parameters:__

- __successCallback__ - 파일이 지워지고 난 뒤 호출되는 콜백. 아무 인자 없이 호출된다. _(Function)_
- __errorCallback__ - 파일을 제거하다가 에러가 발생하면 호출되는 콜백. FileError 객체와 함께 발생한다. _(Function)_

__빠른 예제__
	
    function success(entry) {
        console.log("Removal succeeded");
    }

    function fail(error) {
        alert('Error removing file: ' + error.code);
    }

    // remove the file
    entry.remove(success, fail);


getParent
---------

파일을 담고있는 부모 DirectoryEntry를 검색한다.

__Parameters:__

- __successCallback__ - 파일의 부모 DirectoryEntry와 함께 호출되는 콜백. _(Function)_
- __errorCallback__ - 부모 DirectoryEntry를 검색하다가 에러가 발생하면 호출되는 콜백. FileError 객체와 함께 발생한다. _(Function)_

__빠른 예제__
	
    function success(parent) {
        console.log("Parent Name: " + parent.name);
    }

    function fail(error) {
        alert(error.code);
    }

    // 부모 DirectoryEntry를 얻는다.
    entry.getParent(success, fail);	


createWriter
------------

FileEntry를 나타내는 파일과 관련된 FileWriter 객체를 생성한다.

__Parameters:__

- __successCallback__ - FileWriter 객체와 함께 호출되는 콜백. _(Function)_
- __errorCallback__ - FileWriter를 생성하기를 시도하는 중에 에러가 발생했을 경우 불리우는 콜백. FileError 객체를 발생한다. _(Function)_

__빠른 예제__
	
    function success(writer) {
        writer.write("Some text to the file");
    }

    function fail(error) {
        alert(error.code);
    }

    // 파일을 쓰기 위해 FileWriter를 생성한다.
    entry.createWriter(success, fail);	


file
----

해당 FileEntry가 가리키는 파일의 현재 상태를 나타내는 File 객체를 반환한다.

__Parameters:__

- __successCallback__ - File 객체와 함께 호출되는 콜백이다. _(Function)_
- __errorCallback__ - File 객체를 생성할 경우 에러가 발생하면 호출되는 콜백(예를 들면 실제 파일이 존재하지 않을 경우). FileError 객체를 발생한다. _(Function)_

__빠른 예제__
	
    function success(file) {
        console.log("File size: " + file.size);
    }

    function fail(error) {
        alert("Unable to retrieve file properties: " + error.code);
    }
 
    // 파일의 속성들을 얻는다.
    entry.file(success, fail);	
