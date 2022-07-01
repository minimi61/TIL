### 220624
-   리액트 규칙 
    1.  HTML을 HTML 페이지에 직접 작성 x
    2.  대신 js 코드 사용

-   리액트 import 방법 1 : HTML에 script 태그로 리액트와 리액트 돔,바벨을 삽입해야함
    -    리액트를 import했기 때문에 createElement function을 가진 리액트 object에 접근 가능
    -   const span 그러나 createElement(“span”) 은 반드시 생성하고자 하는 HTML 태그와 똑같아야함
        
    -    React JS - 어플리케이션이 아주 인터랙티브하도록 만들어주는 library. 엔진과 같다.
    -    React-dom - library 또는 package. 모든 react element들을 HTML body에 둘 수 있도록 해줌.
    -    ReactDOM.render() - render의 의미는 react element를 가지고 HTML로 만들어 배치한다는 것. 즉, 사용자에게 보여준다는 의미
    -   ReactDOM.render(span, span이 가야할 위치)<br>
        -> 그래서 보통 body에 id=“root” 만들어서 span을 root 안에 두라고 함
        
    -    React.createElement("span", {span의 property임, id='yoyo'}, “span의 내용”)<br>
        -> property는 class name, id도 가능 style도 가능<br>
        -> 참고만 하고 외우지 말기. 이렇게 쓸 일 없음
        
    -    바닐라JS는 HTML -> JS 순서<br>
        리액트는 JS -> HTML 순서
        
    -    JS가 element를 생성하고 React JS가 그것을 HTML로 번역하는 것<br>
        React JS는 업데이트 해야 하는 HTML을 업데이트 할 수 있음
    -   두가지(span, button 태그) const를 render하고 싶은 경우 div를 만들고 React.createElement('div', null, [span, button])와 같이 배열을 만들어서 const를 넣어준다
    -   property에 eventListener 넣는 것도 가능함<br>
        클릭 - {onClick : () => console.log('im clicked')}
    -   콘솔 안 뜰 경우 대소문자 확인(js와 같은지)

-   JSX : 자바스크립트를 확장한 문법, 보통의 HTML과 비슷, 그러나 property를 HTML 태그의 속성처럼 적으면 됨<br>
    -   const Title = <h3 onMouseEnter = { () => console.log('mouse enter')}>Hello</h3>
    -   style = {{ backgroundColor: "tomato" }} -> 스타일은 {} 2개임
    -   JSX를 브라우저가 온전히 이해하지 못하므로 이해할 수 있게 https://unpkg.com/@babel/standalone/babel.min.js 를 설치해야함<br>
    -> JSX로 적은 코드를 브라우저가 이해할 수 있는 형태로 바꿔준다. 바벨로 가져온 후 바벨 문장이 있는 곳 상위 script type = "text/babel"로 적어줘야 인식함
    -   변수를 JSX에 전달하는 방법<br>
        let counter = 0; 변수를 만들고
        Total clicks: {counter} 로 만들어주면
        변수의 카운터 숫자에 따라 변화됨
#### 컴포넌트의 첫 글자는 무조건 대문자로 시작!(직접 만든 요소는 전부 대문자로 시작해야함)
-   리액트의 장점 : UI에서 바뀐 부분만 업데이트 해줌

### 220627
-   리액트 js에서 데이터를 저장시켜 자동으로 리렌더링을 일으키는 방법
    -   const data = React.useState() console.log 시키면
        [undefined, f ] -> undefined와 함수가 적힌 배열이 나타남<br>
        undefined는 data이고 f는 data를 바꿀 때 사용하는 함수
    -   React.useState() 함수는 초기값을 설정할 수 있음 <br>
        즉, undefined는 초기값이고 두 번째 요소인 f는 그 값을 바꾸는 함수
    -   배열을 꺼내기 <br>
        const x = [1, 2, 3]<br>
        const [a, b, c] = x;으로 꺼낼 수 있음
    -   React.useState() 배열에서
        보통 데이터에는 counter처럼 원하는대로 붙이고
        f는 set 뒤에 데이터 이름을 붙임 (setCounter)
        어떤값을 부여하던 setCounter 함수는 그 값으로 업데이트하고 리렌더링 일으킴
        1. counter라는 데이터를 받음
        2. return()에 그 데이터를 담고 있음 (리턴은 사용자가 보게될 컴포넌트)
        3. 버튼이 클릭되면 counter값을 바꿔줄 함수 호출 -> setCounter
        4. counter의 새로운 값을 가지고 counter 함수를 호출
        5. 그 새로운 값은 setCounter(counter + 1)에 써준 counter + 1
    -   state를 세팅하는 데는 2가지 방법이 있다.
        1. 직접 할당 :setState(state +1) 현재 state랑 관련이 없는 값을 새로운 state로 하고싶은 경우
        2. 함수를 할당:setState(state => state +1) (함수의 첫번째 인자는 현재 state 이다) 현재 state에 조금의 변화를 주어서 새로운 state를 주고 싶은 경우

### 220628
-    input 옆의 쓰는 label의 for 속성은 react에서는 htmlFor로 표시한다.
-   controlled component :Input 태그 나오면 value, onChange 속성을 붙여서 상태를 관리하자
    -   onChange = {onChange} 
    input에 변화가 생기면 onChange 함수 실행

### 220629
-   state 값으로 input을 enabled할지 disabled할지 결정 가능함
-   디폴트 값이 false면 disabled = {!flipped} 로 disable적용되게 만들어줌
-   useState의 두번째 인자인 modifier 함수를 실행하면 해당 컴포넌트가 리렌더링된다
    -   리렌더링 조건
        -   props가 바뀔 때
        -   state가 바뀔 때
        -   부모 컴포넌트가 리렌더링될 때 
