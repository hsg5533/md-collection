# 1. 개요

- node.js는 javascript를 실행할 수 있게 해주는 Runtime 환경이다
- node.js를 설치하면 작성한 자바스크립트를 실행할 수 있다
- 이를 활용해 javascript언어로 작성된 서버, 앱, 소프트웨어를 만들 수 있다
- ejs라는 확장자의 파일을 이용하여 별도의 html를 생성할 수 있고 자바스크립트를 `<% %>`태그를 통해 jsp처럼 사용할 수 있다
- node.js와 함께 쓰이는 것 중에 express라는 것이 있는데 이 것은 node.js 서버 프레임워크라고 이해하면 된다

# 2. 시작하는 법

## 2-1. 원하는 디렉토리를 생성한 후 cmd로 `npm init -y`를 입력하면 해당 디렉토리에 package.json파일이 만들어진다

## 2-2. cmd에 npm install express를 입력한다

## 2-3. index.js 이름의 파일을 생성하여 다음의 코드를 입력한다.

```javascript
const express = require("express");
const app = express();
// 포트 설정
app.set("port", process.env.PORT || 3030);
// 아이피 설정
app.set("host", process.env.HOST || "0.0.0.0");
// 루트 접속시 아이피 출력
app.get("/", function (req, res) {
  res.send("접속된 아이피: " + req.ip);
});
// 서버 동작중인 표시
app.listen(app.get("port"), () =>
  console.log(
    "Server is running on : " + app.get("host") + ":" + app.get("port")
  )
);
```

## 2-5. cmd에서 node index.js를 입력하여 node를 실행할 수 있다.

- package.json에서 scripts부분에 `"start": "node ./index.js"`를 입력하면 npm start로 node를 실행할 수 있다.

# 3. Forever

## 3-1.forever를 사용하면 서버가 중지되지 않는다.

다음 명령어를 사용하어 설치할 수 있다

```bash
 npm install -g forever
```

## 3-2.서버를 시작할 때 다음 명령어를 사용하면 된다.

```bash
forever start -c "npm start" ./
```

# 4. nodemon

- 파일을 수정했다면 다시 파일을 저장하고 express를 재시작하여야지만 변경사항이 적용된다.

## 4-1. nodemon을 사용하여 express 재시작을 자동화할 수 있다. 다음 명령어로 설치가 가능하다.

```bash
npm install -g nodemon
```
