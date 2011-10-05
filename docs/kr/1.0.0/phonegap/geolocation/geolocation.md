Geolocation
===========

> `geolocation`객체는 기기의 GPS 센서에 접근을 제공한다.

Geolocation은 위도나 경도같은 기기의 위치 정보를 제공한다. 위치 정보의 일반적인 소스는 Global Positioning System (GPS) 와 IP 주소, RFID, WiFi와 블루투스 MAC 주소 그리고 GSM/CDMA 망 ID와 같은 네트워크 신호로 추측하는 위치를 포함한다. API가 기기의 실제 위치를 반환하는 것에 대해 보장 되지 않는다. 

이 API는 [W3C Geo location API Specification](http://dev.w3.org/geo/api/spec-source.html)에 기반한다.  일부 기기들은 이 표준에 대한 구현이 이미 되어있다. 이러한 기기들을 위해, PhoneGap의 구현으로 교체하는 대신에 빌트-인된 기능을 사용한다. geolocation 기능을 가지지 않은 기기들을 위해, PhoneGap의 구현은 반드시 W3C 표준에 호환된다.

Methods
-------

- geolocation.getCurrentPosition
- geolocation.watchPosition
- geolocation.clearWatch


Arguments
---------

- geolocationSuccess
- geolocationError
- geolocationOptions

Objects (읽기 전용)
-------------------

- Position
- PositionError
- Coordinates
