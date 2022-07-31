# state
리액트에서 state는 컴포넌트 내부에서 바뀔 수 있는 값을 의미<br><br>
porps는 컴포넌트가 사용되는 과정에서 부모 컴포넌트가 설정하는 값, 컴포넌트 자신은 해당 props를 읽기 전용으로만 사용<br>

props를 바꿀려면 부모 컴포넌트에서 변경해야함<br>
즉, 컴포넌트 내부에서 전달받은 value 값을 직접 바꿀 수 없음<br>

state를 활용하여 컴포넌트 내부에서 값을 바꿀 수 있음<br>

## state VS props<br>
props와 state 모두 렌더링 결과물에 영향을 주는 정보를 갖고 있는 객체이지만,  props는 컴포넌트에 읽기전용으로 전달만 되지만 state는 컴포넌트 안에서 관리 가능<br>

state는 클래스 컴포넌트가 가지고 있는 ```state```와 함수컴포넌트의 ```useState``` 함수를 통해 사용 가능<br>

## 클래스형 컴포넌트 State<br>
클래스형 컴포넌트에서 state 사용법

```javascript
class MyComponent extends Comment {
    constuctor(props) {
        super(props)
        this.state = {
            number: 0
        }
    }
    render() {
        return(
            <div>{number}
                <button onclick {() => { this.setState({number:number+1})}}>클릭</button>
            </div>
        )
    }
}
```
위의 constuctor는 생성자 함수로 작성시 반드시 ```super(props)``` 호출해야함<br>
this.state값에 초기값을 설정<br><br>

컴포넌트의 stste 는 객체 형식이어야 함<br>

```javascript
onClick = {()=> {
    this.setState(number: number+1)
    this.setState(number: this.state.number + 1)
}}

```
위와 같이 number를 this.state를 두번 호출해도 state 값을 업데이트 할때는 상대가 비동기적으로 업데이트함<br>
따라서 prevState를 사용하여 업데이트 하는 가정이 필요

```javascript
onClick = {()=> {
    this.setState(prevState => ({
        number: prevState.number+1
    }))
}}
```


## 함수형 컴포넌트<br>

```javascript
const App = () => {
   const[value, setNum] = React.useState(2);

  return (
      <div>
        {value}
        <button onClick = {() => {setNum(value+1)}}>클릭</button>
      </div>
  )
}
```
위와 같이 useState 를 사용하여 초기값을 지정할 수 있음<br>
초기값 2를 가지고 +1 상태변경 하도록 가능<br>
