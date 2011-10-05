Metadata
==========

이 인터페이스는 파일이나 디렉토리의 상태에 대한 정보를 채운다.

Properties
----------

- __modificationTime:__ 이것은 파일이나 디레고리가 마지막으로 수정된 시간값이다. _(Date)_

Details
-------

`Metadata` 객체는 파일이나 디렉토리의 상태에 대한 정보를 나타낸다. 당신은 `DirectoryEntry`나 `FileEntry` 객체의 __getMetadata__ 함수를 호출함으로써 Metadata 객체의 인스턴스를 얻는다. 

지원하는 플랫폼
-------------------

- Android
- BlackBerry WebWorks (OS 5.0 and higher)
- iOS

빠른 예제
-------------

	function win(metadata) {
		console.log("Last Modified: " + metadata.modificationTime);
	}
	
	// 이 엔트리의 metadata 객체를 요청한다.
	entry.getMetadata(win, null);
