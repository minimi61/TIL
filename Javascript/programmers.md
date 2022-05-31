### 220531
-   x만큼 간격이 있는 n개의 숫자
    -   function solution(x, n) {<br>
    var answer = [];<br>
    for(let i =1; i <= n; i++){<br>
        a = x * i;<br>
        answer.push(a)<br>
    }<br>
    return answer;<br>
    }

    -   다른 사람 식: <br>
    function solution(x, n) { <br>
    return Array(n).fill(x).map((v, i) => (i + 1) * v)<br>
    }<br>

    -   Array.prototype.fill(): arr.fill(value[, start[, end]])
        - value: 배열을 채울 값
        - start 시작 인덱스, 기본값은 0
        - end: 끝 인덱스, 기본 값은 this.length
        -  const Array = [1,2,3,4]<br>
        Array.fill(0,1,3); <br>
        // [1,0,0,4]