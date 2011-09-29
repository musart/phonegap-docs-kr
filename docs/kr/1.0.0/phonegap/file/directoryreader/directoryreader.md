DirectoryReader
===============

디렉토리내에 파일과 디렉토리들을 열거하는 객체이다. [Directories and Systems](http://www.w3.org/TR/file-system-api/) 표준에 정의되어 있다.

Methods
-------

- __readEntries__: 디렉토리안에 엔트리들을 읽는다.

지원하는 플랫폼
-------------------

- Android
- BlackBerry WebWorks (OS 5.0 and higher)
- iOS

readEntries
-----------

디렉토리안에 엔트리들을 읽는다.

__Parameters:__

- __successCallback__ - FileEntry와 DirectoryEntry 객체들의 배열을 전달하는 콜백. _(Function)_
- __errorCallback__ - 만약 디렉토리를 열거하다가 에러가 발생하면 호출되는 콜백. FileError 객체와 함께 발생한다. _(Function)_

__빠른 예제__
	
    function success(entries) {
        var i;
        for (i=0; i<entries.length; i++) {
            console.log(entries[i].name);
        }
    }

    function fail(error) {
        alert("Failed to list directory contents: " + error.code);
    }

    // directory reader 를 얻는다.
    var directoryReader = dirEntry.createReader();

    // 디렉토리 안에 모든 엔트리들의 리스트를 얻는다.
    directoryReader.readEntries(success,fail);
