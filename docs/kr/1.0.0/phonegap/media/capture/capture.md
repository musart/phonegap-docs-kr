Capture
=======

> 기기의 오디오, 이미지, 비디오 캡처 기능으로의 접근을 제공한다.

Objects
-------

- Capture
- CaptureAudioOptions
- CaptureImageOptions
- CaptureVideoOptions
- CaptureCB
- CaptureErrorCB
- ConfigurationData
- MediaFile
- MediaFileData

Methods
-------

- capture.captureAudio
- capture.captureImage
- capture.captureVideo
- MediaFile.getFormatData

Scope
-----

__capture__ 객체는 __navigator.device__ 객체에 의해 할당되고, 따라서 전역 범위이다.

    // 전역 capture 객체
    var capture = navigator.device.capture;

Properties
----------

- __supportedAudioModes:__ 기기에 의해 지원되는 포멧으로 기록되는 오디오. (ConfigurationData[])
- __supportedImageModes:__ 기록된 이미지 크기와 기기에 의해 지원되는 포멧. (ConfigurationData[])
- __supportedVideoModes:__ 기록된 비디오 해상도와 기기에 의해 지원되는 포멧. (ConfigurationData[])

Methods
-------

- capture.captureAudio: 오디오 클립(들)을 기록하기 위해 기기의 오디오 녹음 어플리케이션을 구동한다.
- capture.captureImage: 이미지(들)을 얻기 위해 기기의 카메라 어플리케이션을 구동한다.
- capture.captureVideo: 비디오(들)을 녹음하기 위해 기기의 비디오 레코더를 구동한다.


지원하는 플랫폼
-------------------

- Android
- BlackBerry WebWorks (OS 5.0 and higher)
- iOS
