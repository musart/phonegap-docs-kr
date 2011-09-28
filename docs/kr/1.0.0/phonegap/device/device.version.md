device.version
==============

운영 시스템의 버전을 얻는다.

    var string = device.version;

지원하는 플랫폼
-------------------

- Android 2.1+
- BlackBerry
- BlackBerry WebWorks (OS 5.0 and higher)
- iPhone

빠른 예제
-------------

    // Android:    Froyo OS 는 "2.2"를 반환한다.
    //             Eclair OS 는 "2.1", "2.0.1", or "2.0"를 반환한다.
    //             버전은 또한 "2.1-update1"와 같은 업데이트 레벨을 리턴할 수 있다.  
    //
    // BlackBerry: OS 4.6을 사용하는 Bold 9000 는 "4.6.0.282"를 반환한다.
    //
    // iPhone:     iOS 3.2 는 "3.2"를 반환한다.
    //
    var deviceVersion = device.version;

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
