contactFindOptions
==================

`contacts.find`함수의 선택적인 변수. 이 변수를 연락처 저장소로부터 반환되는 contacts를 거르기 위해 사용한다.

    { 
		filter: "",
		multiple: true,
	};

Options
-------

- __filter:__ 연락처를 거르기 위한 검색 문자열. _(DOMString)_ (기본값: "")
- __multiple:__ find 동작이 여러개의 연락처를 반환하는지를 결정한다. _(Boolean)_ (기본값: false)

