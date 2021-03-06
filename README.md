# 강재혁 [201840102]
## [6월 1일]
### 웹 브라우저에서 사용 할 수 있는 자바스크립트 범위

let, const  키워드르 사용 하지 못함 var을 써야됨

화살표함수

for of 반복문

### Window 객체

alrert(메세지)  경고창을 띄어줌

prompt(메세지,<임시글자>) 프롬프트를 출력

### location  메소드

assign(<링크>) 매개변수로 전달한 위치로 이동

reload() 새로 고침

replace() 매개변수로 전달한 위치로 이동  ※뒤로가기는 못함

### history 메소드

forward()  앞으로 이동

back() 뒤로 이동

### 문서 객체

html 태그를 자바 스크립트에서 사용할 수 있는 객체로 만듦

### 정적으로 문서 객체를 생성한다

HTML 페이제에 있는 태그들을 읽으면서 생성하는것

### 동적으로 문서 객체를 생성한다

자바스크립트를 사용하여 프로그램 실행 중에 문서 객체를 생성하는것

### 문서 객체 선택

document.getElementByid(아이디) 아이디를 사용해 문서 객체를 선택

document.querySelector(선택자) 선택자를 사용해 문서 객체를 선택  ※ 첫태그만 선택됨

### 문서 객체 조작

innerHTML

```jsx
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">

  <title>Dom Basic</title>
  <script>
    window.onload = function(){
      var headers = document.querySelectorAll('h1');
      for (var i = 0; i<headers.length; i++){
        var header = new headers[i];
        header.style.color = 'orange';
        header.style.background = 'red';
        header.innerHTML = 'From JavaScript';
      }
    };
  </script>
</head>
<body>
<h1>Header</h1>
<h1>Header</h1>
<h1>Header</h1>
  
</body>
</html>
```

이렇게하면 다 적용이됨

### 속성 조작

img.src ='ring.png'

alert(img.src)
## [05월 25일]
# express

### express 모듈설치

- npm install express@4

### express 기본  모듈

express(): 서버 애플리케이션 객체를 생성합니다

app.use(): 요청이 왔을 떄 실행할 함수를 지정합니다

app.listen(): 서버를 실행합니다

### express 예제

```jsx
//모듈 추출
const express = require('express');
//서버 생성
const app = express();
//request 이벤트 리스너 설정
app.use((request,response)=>{
  response.send('<h1> Hello expresss</h1>');
});
//  서버를 실행
app.listen(52273,()=>{
  console.log(('server running at http://127.0.0.1:52273'));
})
```

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/e3cbcbdd-9245-4741-b104-b81116962960/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/e3cbcbdd-9245-4741-b104-b81116962960/Untitled.png)

### 페이지 라우팅

클라이언트 요청에 적절한 페이지를 제공하는 기술

get(path,callback)      GET요청이 발생했을때 

post(path,callback)     POST요청이 발생했을때 

put(path,callback)       PUT요청이 발생했을때 

delete(path,callback)  DELETE요청이 발생했을때 

all(path,callback)        모든요청이 발생했을때 

```jsx
//모듈 추출
const express = require('express');
//서버 생성
const app = express();
//request 이벤트 리스너를 설정
app.get('/page/:id',(request,response)=>{
  //토큰을 꺼냅니다
  const id = request.params.id;
  //응답
  response.send(`<h1>${id} Page</h1>`)
});

// 서버실행
app.listen(52273,()=>{
  console.log(('server running at http://127.0.0.1:52273'));
});
```

### ‘[http://127.0.0.1:52273/page/](http://127.0.0.1:52273/page/273)(여기 값을 get 방식으로 받아와서 보여줌)
response 객체

send()  데이터 본문을 제공

status() 상태 코드를 제공합

set() 헤더를 설정합니다  ※메소드는 가장 마지막에 실행해야함, 두 번 실행 불가능

```jsx
//모듈 추출
const { response } = require('express');
const express = require('express');
//서버 생성
const app = express();
//request 이벤트 리스너를 설정
app.get('*',(request,response)=>{
  response.status(404);
  response.set('methodA','ABCDE');
  response.set({
    'methodB1':'FGHIJ',
    'methodB2':'KLMNO',
    
  })
  response.send('내 마음대로 본문을 입력합니다');
}
)

// 서버실행
app.listen(52273,()=>{
  console.log(('server running at http://127.0.0.1:52273'));
});
```

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/f7fecc64-38a0-4b5a-af48-b950a294c982/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/f7fecc64-38a0-4b5a-af48-b950a294c982/Untitled.png)

### type()매소드

