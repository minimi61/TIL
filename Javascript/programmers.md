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

    -   fill? map?
    -   Array.prototype.fill(): arr.fill(value[, start[, end]])
        - value: 배열을 채울 값
        - start 시작 인덱스, 기본값은 0
        - end: 끝 인덱스, 기본 값은 this.length
        -  const Array = [1,2,3,4]<br>
        Array.fill(0,1,3); <br>
        // [1,0,0,4]



### 220608
-   핸드폰 번호 가리기
    -   str.substring(indexStart[, indexEnd])
    -   str.padStart(targetLength [, padString]) : <br>
        targetLength: 목표 문자열 길이. 현재 문자열의 길이보다 작다면 채워넣지 않고 그대로 반환.<br>
        padString: 현재 문자열에 채워넣을 다른 문자열. 문자열이 너무 길어 목표 문자열 길이를 초과한다면 좌측 일부를 잘라서 넣음. 기본값은 " ".<br>
    -   slice() 메소드: begin부터 end 전까지의 복사본을 새로운 배열 객체로 반환한다. 즉, 원본 배열은 수정되지 않는다.
    -   repeat() : string.repeat(반복 카운트)

    -   내가 푼 식<br>
        1.   substring 함수를 통해서 뒷자리 4개를 잘라줌
        2.  나머지 길이를 알아냄
        3.   나머지 길이를 '*'로 채우기 위해  padStart()를 사용
        let answer = '';<br>
        let a = phone_number.substring(phone_number.length-4);<br>
        let b = phone_number.length-a.length;<br>
        answer = answer.padStart(b,'*')+a
    
    -   다른 사람의 식<br>
         var result = "*".repeat(s.length - 4) + s.slice(-4);<br>
         


