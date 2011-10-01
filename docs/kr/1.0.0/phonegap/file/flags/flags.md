Flags
=====

이 객체는, 각각 파일이나 디렉토리들을 검색하거나 생성할 경우, 'DirectoryEntry'의 __getFile__과 __getDirectory__ 함수의 아규먼트를 지원하기 위해 사용된다. 

Properties
----------

- __create:__ 파일이나 디렉토리가 존재하지 않는 경우, 반드시 생성되어야 함을 나타내기 위해 사용된다. 설정되어 있지 않으면 기본값으로 false를 설정한다. _(boolean)_ 
- __exclusive:__ exclusive 그 자체로는 아무런 효과가 없다. create와 사용되는데, target 경로가 이미 존재하면 파일이나 디렉토리 생성에 실패를 초래한다.

지원하는 플랫폼
-------------------

- Android
- BlackBerry WebWorks (OS 5.0 and higher)
- iOS

빠른 예제
-------------

    // data 디렉토리를 얻고, 존재하지 않으면 생성한다.
    dataDir = fileSystem.root.getDirectory("data", {create: true});

    // lockfile을 생성하고, 존재하지 않으면 생성한다.
    lockFile = dataDir.getFile("lockfile.txt", {create: true, exclusive: true});
