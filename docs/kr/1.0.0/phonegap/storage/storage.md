Storage
==========

> 기기의 storage options 접근을 제공한다.

이 API는 [W3C Web SQL Database Specification](http://dev.w3.org/html5/webdatabase/) 와 [W3C Web Storage API Specification](http://dev.w3.org/html5/webstorage/)에 기반한다. 일부 기기들은 이미 이 사양의 구현을 제공한다. 이 기기들에서는 PhoneGap의 구현으로 변경하지 않고 빌트인된 기능을 사용한다. storage 기능을 갖지 않은 기기를 위해 PhoneGap의 구현은 W3C 사양에 호환이 될 것이다.

Methods
-------

- openDatabase

Arguments
---------

- name
- version
- display_name
- size

Objects
-------

- Database
- SQLTransaction
- SQLResultSet
- SQLResultSetList
- SQLError
- localStorage
