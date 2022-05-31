# 노마드코더
## HTML, JS
### 3.0~3.1 강의(220518)
-   js 파일이 있기에 js를 통해 html의 내용을 갖고 올 수 있음, document가 html이 js파일을 load하게 해줌->그 다음에 browser를 통해 우리가 document에 접근 가능
-   브라우저에서 이미 자바스크립트와 HTML의 동기화를 제공하여 연결만 해줘도 불러오고 설정 할 수 있음
-   HTML : CSS, JS 갖고오는 접착제 같은 역할
-   console에 document를 입력하면 작성한 HTML 가져올 수 있다.
-   document
    -   브라우저에 존재하는 object
    -   모든 것들의 시작점
    -   web site 의미
    -   JS관점에서의 HTML

-   console.dir()도 쓸 수 있는데 dir함수는 객체의 속성을 계층구조로 출력,<br>
log함수로 document.body 객체 출력하면 태그내용 나오고 dir 함수 쓰면 객체의 속성 출력<br>
element의 내부볼 수 있다.
-    JS에서 HTML document 객체로부터 title 가져올 수 있다(불러오기, 수정도 가능)
-   document 함수 중 getElementById라는 함수가 HTML에서 id를 통해 element를 찾아준다. element 찾고 나면, JS로 해당 HTML의 무엇이든 바꿀 수 있다(element의 innerText 등)

### 3.2~ 3.8 강의(220520)
- 원하는 값 불러오는 방법 여러가지 있다.
    -   getElementById : 하나의 값(id)
    -   getElementByClassName: 배열(배열을 가져오면 .innerText와 같은 방법 사용 x)
    -   getElementByTagName : 배열(위와 동일)
    -   querySelector : getElementById는 하위 태그를 선택할 수 없다. 이 때 사용하는 것. 한개만 선택, CSS selector처럼 원하는 요소 선택이 가능하고 innerText 사용 가능<br>
    querySelector("#id명") = getElementById("id명")
    -   querySelectorAll : 동일한 class를 가진 태그가 여러개인 경우 다 불러올 때 쓴다.
- Event
    -   console.dir()를 통해 object로 표시한 element를 보여줌(전부 js object).<br>
    그 element 중 앞에 on이 붙은 것들은 event이다.
    -   event: 어떤 행위하는 것, 모든 event는 js가 listen할 수 있다.(클릭,마우스 올리기, enter누르기 등)
    -   eventListener: event를 listen한다, js에서 무슨 event를 listen하고 싶은지 알려줘야 한다.
    -   title.addEventListener("click",함수 이름)
        -    누군가가 title을 click하는 것을 listen할 것임
        -   click하면 함수이름이라는 function이 동작하길 원함
        -    함수() : ()두 괄호는 실행이라는 의미인데 js가 특정상황에 수행하길 바라기에 addEventListener("click",함수이름) 함수이름하고 ()괄호 안 넣음
    -   listen하고픈 event 찾는 좋은 방법: 구글에 element이름 검색(ex) h1 html element mdn), JS 관점에서 찾기를 원하면 Web APIs라는 문장 포함된 페이지로 gogo,<br>
    복잡하면 element를 console.dir()로 출력해서 on~으로 시작하는 것을 사용하면 됨
    -   title.onclick = blabla; === title.addEventListener("click",blabla)와 같지만 addEventListener를 더 선호함, removeEventListener을 통해 event listener을 제거할 수 있기에
    -   document.body(title,head) 로 불러올 수 있다. But, div, h1 등 element들은 querySelector, getElementById 등으로 찾아야함(ex)document.querySelector('h1'))
    -   window는 기본 제공 (resize, online, offline 등 가능)
    -   1. element 찾기, 2. event를 listen, 3. 그 event에 반응하기


-   getter 메소드: 인스턴스나 클래스 변수의 값을 가져오는 메소드<br>
setter 메소드: 인스턴스나 클래스 변수의 값을 적용하는 메소드

-    raw string이 반복되면 const 상수로 만들어서 쓸 것!(오류발생 안되기 위해)

-   classList : 우리의 class들 목록으로 작업할 수 있게 허용
    -   js에서 사용하는 것은 HTML element가 가지고 있는 또 하나의 요소 사용하는 것 = element의 class 내용물 조작을 허용한다는 뜻
    -   classList.contains : 우리가 명시한 class가 HTML element의 class에 포함되어 있는지 말해줌
    -   classList.remove : 목록에 있는 것을 삭제
    -   classList.add : 목록에 새롭게 추가
    -   classList.toggle : 토큰이 존재하면 토큰제거, 토큰존재 하지 않으면 토큰 추가<br>
    #### toggle이 대박이다!!!!
-   className : 이전 class 상관않고 모든 것을 교체


### 4.0~ 강의 (220523)
-   if (username === "") {<br>
        alert("please write your name")<br>
    } else if (username.length > 15) {<br>
        alert("Your name is too long")<br>
    }<br>
    여기서 username.length > 15 이 부분은  html에서 바꿔줄 수 있다.
