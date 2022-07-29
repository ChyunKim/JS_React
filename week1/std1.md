# JSX 문법
JSX는 Javascript를 확장한 문법으로 React element를 생성

React 에서 렌더링 로직이 UI 로직과 연결되어 UI 관련 작업을 할 때 시각적 도움을 줌

## JSX 표현식

```JSX
function formatName(user){
  return user.firstName + '' + user.lastName;
}
const user = {
    firstName: 'kim',
    lastName : 'ch'
}
const element = <h1 className='greeting'>hello {formatName(user)}</h1>;
// const elements = React.createElement('h1', {className:'greeting'},'Hello world');
function App() {
  return (
      <div>{elements}</div>
  );
}
```
JSX의 중괄호 안에는 유효한 모든 자바스크립트 표현식을 넣을 수 있음

JSX도 표현식이므로 자바스크립트 함수 호출이 되며 자바스크립트 객체로 인식

즉, JSXfmf if문, for문, switch 문 등 사용이 가능하며 변수에 할당하고 인자로 받아들이며 함수로 반환 가능

### JSX 속성정의
어트리뷰트에 따옴표를 이용해 문자열 리터럴 정의 가능

```JSX
const element = <a href="https://www.reactjs.org">link</a>
```
 위와 같은 표현식을 어트리뷰트 타음표를 이용해 아래와 같이 사용가능

 ```JSX
 const elememt = <img src = {user.url}></img>
 ```

 ### JSX 자식정의
 태그가 비어있다면 XML 처럼 ```/>```를 이용해 바로 닫아주여야 함

 ```JSX
 const element = <img src = {user.url} />
 ```

 ```JSX
 const element = (
    <div>
        <h1>Hello world</h1>
        <h2>Good to see you here</h2>
    </div>
 )
 ```
 JSX 태그는 위와 같이 자식을 포함할 수 있음

 






