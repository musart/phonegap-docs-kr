cameraSuccess
=============

이미지 데이터를 제공하는 onSuccess 콜백 함수.

    function(imageData) {
        // 이미지를 가지고 어떤것을 해라.
    }

Parameters
----------

- __imageData:__ `cameraOptions`에 따른 이미지 데이터의 Base64 인코딩 값이나 이미지 파일의 URL. (`String`)

Example
-------

    // 이미지를 보여준다.
    //
    function cameraCallback(imageData) {
        var image = document.getElementById('myImage');
        image.src = "data:image/jpeg;base64," + imageData;
    }