-   input의 유효성 검사를 작동시키기 위해서는 input태그가 form 태그 안에 있어야 한다
-  html 규칙:
    -   form태그가 submit되면 내 웹사이트를 재시작시킴
    -    form 안에서 엔터를 누르고 input이 더 존재하지 않으면 자동으로 submit된다는 규칙
    -   form 안에 있는 버튼을 눌렀을 때, 이 때도 form이 자동으로 submit됨
    -   js에서 해결하기 위해서는 form의 submit event를 감지하고 있는 것을 loginForm.addEventListener("submit", clickSubmit ) 이렇게 바꿈,<br>submit은 엔터를 누르거나 버튼을 클릭할 때 발생함
-   const clickSubmit = (potato) => {<br>
    potato.preventDefault();
    -   //<a>태그나 <submit>과 같은 태그처럼 몇몇 태그는 특정 기능을 가지고 있다.
        -   a태그는 href를 통해 특정 사이트로 이동하거나, submit태그는 값을 전송하면서 창이 새로고침(reload)된다.
        -   이런 태그의 이벤트 기능을 preventDefault를 통하여 동작하지 않도록 막을 수 있다.
    -   // preventDefault : 어떤 event의 기본 행동(어떤 function에 대해 브라우저가 기본적으로 수행하는 동작)이 발생되지 않도록 막는것<br>
    console.log(potato)
    -   // 위의 콘솔 찍어보면 정보가 뜸, 이 정보가 방금 실행된 event임
    -   // clickSubmit에 대해 하나의 argument로 정보 받음
    -   // 모든 EventListener function의 첫번째 argument는 항상 지금 막 벌어진 일들에 대한 정보
    -   // argument라는 공간만 제공해주면 JS가 방금 일어난 event에 대한 정보를 지닌 argument를 채워넣는다
    const username = loginInput.value;<br>
    console.log(username)<br>
    }<br>
    loginForm.addEventListener("submit", clickSubmit)<br>

    -   // event 발생시 브라우저가 해당 함수 실행
    -   // clickSubmit(argument=event로부터 정보를 받아 해당 함수로 넘겨줌)


### 4.3~ (220524) localstorage활용과 저장한 값 새로고침해도 나오지 않게 하는법
-   visibility:hidden은 공간은 그대로 두고 보이지만 않는건데 display:none은 잡아둔 공간도 사라짐
-   local storage: 
    -   API의 이름
    -   저장할 수 있게 해줌
    -   사용 방법: localstorage.뒤에 
        -   .removeItem(저장된 아이템제거)
        -   .getItem(value 불러오기)
        -   .setItem(key,value 입력)


### 4.7~ (220525)
-   `<button>`과 `<input type="submit" >` 차이
    -   폼 전송 기능을 하는 `<input type="submit">` 과 `<button>` 은 기능적으로 동일하다. 기본적으로 button 요소는 type 속성을 명시하지 않으면 submit 기능을 수행한다. 즉 폼에서 이를 대체하기 위한 목적으로는 안성맞춤이다.<br>
    -   button 속성값
        -   type="submit" : 폼의 전송 기능을 담당한다.
        -   type="reset" : 폼 작성 내용을 초기화하는데 사용한다.
        -   type="button" : 흔히 자바스크립트를 이용한 기능 구현에 많이 사용한다.
        -   (출처: https://webdir.tistory.com/421)

-   css selector combination 에 이런 규칙이 있음
    - 후손 셀렉터(Descendent Selector) : '스페이스'로 연결
    - 자식 셀렉터(Child Selector) : ' >' 로 연결
    - ex) `<h2 id="clock"></h2>`이면 h2#id로 스페이스 없이 연결
- interval = 매번 일어나야 하는 무언가!
- setInterval(실행할 함수, 실행할 함수의 주기(ms단위1초=1000))!
- setTimeout(sayHello, 1000);
1초 기다렸다가 한번만 실행.


### 5.1 ~ (220531)
-   string이 적어도 2개 이상의 문자를 가지고 있게 만드는 방법 
    -   number -> string으로 바꾸기
        -   String(date.getHours())
        -   date.getHours().toString()
    -   padStart(최소 문자길이, 추가할 내용): 앞에 문자 추가 / padEnd(): 뒤에 문자 추가
    -   ex ) "1".padStart(2, "0") : 문자 길이가 2이상이여야 하고 없으면 앞에 0 추가 <br>
결과 : "01"
-   Math 메서드
    -   Math.ceil() 올림
    -   Math.floor() 내림
    -   ex) const todaysQuote = quotes[Math.floor(Math.random() * quotes.length)];
        -   Math부터는 숫자임.
-   const bgimg = document.createElement("img");<br>
    createElement를 통해 "img"태그를 만든다
-   bgimg.src = `img/${chosenImg}`;<br>
    src를 만들어줄 수 있음
-   document.body.appendChild(bgimg);<br>
    HTML에 body태그 안 새로운 태그 만들어 줌<br>
    appendChild 메서드는 한번에 한개의 노드만 추가할 수 있음
    -   append, appnedChild 메서드 모두 부모노드에 자식 노드 추가
    -   append는 여러 개의 자식 요소 설정 가능<br>
    ex) document.body.append(div, 'hello',span, p)
-   css => position : absoulute 부모에 position: relative 안줘도 사용 가능, body를 기준으로 위치하기도