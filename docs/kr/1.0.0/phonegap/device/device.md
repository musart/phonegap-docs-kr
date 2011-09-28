Device
======

> 기기의 하드웨어와 소프트웨어를 묘사하는 `device` 객체.

Properties
----------

- device.name
- device.phonegap
- device.platform
- device.uuid
- device.version

Variable Scope
--------------

'device'가 'window' 객체에 할당된 이후, 그것은 전역 범위안에 내제된다.

    // 이것은 같은 'device'를 참조한다.
    //
    var phoneName = window.device.name;
    var phoneName = device.name;
