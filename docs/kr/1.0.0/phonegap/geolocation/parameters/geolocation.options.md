geolocationOptions
==================

geolocation 검색을 원하는 대로 설정하는 선택적인 변수들

    { maximumAge: 3000, timeout: 5000, enableHighAccuracy: true };

Options
-------

- __frequency:__ 얼마나 자주 1000분의 1초 단위로 위치를 검색하는지. 이 옵션은 W3C v표준의 일부가 아님으로 앞으로 삭제될 예정이다. maximumAge가 대신 사용되야 한다. _(Number)_ (Default: 10000)
- __enableHighAccuracy:__ 어플리케이션이 가장 가능성 있는 결과를 받고 싶다라는 힌트를 제공한다. _(Boolean)_
- __timeout:__ 적절한 `geolocationSuccess` 콜백이 호출될때 까지 `geolocation.getCurrentPosition`이나 `geolocation.watchPosition`의 호출이 허용되는 최대 시간(msec) 길이. _(Number)_
- __maximumAge:__ 1000분의 1초 단위의 명시된 시간보다 크지 않은 시간의 캐시된 위치를 받아 들인다. _(Number)_

Android Quirks
--------------

안드로이드 2.x 애뮬레이터는 enableHighAccuracy 옵션을 true로 하지 않으면 geolocatoin 결과를 반환하지 않는다.

    { enableHighAccuracy: true }

