# 강재혁 [201840102]
## [04월 03일]
>생성자 :객체를 만드는 함수 대문자 시작<br>
>스크립트는 변수 선언이 let으로 자료형이 무엇인지 상관없이 쓰기때문에 type of 함수를 많이씀<br>
>그리고 자료형에 function가능<Br>
>MAX_VALUE에 10000을 더한겂을해도 오류는 나지 않지만 MAX_VALUE값이 그대로 나옴<br> 
>객체안에 배열이랑 함수 다 넣을 수 있음
## [04월 25일]
>오늘 배운 내용 요약 <br/>
>배열은 요소에 접근할 때 인덱스를 사용하고, 객체는 키를 사용함<br>
>this함수 생성자 함수 객체를 만드는 함수, 대문자로 시작하는 이름 사용<br>
>생성자 함수로 만든 객체는 프로토타입 공간에 메소드를 지정해서 모든
객체가 공유 하도록 함, 해당 함수를 생성자 함수로 사용했을 때만 의미가 있음<br>
>객생성방법 let product = new Product("x","y");
>
## [04월 13일]
>오늘 배운 내용 요약 <br/>
>무명함수<br/>
>let foo = function(){  <br/>
>    console.log("첫줄");<br/>
>    console.log("둘째줄");<br/>
>}
>let foo = () => {<br/>
>    console.log("첫줄");<br/>
>    console.log("둘째줄");<br/>
>function foo (){<br/>
>    console.log("첫줄");<br/>
>    console.log("둘째줄");<br/>
>}<br/>
>foo();<br/>
>console.log(foo);<br/>
>표준 내장함수<br/>
>parseInt(): 문자열을 정수로 변환하는 함수<br/>

>parseFloat(): 문자열을 실수로 변환하는 함수<br/>
>let inputA = "52";<br/>
>let inputB = "52.273";<br/>
>let inputC = "1401동";<br/>
>console.log("정수형 전환")<br/>
>console.log(parseInt(inputA));<br/>
>console.log(parseInt(inputB));<br/>
>console.log(parseInt(inputC));<br/>
>console.log("실수형 전환")<br/>
>console.log(parseFloat(inputA));<br/>
>console.log(parseFloat(inputB));<br/>
>console.log(parseFloat(inputC));<br/>
>console.log("숫자만 출력");<br/>
>console.log(Number(inputA));<br/>
>console.log(Number(inputB));<br/>
>console.log(Number(inputC));<br/>


>표준 내장 함수<br/>
>- 자바스크립트에서 기본적으로 지원하는 함수<br/>
>- 콜백 함수<br/>
>- 함수의 매개 변수로 전달되는 함수<br/>

## [04월 06일]
>오늘 배운 내용 요약 <br/>
>**배열**<br/>
>let array = [1, 2, 3, 4, 5, 6]; 이런식으로 선언 "배열은 0부터 시작*<br/>
>console.log(array[0]); 0번쨰 배열에 있는 값 출력 <br/> 
>array.length 배열의 길이 <br/>
>console.log(`$(i) 번쨰 요소: $[
>**push**는 배열의 끝에 원하는 값을 추가해주는 함수  **foo.push(1,2,3);**<br/>
**pop**은 배열의 마지막 주소에 있는 값을 제거해주는 함수. **foo.pop();**<br/>
**shift**는 배열의 첫번째 주소에 있는 값을 제거한 후에 반환해주는 함수**.foo.shift():**<br/>



## [03월 30일]
>오늘 배운 내용 요약 <br/>
>요약 if (조건){<br/>
>조건이 참일떄 실행하는 문장}<br/>
>else {조건 여집합일떄 실행하는문장}              ---> 2중 if 가능<br/>
>switch(조건문){<br/>
>case 비교할값<br/>
>비교해서 같으면 실행되는 문장<br/>
>break;<br/>
>case 비교할값<br/>
>비교해서 같으면 실행되는 문장<br/>
>break;<br/>
>default<br/>
>switch에 없는 값 입력시 실행되는 문장<br/>
>break;<br/>
>삼항연산자<br/>
><표현식>?<참>:<거짓><br/>
>A || B에서 A가 참이라면 A로 대치 / A || B에서 B가 참이라면 B로 대치<br/>
>prompt: Scanner 같은함수<br/>
>eval 함수 - 입력값을 받고 저장하는 함수 / callback함수 - 무한반복 시키는 함수<br/>






## [03월 23일]

>오늘 배운 내용 요약 <br/>
>요약  % 나머지 연산자<br/>
> 문자열 생성시 큰따옴표나 작음따옴표 사용<br/>
>  같다(==) 대입해라(=)<br/>
 또는(||), 그리고(&&)v
 a+= 10 은 a= a+10 이랑같음 <br/>
 변수가 10이고변수++이면 화면에 10로 나오고 ++변수 이면 11로나옴<br/>
 

## [3월 16일]
>오늘 배운 내용 요약 <br/>
>요약  출력 코드 console.log('hi') , alret('hi')<br>
줄바꿈(\n)<br>
주석: //<br>
라인별 주석, (/*~~~~~~~~~~~~~~~~ * /)<br>