MIME 형식을 지정  ex)type(text/html) :html데이터를의미

### status()매소드

상태코드를 지정

1xx처리중

2xx성공

3xx리다이렉트     redirect() 화면을 출력하지 않고 응답 헤더에 있는 로케이션 속성을 확인해서 해당위치로이동 , 특정 경로로 웹브라우저를 인도 할떄 사용

4xx클라이언트오류

5xx서버오류

### 요청 매개 변수 추출

```jsx
//모듈 추출
const { response } = require('express');
const express = require('express');
//서버 생성
const app = express();
//request 이벤트 리스너를 설정
app.get('*',(request,response)=>{
  console.log(request.query);
  response.send(request.query)
})

// 서버실행
app.listen(52273,()=>{
  console.log(('server running at http://127.0.0.1:52273'));
});
```

‘[http://127.0.0.1:52273/?a=10&b=20](http://127.0.0.1:52273/?a=10&b=20) 입력하면

{'a',:'10', 'b':'20'}나옴

쿼리문자열:변수=값 형태로구성 여러쌍의ㅡ 변수와 값을 전달할경우 & 구분

### 미들웨어

정적 파일(이미지,음악,자바스크립트 파일,스타일시트파일) 제공

### morgan  미들웨어 설치

npm install morgan

```jsx
const express = require('express');
const morgan = require('morgan');
const app = express();

app.use(morgan('combined'));

app.get('*', (req, res)=> {
res.send('Check CMD');
});

app.listen(52273, ()=> {
  console.log('Server is Running at http://localhost:52273');
})
```

### body-parser 미들웨어

 npm install body-parser

params 객체: URL의 토큰 보기가 간편

query 객체 :URL의 요청 매개변수 ㅌ큰보다 많은데이터를 전달 주소로 어떤데이터가 오고가는지확인가능

body 객체:ㅣ 대용량 문자열 등을 전송할 떄 사용 주소에 데이터를 기록못하므로 새로고침이나 즐겨찾기 기능 등을 활용할수없음

## [05월 18일]
### 전역변수

__ filename 현재 실행중인 코드의 파일 경로를 나타냅니다

__dirname 현재 실행중인 코드의 폴더경로를 나타냅니다

### process 객체의 속성

※ Node.js는 process 전역 객체를 제공

※ process 객체는 프로세스 정보를 제공하며, 제어할 수 있게 하는 객체

- env:  컴퓨터 환경 정보를 나타냅니다
- version:  Node.js  버전을 나타냅니다
- versions: Node.js와 중속된 프로그램 버전을 나타냅니다
- arch: 프로세서의 아키텍처를 나타냅니다
- platform: 플랫폼을 나타냅니다

### process 객체의 매소드

- exit: 프로그램을 종료합니다
- memoryUsage(): 메모리 사용 정보 객체를 리턴합니다
- uptime(): 현재 프로그램이 실행된 시간을 리턴합니다.

### 파일 읽기

- fs.readFileSync(<파일 이름>)  —————>동기적으로 파일을 읽어 들입니다
- fs.readFile(<파일이름>),<콜백 함수>) ————————>비동기적으로  파일 읽어드림

### 동기적 파일 읽기

```jsx
/*모듈 추출 */
const fs require('fs');
/*파일 읽어들이고 출력*/
const file = fs.readFileSync('textfile.txt');
console.log(file);
console.log(file.toString());
```

### 비동기적 파일 읽기

```jsx
//모듈 추출
const fs require('fs');
//파일 읽어들임
fs.readFile('textfile.txt',(error,file))=>{
//출력
console.log(file);
console.log(file.toString());
});
```

### 차이점

- 동기적은 *모듈을 만듦→파일을 읽어들이고 출력→ 프로그램 끝* 반면
- 비동기적은 *모듈을 만듦→프로그램 끝→ 파일을 읽어들이고 출력*
- 동기적은 읽고출력을하고 프로그램끝을낼떄 파일크기가 크면 코드가 정지
- 비동기적은 그딴거 없음
- 비동기적 처리는 프로그래밍 언어 자체는 느리지만 큰 의미는 없어  개발 속도와 유지 보수성이 좋은 프로그래밍 언어를 사용

### process 객체의 이벤트

- exit : 프로세스 종료
- uncaughtException  예외가 일어날  떄 발생

```jsx
process.on('exit',()=>{
  console.log('프로세스가 종료되었습니다');
});

process.on('uncaughtException',()=>{
  console.log('예외가 발생되었습니다');
});
//오류발생
error.error.error();
```

