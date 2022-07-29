# React Element
엘리먼트는 React 앱의 가장 작은 단위로 엘리먼트는 화면에 표시할 내용을 기술

## Dom 엘리먼트 렌더링
```javascript
<div id ="root"></div>
```
이 안에 들어가는 모든 엘리먼트를 React Dom 에서 관리하기 때문에 이것을 루트 DOM 노드라고 부름

리액트로 구현된 애플리케이션은 일반적으로 하나의 루트 DOM 노드가 있음
리액트를 기존 앱에 통합하려는 경우 원하는 만큼 많은 수의 독립된 루트 DOM 노드가 있음

# React Component
컴포넌트를 통해 UI를 재사용 가능한 개별적인 여러조각으로 나누고 각 조각을 개별적으로 사용

## 함수 컴포넌트와 클래스 컴포넌트
컴포넌트를 정의하는 가장 간단한 방법은 자바스크립트 함수를 작성하는 것

```javascript
function Welcome(props){
    return <h1>Hello, {props.name} </h1>
}
```
위 함수는 데이터를 가진 하나의 props 객체 인자를 받은 후 React 엘리먼트를 반환하므로 유효한 React 컴포넌트 => 이러한 함수는 함수 컴포넌트

```javascript
class Welcome extends React.Component {
    render() {
        return <h1>Hello, {this.props.name}</h1>
    },
}
```
클래스를 활용해서도 컴포넌트를 정의할 수 있음
위의 두가지 유형의 컴포넌트는 동일함

## 컴포넌트 합성
컴포넌트는 자신의 출력에 다른 컴포넌트를 참조할 수 있음
React 앱에서는 버튼, 폼, 다이얼로그, 화면 등의 모든것들이 컴포넌트로 표현

```javascript
function Welcome(props) {
    return <h1>Hello, {props.name}</h1>  
}

function App() {
    return (
        <div>
            <Welcome name = 'Kim' />
            <Welcome name = 'Lee' />
            <Welcome name = 'Park' />
        </div>
    )
}
```

## 컴포넌트 추출

```javascript
function Comment(props) {
  return (
    <div className="Comment">
      <div className="UserInfo">
        <img className="Avatar"
          src={props.author.avatarUrl}
          alt={props.author.name}
        />
        <div className="UserInfo-name">
          {props.author.name}
        </div>
      </div>
      <div className="Comment-text">
        {props.text}
      </div>
      <div className="Comment-date">
        {formatDate(props.date)}
      </div>
    </div>
  );
}
```
이 컴포넌트는 author, text, data를 props로 받음
먼저 className 이 Auator 인 컴포넌트를 추출

```javascript
function Auator(props) {
    return (
        <img className = "Avatar"
          src = {props.user.avatarUrl}
          alt = {props.user.name}
    )
}

```
```javascript
function Comment(props) {
  return (
    <div className="Comment">
      <div className="UserInfo">
      <Avatar user = {props.author} />
       ...
  );
}
```
위와 같이 컴포넌트를 사용

위의 userInfo-name 컴포넌트도 추출

```javascript
function UserInfo() {
  return (
    <div className="UserInfo">
      <Avatar user={props.user} />
      <div className="UserInfo-name">
        {props.author.name}
      </div>
    </div>
  )
}
```

위와 같이 컴포넌트 추출

```javascript
function Comment(props) {
  return (
    <div className="Comment">
      <UserInfo user={props.author} />
      <div className="Comment-text">
        {props.text}
      </div>
      <div className="Comment-date">
        {formatDate(props.date)}
      </div>
    </div>
  );
}
```

Comment 간단해짐





