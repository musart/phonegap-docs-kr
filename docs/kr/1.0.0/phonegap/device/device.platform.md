device.platform
===============

기기의 운영 시스템 이름을 반환한다.

    var string = device.platform;

지원하는 플랫폼
-------------------

- Android
- BlackBerry
- BlackBerry WebWorks (OS 5.0 and higher)
- iPhone

빠른 예제
-------------

    // 기기에 따라 몇개의 예제는 다음과 같다.
    //   - "Android"
    //   - "BlackBerry"
    //   - "iPhone"
    //   - "webOS"
    //
    var devicePlatform = device.platform;

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
    
iPhone Quirks
-------------

모든 기기는 플랫폼으로써 `iPhone`을 반환한다. 이 부정확함은 애플이 iPhone 운영체제를 `iOS`로 새로 바꿔서이다.

BlackBerry Quirks
-----------------

기기들은 플랫폼 이름 대신 기기 플랫폼 버전을 반환한다. 예를 들면 Storm2 9550은 '2.13.0.95'나 유사하게 반환한다.
