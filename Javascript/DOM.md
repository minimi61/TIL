#### BOM
-   브라우저와 관련된 객체들의 집합을 브라우저 객체 모델(Browser Object Model)
- BOM의 최상위 객체는 window

#### DOM(Document Object Model)
-   DOM은 BOM 중의 하나, window 객체의 하위 객체
-   문서 객체란 html, body 와 같이 html 문서의 태그들을 js가 이용할 수 있는 객체로 만든 것 (ex. document 객체를 통해 body 객체에 접근)
-   넓은 의미: 웹 브라우저가 HTML 페이지를 인식하는 방식
-   좁은 의미: document 객체와 관련된 객체의 집합

<img src='https://image.slidesharecdn.com/dom-130225112417-phpapp02/95/an-introduction-to-the-dom-3-638.jpg?cb=1367487766'>

-   DOM은 tree형식의 자료구조임
    -   tree형 자료구조 : 위의 root에서 아래 node로 퍼져가는 형태
    -   위쪽 node는 부모, 아랫쪽 노드는 자식, 자식이 없는 경우 leaf node
    -   node란 ? head, body, title, script, h1 등 태그 뿐만 아니라 태그 안 텍스트나 속성 등 모두 node에 속함/ HTML 태그: 요소노드(element node), 요소노드 안에 있는 글자는 Text node
