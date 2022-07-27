#### Destructuring [구조분해할당]
- 배열의 원소나 객체의 프로퍼티를 추출해서 변수에 저장할 수 있도록 한다.
- 스프레드 연산자와 비슷하지만 스프레드는 모든 원소와 프로퍼티를 가져와 새 배열 혹은 객체에 전달하지만 Destructuring은 원소나 프로퍼티를 하나만 가져와서 변수에 저장한다.

<br>
<br>

##### Array Destructuring Example
```JavaScript
[a, b]= ['Hello', 'Max']
console.log(a) // Hello 출력
console.log(b) // Max 출력

```
- 배열을 새롭게 생성하는 것 같지만 변수 a와 b에 각각 Hello와 Max를 할당한 것이다.
- 객체의 Destructuring도 배열을 Destructuring하여 가져올 프로퍼티의 순서를 정하는 곳에 중괄호를 넣은 구문을 사용한다.

<br>

##### Object Destructuring Example
```JavaScript
{name}= {name: 'Max', age:28}
console.log(name) // Max 출력
console.log(age) // undefined 출력 -> 객체에서 age를 추출하지 않았기 때문이다.
```
- 왼쪽에 {name}을 넣고 오른쪽 객채의 name 프로퍼티를 대상으로 한다.