-   컴포넌트는 그 안에 또 다른 컴포넌트를 렌더링할 수 있음
    -   App 컴포넌트는 root div를 그려주는 역할
    -   App 컴포넌트는 그 안에 다른 2개의 컴포넌트들을 렌더링
    -   App 컴포넌트가 state를 가지도록 만들자
    -   select는 그냥 HTML
    -   HTML에 {}를 쓰면 js로 쓸 수 있음
    -   state를 변화시킬 때, 모든 것이 다 새로고침됨

- tips
    -   = () => {} 일 경우에는 함수가 여러개 쓸 때
    -   = () => () 는 return이 있거나 단일로 쓸 때
    -   onClick : 클릭시 이벤트(button)
    -   onChange : 타자 입력시 수정(input)

- 버튼의 style property(속성)사용시 <br>
    -  style - {{<br>
        backgroundColor: 'tomato',<br>
        color: 'white'<br>
    }} : 중괄호 두개 열고 일반적인 HTML방식으로
    -   여러개의 버튼 만들시 한가지의 버튼 컴포넌트로 만들어 재사용하면 효율적
        -   function Btn (props) Btn으로부터 전달받은 속성인 props로 인자를 받을 수 있음(이름은 내맘대로)
        -   <Btn banana="라라" /> 자동으로 Btn함수내 ({banana:'라라'}) or (props)로 전달
        -   Btn({props.banana}) == Btn({banana})
    -   이 오브젝트에 Btn() 컴포넌트의 첫번째 인자로 주어짐 (유일한 인자, Btn({text}, {No})

### 220630
-   리액트에서는 font-size와 같이 중간에 대시 기호(-)가 들어간 속성명은 fontSize와 같이 카멜 케이스로 바꿔야함
-   props 다시
    -   function App(<SaveBtn />)은 SaveBtn이라는 함수형 컴포넌트를 부르는 것
    -   function SaveBtn () {} <= 컴포넌트
    -   App 함수는 JSX 내부
    -   style 꾸미기  태그내 style={{ 안에 object 형식으로 }}
    -   props = App( <Btn ~~/>) 으로부터 보낸 모든 것(오브젝트)들을 전달받는 property
    -   object 바로 부르려면 Btn({banana})
    -   props에 이벤트를 전달한다고 해서 이벤트가 전달되는 것은 아니다, html태그안에 onClick을 직접 작성하고 파라미터로 넘긴 이벤트 함수를 넣어줘야함
-  React.memo(Btn) : 경고문
    -   리액트는 컴포넌트 상태가 변경되면 리랜더링한다
    -   리랜더링할 필요가 없는 컴포넌트도 랜더링되는 것이 문제
    -   이런 문제 해결한 것이 리액트메모, props가 변경되지 않는다면 리랜더링되지 않게 한다.(재사용성 높은 컴포넌트에 사용용이)
-   Prop Types
    -   리액트는 파라미터를 잘 못 넘겨도 확인할 수 없는 문제점이 존재, 이런 문제를 줄이기 위해서 PropTypes라는 모듈의 도움있음
    -  Btn이 어떤 prop들을 받는지 검사하는게 가능하게끔 도와줌(Btn.propTypes)
    -   src를 불러서 바벨위에 설치
    -   .isRequired를 통하여 필수적으로 필요한 것을 인식
    -   
    ```
    Btn.propTypes  = {
        text: PropTypes.string.isRequired,
        fontSize: PropTypes.number
    } 
    ```
    -   Btn({fontSize = 16})으로 기본 값 설정 가능
-   JSX 문법에서 return문을 사용할 때 그 뒤에 소괄호를 사용해야 하는 규칙   

### 220701
-   css를 이용시 전체가 다 적용될 수 있다 그 해결책으로 module을 사용 
-   module.css로 import하여 className = {styles.btn} 이렇게 부를 수 있다
#### ? 내내 다른 클래스 이름을 사용하기 위해 기억하는 것보다 훨씬 낫다? 기억할 필요가 없어진다? 리액트가 다 랜덤하게 바꿔준다? -> 
-   여기서 스타일은 className이나 id로 import한 스타일 객체의 property를 전달하여 적용된다는 것! 이는 기존의 "어떤 class나 id에 적용할 스타일"이 아닌 "특정 jsx element에 적용할 스타일"로 생각할 수 있다~ react 컴파일 과정 중 random class나 id가 생성되기 때문에 .css 파일의 class, id 이름을 굳이 외울 필요없다
-   useEffect
    -   두개의 argument를 가지는 함수 
        -   실행하려는 코드, dependency(지켜보려는 것) 구성
    - 한번만 실행하고 싶을때  
        -   첫번째 argument는 우리가 딱 한번만 실행하고픈 코드, 두번째는 [] 배열을 넣어줌
    -   특정 코드 변화있을 때만 원하는 코드 실행 방법 
        -   useEffect(()=> {console.log('search for'), keyword})이런 식으로 두번째로 써줌([] 대신, 배열안에 여러개 쓸 수 있음, 그렇다면 둘중에 하나라도 변화가 있으면 코드 실행)
        -   keyword가 변화할 때 코드 실행할 것이라고 react.js에 알려주는 것
        -   [] 빈 배열일 때 코드가 단 한번만 실행되는 이유: react가 지켜볼 것(dependencies)이 없어서 한번만 실행됨
        -   cleanup 
            -   컴포넌트가 destroy될 때도 코드 실행가능
            - useEffect 내에 return 함수로 이펙트 클린업
            - 리랜더링 -> 이전 이펙트 클린업 -> 새로운 이펙트 실행(순서는 클로져때문)
            -   
            ```
            useEffect(() => {
                console.log('hi');
                return function () {
                console.log('bye')
                }
            },[])
            return <h1>Hello</h1>
            ```

