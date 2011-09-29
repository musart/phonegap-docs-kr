contactSuccess
==============

'contacts.find' 동작의 결과인 'Contact' 배열을 제공하는 성공 콜백 함수.

    function(contacts) {
        // 무언가 한다.
    }

Parameters
----------

- __contacts:__ find 동작의 결과인 연락처 배열. (`Contact`)

Example
-------

    function contactSuccess(contacts) {
		for (var i=0; i<contacts.length; i++) {
			console.log("Display Name = " + contacts[i].displayName;
    }
