device.uuid
===========

기기의 Universally Unique Identifier ([UUID](http://en.wikipedia.org/wiki/Universally_Unique_Identifier)) 를 반환한다.

    var string = device.uuid;
    
설명
-----------

어떻게 UUID가 기기 제조사에 의해 생성되고 결정되는지를 그리고 기기의 플랫폼이나 모델에 특유해지는 세부사항
The details of how a UUID is generated are determined by the device manufacturer and specific to the device's platform or model.

지원하는 플랫폼
-------------------

- Android
- BlackBerry
- BlackBerry WebWorks (OS 5.0 and higher)
- iPhone

빠른 예제
-------------

    // Android: 64-bit의 무작위의 정수를 반환한다. (문자열로 반환한다.)
    //          기기가 처음 부팅할때 생성되는 숫자이다.
    //
    // BlackBerry: 기기의 PIN 번호를 반환한다.
    //             9자리 유일한 숫자이다. (문자열로 반환한다.)
    //
    // iPhone: (UIDevice Class documentation로 바꾸어 표현된다.)
    //         여러개의 하드웨어 식별자로부터 생성된 문자열의 해쉬값을 반환한다.
    //         이것은 모든 기기에서 유일하도록 보장되고 사용자 계정에 결부되지 않는다.
    //
    var deviceID = device.uuid;

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
