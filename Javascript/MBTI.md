### 220620 Webkit
-  
```
    @-webkit-keyframes fadeOut {
    from { opacity : 1; }
    to { opacity : 0;  }
}
```
- webkit을 부를 때에는 ~style.WebkitAnimation = "fadeIn 1s"; 이렇게 불러주면 됨
    -  -webkit- : 구글, 사파리 브라우저에 적용

    -  -moz- : 파이어폭스 브라우저에 적용

    -  -ms- : 익스플로러에 적용, 보통 생략합니다.

    -  -o- : 오페라 브라우저에 적용

### 220621 sort
-     
```
let resultArray = pointArray.sort(function (a, b) {
        if (a.value > b.value) {
            return -1;
        }
        if (a.value < b.value) {
            return 1
        }
        return 0;
    })
```
-   sort()함수는 배열 정렬, 오름차순(1부터 내려감)
-   두개의 배열 element를 파라미터로 입력받음
-   sort() 함수는 파라미터(compareFunction)가 입력되지 않으면, 유니코드 순서에 따라서 값을 정렬
-   내림차순 방법 :
    -   arr.sort(function(a, b)  {<br>
  return b - a;<br>
});