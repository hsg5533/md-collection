- setState함수는 비동기로 동작하며 리액트의 클래스형 컴포넌트에서 state를 변경하고 관리할 수 있다
- setState함수는 componentDidMount함수 안에서 사용할 경우 제일 마지막으로 실행한다
- setState함수가 실행되면 render함수를 실행하여 컴포넌트를 리랜더링한다
- 여러 개의 setState()를 사용해도 모든 변화가 완료 된 후 리렌더링 된다
- setState함수에서 콜백 함수가 있다면 콜백함수가 먼저 실행 된 후 변수가 업데이트 되고 그 후 컴포넌트가 리랜더링된다

## ex. state안에 num이라는 변수가 있고 이 값의 초기값이 0일 때

```javascript
// setState함수는 비동기로 실행되어 기존 초기값에서 1을 더해 num의 값은 3이 아닌 1이 된다
this.setState({ num: num + 1 });
this.setState({ num: num + 1 });
this.setState({ num: num + 1 });

// 똑같은 예시로 이렇게 코드를 작성한다고 하면 num의 값은 9가 되는 것이 아닌 setState함수가 비동기로 실행되어 num의 값은 7이다
this.setState({num: num + 1});
this.setState({num: num + 1});
this.setState({num: num + 7});

// 이렇게 코드를 작성해야 state의 이전 값에서 1을 더하여 num의 값은 3이 된다
this.setState((prevState) => ({num: prevState.num + 1}));
this.setState((prevState) => ({num: prevState.num + 1}));
this.setState((prevState) => ({num: prevState.num + 1}));

// 리액트의 클래스형 컴포넌트 실행과정
render() -> componentDidMount() -> setState() -> render()
```
