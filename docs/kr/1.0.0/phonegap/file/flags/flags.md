Flags
=====

This object is used to supply arguments to the `DirectoryEntry` __getFile__ and __getDirectory__ methods, which look up or create files and directories, respectively.

Properties
----------

- __create:__ Used to indicate that the file or directory should be created, if it does not exist. If not set defaults to false. _(boolean)_ 
- __exclusive:__ By itself, exclusive has no effect. Used with create, it causes the file or directory creation to fail if the target path already exists. If not set defaults to false. _(boolean)_ 
지원하는 플랫폼
-------------------

- Android
- BlackBerry WebWorks (OS 5.0 and higher)
- iOS

빠른 예제
-------------

    // Get the data directory, creating it if it doesn't exist.
    dataDir = fileSystem.root.getDirectory("data", {create: true});

    // Create the lock file, if and only if it doesn't exist.
    lockFile = dataDir.getFile("lockfile.txt", {create: true, exclusive: true});
