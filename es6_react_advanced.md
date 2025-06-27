# ES6 및 React 고급 개념 정리

## 1. 구조분해 할당 (Destructuring Assignment)

- 전개 연산자와 함께 사용 가능
- 배열 및 객체 요소를 한 번에 변수에 대입

```js
// ES5 방식
var list = [0, 1];
var item1 = list[0];

// ES6 방식
var [item1, item2, item3 = -1] = list;
```

## 2. 라이브러리 의존성 관리

- ES5: `<script>` 태그로 외부 라이브러리 로딩 (순서 중요)
- ES6: `import` 키워드를 사용하여 모듈 불러오기

```js
import 모듈명 from "파일경로";
```

## 3. 배열 함수

### (1) forEach()

- 배열의 각 요소를 순회

```js
array.forEach((item, index, array) => {
  console.log(item, index);
});
```

### (2) map()

- 콜백 함수 실행 결과로 **새로운 배열 생성**

```js
const result = array.map((item, index, array) => {
  return item * 2;
});
```

### (3) reduce()

- 배열의 요소를 누적 계산해 하나의 값 또는 객체 반환

```js
const sum = array.reduce((accumulator, currentValue, index, array) => {
  return accumulator + currentValue;
}, 0); // 0은 초기값
```

## 4. 비동기 함수 (Asynchronous Functions)

### 개념

- 특정 연산이 끝나기 전까지 기다리지 않고 다음 코드 실행
- JS는 싱글 스레드 기반이므로 비동기 처리가 중요

### (1) Promise

```js
const promise = new Promise((resolve, reject) => {
  // 비동기 처리
  if (성공) {
    resolve(결과);
  } else {
    reject(에러);
  }
});

promise
  .then((result) => console.log(result))
  .catch((error) => console.error(error));
```

- 상태
  - `pending`: 대기 중
  - `fulfilled`: 성공
  - `rejected`: 실패

## 5. React 이벤트 함수 바인딩 방법

### 1. 화살표 함수로 전달

```jsx
<button onClick={() => this.handleClick()} />
```

### 2. 익명 함수로 작성

```jsx
<button
  onClick={() => {
    this.handleClick();
  }}
/>
```

### 3. bind 사용

```jsx
<button onClick={this.handleClick.bind(this)} />
```

### 4. 생성자(constructor)에서 미리 bind

```js
constructor(props) {
  super(props);
  this.handleClick = this.handleClick.bind(this);
}
```
