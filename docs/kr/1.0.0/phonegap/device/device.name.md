device.name
===========

기기의 모델 이름을 얻는다.

    var string = device.name;
    
설명
-----------

`device.name` 은 기기의 모델과 제품의 이름을 반환한다. 이 값은 기기의 제조사에 의해 설정되고, 같은 제품의 다른 버전일 수도 있다.

지원하는 플랫폼
-------------------

- Android
- BlackBerry
- BlackBerry WebWorks (OS 5.0 and higher)
- iPhone

빠른 예제
-------------

    // Android:    Nexus One       returns "Passion" (Nexus One code name)
    //             Motorola Droid  returns "voles"
    // BlackBerry: Bold 8900       returns "8900"
    // iPhone:     All devices     returns a name set by iTunes e.g. "Joe's iPhone"
    //
    var name = device.name;

전체 예제
------------

    <!DOCTYPE html>
    <html>
      <head>
        <title>Device Properties Example</title>

        <script type="text/javascript" charset="utf-8" src="phonegap.js"></script>
        <script type="text/javascript" charset="utf-8">

        // PhoneGap이 로드되기를 기다린다
        //
        document.addEventListener("deviceready", onDeviceReady, false);

        // PhoneGap이 준비되면 호출된다
        //
        function onDeviceReady() {
            var element = document.getElementById('deviceProperties');
    
            element.innerHTML = 'Device Name: '     + device.name     + '<br />' + 
                                'Device PhoneGap: ' + device.phonegap + '<br />' + 
                                'Device Platform: ' + device.platform + '<br />' + 
                                'Device UUID: '     + device.uuid     + '<br />' + 
                                'Device Version: '  + device.version  + '<br />';
        }

        </script>
      </head>
      <body>
        <p id="deviceProperties">Loading device properties...</p>
      </body>
    </html>


Android Quirks
--------------

- [model name](http://developer.android.com/reference/android/os/Build.html#MODEL) 대신에 [product name](http://developer.android.com/reference/android/os/Build.html#PRODUCT) 을 얻는다.
    - 제품 이름은 종종 개발 기간의 코드명일 수 있다.
    - e.g. Nexus One 은 "Passion"을 반환하고, Motorola Droid 는 "voles"를 반환한다.

iPhone Quirks
-------------

- [device model name](http://developer.apple.com/iphone/library/documentation/uikit/reference/UIDevice_Class/Reference/UIDevice.html#//apple_ref/doc/uid/TP40006902-CH3-SW1) 대신에 [device's custom name](http://developer.apple.com/iphone/library/documentation/uikit/reference/UIDevice_Class/Reference/UIDevice.html#//apple_ref/doc/uid/TP40006902-CH3-SW13) 을 얻는다.
    - custom name 은 아이튠스의 소유자에 의해 설정된다.
    - e.g. "Joe's iPhone"