Node.js가 제공하는 객체의 이벤트 : [https://nodejs.org/en/docs/](https://nodejs.org/en/docs/) 

• process 객체 : [https://nodejs.org/dist/latest-v6.x/docs/api/process.html](https://nodejs.org/dist/latest-v6.x/docs/api/process.html)

※ os 모듈의 메소드

- hostname() : 운영체제의 호스트 이름을 리턴
- type() : 운영체제의 이름을 리턴
- platform() : 운영체제의 플랫폼을 리턴
- arch() : 운영체제의 아키텍처를 리턴
- release() : 운영체제의 버전을 리턴
- uptime() : 운영체제가 실행된 시간을 리턴
- loadavg() : 로드 에버리지 정보를 담은 배열을 리턴
- totalmem() : 시스템의 총 메모리를 리턴
- freemem() : 시스템의 사용 가능한 메모리를 리턴
- cpus() : CPU의 정보를 담은 객체를 리턴
- getNetworkInterfaces() : 네트워크 인터페이스의 정보를 담은 배열을 리턴

※ Url 모듈의 메소드

- parse(urlStr [, ParseQueryString = false, slashesDenoteHost = false]) : URL 문자열을 URL 객체로 변환하여 리턴
- format(urlObj) : URL 객체를 URL 문자열로 변환하여 리턴
- resolve(from,to) : 매게 변수를 조합하여 완전한 URL 문자열을 생성해 리턴

※ File System 모듈
파일읽기

- 실행할 자바스크립트 파일이 있는 폴더에 textfile.txt 이름의 파일을 생성하고
- fs.readFileSync(<파일 이름>) : 동기적으로 파일을 읽음
- fs.readFile(<파일 이름>,<콜백 함수>) : 비동기적으로 파일을 읽음

 비동기 처리의 장점
• 웹 서버를 C++ 프로그래밍 언어로 만들면 무척 빠르지만, 개발과 유지 보수는
어려움
• 전 세계 웹 서비스 기업(페이스북, 트위터 등)도 C++로 웹 서버를 개발하지 않고
PHP, 자바, 루비, 파이썬, Node.js 등 프로그래밍 언어로 개발
• 프로그래밍 언어 자체는 느리지만 큰 의미가 없다고 판단해 개발 속도와 유지
보수성이 좋은 프로그래밍 언어를 사용
• 자바스크립트 프로그래밍 언어는 C++, 자바보다 느리지만 Node.js를 사용하면
• 손쉽게 비동기 처리를 구현하여 빠른 처리가 가능

### 파일쓰는 메소드

- fs.writeFileSync(<파일 이름>,<문자열>) : 동기적으로 파일을 씀
- fs.writeFile(<파일 이름>,<문자열>,<콜백 함수>) : 비동기적으로 파일을 씀

### npm

노드 패키지 매니저

 npm install <모듈이름>
## [05월 10일]
>interval = Math.floor(interval / (100*60*60*60)); // 밀리세컨이여서 초로바꾸고 분 , 시,일로 바꿈ㅍ
>console.log(interval);<br>

>pop  마지막 요소 뺴냄<br>

>1.pop() : 배열의 마지막 주소에 있는 값을 제거.<br>
>2.shift() : 배열의 첫번째 주소에 있는 값을 제거 후 반환.<br>
>3.unshift() : 배열의 첫번째 자리에 새로운 요소 추가 후 변경된 배열의 길이를 반환.<br>
>4.push() : 배열의 마지막에 새로운 요소를 추가 후 변경된 배열의 길이를 반환<br>
>5.concat() : 두개의 배열을 합쳐주는 함수.<br>
>6.reverse() : 배열을 역순으로 재배치.<br>
>7.splice() : 배열의 특정 위치에 배열 요소를 추가하거나 삭제.<br>
>8.sort() : 배열을 정렬.<br>
>9.join() : 배열의 모든 요소를 연결해 하나의 문자열로 만듬.<br>
>10.slice() : 배열의 지정한 부분을 리턴<br>

>forEach() 배열의 요소를 하나씩 뽑아 반복을 돌림<br>
>map() 콜백 함수에서 리턴하는 것을 기반으로 새로운 배열을 만듦<br>

>let foo  =[1,30,40,50,100];<br>

>foo.forEach((item,index) => {<br>
>  console.log(`${index} - ${item}`);<br>
>});<br>



>let bar = foo.map((item,index) => {<br>
>  return item;<br>
>});<br>
>console.log(bar);<br>

> 예외 처리<br>
>try{<br>
>//예외가 발생<br><br>
>}catch(exception){<br>
>여기서처리<br>
>}finally{<br>
>무조건 실행<br>
>}<br>

## [05월 03일]
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



