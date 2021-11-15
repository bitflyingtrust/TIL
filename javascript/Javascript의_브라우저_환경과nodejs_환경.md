# Javascript의 브라우저 환경과 nodejs 환경

다음 질문입니다. 아래의 예제에서 console.log(person.last-name)의 실행 결과는 Node.js 환경에서는 "ReferenceError: name is not defined"이고 브라우저환경에서는 NaN이다. 
그 이유는 무엇입니까?

var person = {
	'last-name' : 'hungry',
	first_name : 'always'
}

console.log(person.last-name) // 브라우저 환경 : NaN
							  // Node.js 환경 : ReferenceError: name is not defined

person.last를 실행할때 자바스크립트 엔진은 먼저 person.last를 평가해서 person객체의 프로퍼티 키에 last가 존재하지 않기때문에 undefined로 평가됩니다. 
다음으로 엔진은 person.last - name을 undefined - name 로 평가해서 name의 식별자를 찾는데 이때 브라우는저는 암욱적으로 name이라는 전역변수(window의 프로퍼티)로 인식하고
초기값으로 빈문자열인 '' 로 인식하기때문에 다음으로 undefined - '' 변환되어 최종적으로 NaN으로 평가하고 콘솔에 출력하게 됩니다. 반면 Node.js에서는 name이라는 식별자가
존재하지 않게 때문에 "ReferenceError: name is not defined"를 출력합니다.

여기서 생각할 점은 Node.Js 환경과 브라우저 환경은 100% 일치 하지 않는다는 것입니다. 개발을 할때 어떤 환경에서 프로그램이 동작하는 염두하면서 각 환경의 특징을 살펴볼 필요가 있습니다.


