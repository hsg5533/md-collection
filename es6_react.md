# 리액트, Node.js, ES6 정리

## 1. 리액트 (React)

- 자바스크립트 라이브러리로 사용자 인터페이스(UI)를 만들기 위해 사용
- **SPA(Single Page Application)** 방식의 UI 생성
- **컴포넌트 기반**으로 각각의 UI 조각을 모아 하나의 페이지 구성

## 2. Node.js

- 크롬 V8 자바스크립트 엔진 기반의 **서버 측 자바스크립트 실행 환경**
- 자바스크립트로 백엔드 프로그래밍 가능

## 3. NVM (Node Version Manager)

- Node.js 버전 관리 도구
- 윈도우/리눅스/맥 지원
- LTS(장기 지원 버전)과 최신 버전 병행 사용 가능

### 3.1 NVM 기초 명령어

```bash
nvm install [버전]       # 예: nvm install 16.14.2, 또는 nvm install --lts
nvm uninstall [버전]     # 설치된 Node.js 제거
nvm list                 # 설치된 버전 목록 출력
nvm use [버전]           # 특정 버전 사용 설정
```

## 4. Yarn 설치 및 리액트 프로젝트 생성

### 4.1 Yarn 설치

```bash
npm install -g yarn
```

### 4.2 React 프로젝트 생성

```bash
yarn global add create-react-app
yarn create-react-app [프로젝트명]
# 또는
yarn create react-app [프로젝트명]
```

### 4.3 VSCode 확장 설치

- **ES7+ React/Redux/React-Native**
- **Prettier**: 코드 포매터
- 설정 > `formatOnSave` 체크
- `.prettierrc` 예시:

```json
{
  "useTabs": false,
  "printWidth": 100,
  "tabWidth": 2,
  "trailingComma": "all",
  "semi": true,
  "singleQuote": true
}
```

## 5. ES6 변수 키워드

- `let`: 블록 스코프의 변수 선언
- `const`: 재할당 불가한 상수 선언
- `var`과 차이점:
  - 블록 스코프 적용
  - 중복 선언 불가

### 무결성 내장 함수

- 기존 함수: `push`, `pop`, `splice`
- 대체 함수: `concat`, `slice` (불변성 유지)

## 6. 템플릿 문자열

- 문자열 내 변수 표현이 쉬움

```js
const name = "React";
console.log(`Hello, ${name}!`);
```

## 7. 전개 연산자 (Spread Operator)

- 나머지 값 혹은 배열 전체를 한번에 복사/전달

```js
const arr = [1, 2, 3];
const newArr = [...arr, 4];
```

## 8. 클래스 사용 (ES6)

- `class` 키워드 사용
- 생성자: `constructor()`
- 상속: `extends`, 부모 접근: `super()`
- **다중 상속, 인터페이스 지원 없음**

## 9. 화살표 함수 (Arrow Function)

- `function` 키워드 생략 가능

```js
const add = (x, y) => x + y;
const addCurried = (num) => (value) => num + value;
```

## 10. 객체 확장 표현식

- key를 명시하지 않아도 변수명이 key로 사용됨
- key에 연산 가능

```js
const x = 10;
const obj = { x }; // { x: 10 }

const key = "name";
const obj2 = { [key + "Value"]: "React" };

const obj3 = {
  greet() {
    return "Hello";
  },
};
```
