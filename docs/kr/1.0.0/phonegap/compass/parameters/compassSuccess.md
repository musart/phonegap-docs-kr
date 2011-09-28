compassSuccess
==============

나침반의 가리는 방향을 제공하는 onSuccess 콜백 함수

    function(heading) {
        // Do something
    }

Parameters
----------

- __heading:__ 한 순간 0 - 359.99 각도의 가리키는 방향 _(Number)_

Example
-------

    function onSuccess(heading) {
        alert('Heading: ' + heading);
    };
