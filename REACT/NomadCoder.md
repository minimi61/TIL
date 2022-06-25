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
