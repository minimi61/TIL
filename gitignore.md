### 20220613
-   .gitignore 을 이용하여 API키나 보안과 관련된 내용들을 숨길 수 있음
    -   무시할 파일을 넣어주면 됨
    -   ex) js/keys.js <=여기에 API키가 있음
    -   js/keys.js에는 window.api = '~~' 으로 전역변수 설정해주면 됨!


-   .env 파일로 .gitignore 넣어줄 수 있음
    -   .env 파일은 환경변수를 설정하는 파일, 남들에게 보여서는 안되는 정보들 담을 수 있음
    -   .env 사용하려면? dotenv가 필요
    1. dotenv 라이브러리 Node.js 프로젝트 설치
    2.  npm install dotenv --save<br>
        yarn add dotenv
    3. 해당 프로젝트 루트에 .env하고 파일을 만들면된다.
    4. .env 파일 안에 환경변수 설정<br>
        DATABASE_USERNAME=유저네임<br>
        DATABASE_PASSWORD=패스워드<br>
        DATABASE_NAME='데이타베이스명'<br>
    5. 환경변수를 사용할 js파일에 dotenv 사용<br>
        require로 다운받은 dotnev를 불러와서 사용하겠다고 설정<br>
        const dotenv = require('dotenv');<br>
        dotenv.config();
    6. .env 환경변수 사용하기 : process.env<br>
        dotenv를 받아온 파일에서, .env를 사용하려면 .env에 지정했던 환경변수 앞에 process.env.붙여서 사용할 수 있다.<br>
        process.env.DATABASE_USERNAME<br>
        env에 환경변수 DATABASE_USERNAME의 값을 "유저네임"으로 설정했었기에, 변수로 "유저네임"을 사용할 수 있는 것이다.<br>
         this.config = {<br>
      host: 'localhost',<br>
      user: process.env.DATABASE_USERNAME <br>
      password: process.env.DATABASE_PASSWORD<br>
      database: process.env.DATABASE_NAME <br>
    };<br>
    return this;<br>