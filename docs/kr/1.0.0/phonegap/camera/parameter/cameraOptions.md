cameraOptions
=============

카메라 설정값을 사용자 설정 가능한 선택적인 파라미터

    { quality : 75, 
      destinationType : Camera.DestinationType.DATA_URL, 
      sourceType : Camera.PictureSourceType.CAMERA, 
      allowEdit : true,
      encodingType: Camera.EncodingType.JPEG,
      targetWidth: 100,
      targetHeight: 100 };

Options
-------

- __quality:__ 저장된 이미지의 품질.  범위는 [0, 100]. (`Number`)

- __destinationType:__ 리턴값의 포멧을 선택한다.  navigator.camera.DestinationType에 정의되어 있다. (`Number`)
        
            Camera.DestinationType = {
                DATA_URL : 0,                // base64로 인코딩된 문자열기반의 이미지가 반환된다.
                FILE_URI : 1                 // 파일의 URI가 반환된다.
            };

- __sourceType:__ 사진의 근원을 설정한다.  nagivator.camera.PictureSourceType에 정의되어 있다. (`Number`)
     
        Camera.PictureSourceType = {
            PHOTOLIBRARY : 0,
            CAMERA : 1,
            SAVEDPHOTOALBUM : 2
        };

- __allowEdit:__ 선택하기 전에 이미지의 간단한 수정을 허락한다. (`Boolean`)
  
- __EncodingType:__ 반환되는 이미지 파일의 인코딩 타입을 선택한다.  navigator.camera.EncodingType에 정의되어 있다. (`Number`)
        
            Camera.EncodingType = {
                JPEG : 0,               // JPEG로 인코딩된 이미지가 반환
                PNG : 1                 // PNG로 인코딩된 이미지가 반환
            };

- __targetWidth:__ 이미지 크기를 변경하기 위한 픽셀단위의 넓이.  targetHeight와 꼭 함께 사용되어야 한다.  가로세로비는 유지된다. (`Number`)
- __targetHeight:__ 이미지 크기를 변경하기 위한 픽셀단위의 높이.  targetWidth와 꼭 함께 사용되어야 한다. 가로세로비는 유지된다. (`Number`)
  
Android Quirks
--------------

- `allowEdit` 변수는 무시한다.
- Camera.PictureSourceType.PHOTOLIBRARY 와 Camera.PictureSourceType.SAVEDPHOTOALBUM 둘 다 같은 포토앨범을 보여준다.
- Camera.EncodingType 은 지원하지 않는다.

BlackBerry Quirks
-----------------

- `quality` 변수를 무시한다.
- `sourceType` 변수를 무시한다.
- `allowEdit` 변수를 무시한다.
- 어플리케이션은 사진을 찍은 후에 네이티브 카메라 어플리케이션을 닫기 위해 반드시 key injection permissions을 가져야 한다.
- 큰 이미지를 사용하는 것은 고해상도 카메라를 가진 최신 기기에서 이미지를 인코드할 때 불가능한 결과를 얻을 수 있다. (예를 들면 Torch 9800)

Palm Quirks
-----------

- `quality` 변수를 무시한다.
- `sourceType` 변수를 무시한다.
- `allowEdit` 변수를 무시한다.

iPhone Quirks
--------------

- 일부 기기에서 메모리 에러를 피하기 위해 50 이하로 'quality'를 설정한다.
- 'destinationType.FILE_URI'가 사용될 때, 사진은 어플리케이션의 임시 디렉토리에 저장된다.
- 어플리케이션의 임시 디렉토리의 컨텐츠는 어플리케이션이 종료될 때 삭제된다. 개발자는 저장공간에 대해 우려가 될 경우 navigator.fileMgr API를 사용해서 이 디렉토리의 컨텐츠를 지운다.

           
