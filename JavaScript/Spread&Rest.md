#### Spread
- 배열의 원소 혹은 객체의 프로퍼티를 나눌 때 사용한다.
```JavaScript
const newArray= [...oldArray, 1, 2]
const newObject= {...oldObject, newProp: 5}
// oldArray 배열에 존재하는 모든 원소들을 새로운 배열에 추가한다.
// 원소 1과 2를 추가할 경우 첫번째 구문을 사용한다.
// oldArray 앞에 ...이 있으며 모든 원소들을 꺼내 대괄호로 새롭게 생성한 배열에 추가한다.
// 객체의 경우 역시 newProp과 함께 중괄호를 사용해 새로운 객체를 만든다.
// ...Object로 oldObject의 모든 프로퍼티 값을 꺼내 새로운 객체의 키 값으로 추가한다.
// oldObject가 새로운 프로퍼티를 가질 경우 newProp:5로 덮어 쓰여진다.
```

#### Rest
- 함수의 인수 목록을 배열로 합칠 때 사용한다.
- 함수의 인수 목록에서 사용한다.
```JavaScript
function sortArgs(...args){
  return args.sort()
}
// sortArgs는 매개변수를 무한대로 받는다. (매개변수의 갯수에 무관하게 ...args로 적는다)
// 매개변수의 목록에 배열 메소드를 적용하거나 원하는 방법으로 매개변수를 저장할 수 있다.
```


<br>
<br>


##### Spread Example
![image](https://user-images.githubusercontent.com/79950504/181288619-35fbfd3a-2391-49f4-a307-0cf1dec08395.png)  
- ... 없이 실행했다면 [[1, 2, 3], 4]로 표현되었을 것이다.
