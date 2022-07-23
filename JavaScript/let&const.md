### var
- JavaScript에서 변수를 생성할 때 사용한다.

#### let
- 값을 수정할 수 있는 변수를 선언할 때 사용한다.

#### const
- 한번 지정하면 절대 변하지 않는 값인 상수를 선언할 때 사용한다.
- 새로운 값을 할당할 수 없다.

<br>

![image](https://user-images.githubusercontent.com/79950504/180605969-eb2acc46-9339-45cb-9c48-8597bca3c338.png)
- 에러가 발생하는 이유 : 상수 변수에 값을 재할당하려고 했기 때문이다.

<br>

### Arrow Function (화살표 함수)
```JavaScript
const myFnc= () => {
}
```
- JavaScript 함수를 생성하는 또 다른 구문이다.
- "this"로 인해 발생하는 많은 문제점을 해결해주는 장점을 가지고 있다. (this는 항상 우리가 원하는 객체를 참조하지 않는다)
- 화살표 함수 안에 "this"를 사용하면 항상 정의한 객체를 나타내며 실행 중에 갑자기 바뀌지 않는다.

<br>

![image](https://user-images.githubusercontent.com/79950504/180606233-20d09ff8-6b88-4d6f-83d8-e4f255315b56.png)
- Undefined가 발생하는 이유 : 어떠한 인수도 전달되지 않았기 때문이다.
- 해당 함수 (printMyName)에 예를 들어 인수로 'Max' 값을 전달하면 console 창에 'Max'가 출력된다.

#### Arrow Function
```JavaScript
const printMyName= (name) => {
  console.log(name);
}

printMyName('Max');
```
- 마찬가지로 'Max'가 출력되는 것을 볼 수 있다.

```JavaScript
const printMyname= name => {
  console.log(name);
}

printMyName('Max');
```
- 인수가 하나인 경우에 사용할 수 있는 구문이다.

```JavaScript
const printMyName= (name, age) => {
  console.log(name, age);
}

printMyName('Max', 20);
```
- 인수가 하나 이상인 경우에 출력 함수에 위와 같이 입력해야한다.
