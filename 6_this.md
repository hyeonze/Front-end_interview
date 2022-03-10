# This

this의 값은 함수의 호출방법에 의해 결정 됨. 한 마디로 this === 실행한 놈. 호출한 객체.
(클로저는 반대로 선언할 때 결정됨. 호출방법과 별도로 this를 지정하려면 bind 메서드를 사용.)

var someone = {
    name : 'codejong',
    whoAmI : function () {
    console.log(this);
  }
};

someone.whoAmI(); // { name : 'codejong', whoAmI : function } 출력, .앞 포함 호출한 부분에 집중

var myWhoAmI = someone.whoAmI

myWhoAmI(); // Window 객체 출력, 호출 부분에 집중

var btn = document.getElementById('btn');

btn.addEventListener('click', someone.whoAmI); // HTML요소 출력, 호출 부분에 집중, 콜백은 호출한게 아니라 인자로 넘겨준 것

var binedeWhoAmI = myWhoAmI.bind(someone); // someone을 this로 할 것 이라는 뜻

btn.addEventListener('click', binedeWhoAmI); // { name : 'codejong', whoAmI : function } 출력
binedeWhoAmI(); // { name : 'codejong', whoAmI : function } 출력
