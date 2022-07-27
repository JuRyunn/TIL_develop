#### class
```JavaScript
class Person {
  name= 'Max'; // Property
  call= () => {...} // Method
```
- 객체를 위한 핵심이다.
- class 키워드로 정의되며 프로퍼티와 메소드를 가질 수 있다.
- React에서 컴포넌트를 생성할 때 사용한다.

##### Usage
```JavaScript
const myPerson= new Person()
  myPerson.call()
console.log(myPerson.name)
```
##### Inheritance
```JavaScript
class Person extends Master
```
- 다른 클래스에 있는 프로퍼티와 메소드를 상속한다면 잠재적으로 새로운 프로퍼티와 메소드를 추가할 수 있다.

<br>
<br>

![image](https://user-images.githubusercontent.com/79950504/181182238-a93c7ca5-483e-4368-b558-ccb94205e236.png)
- this 키워드로 프로퍼티를 설정할 수 있다. 
- 클래스를 NEW Person() 메소드를 사용해 상수 person에 저장한 후 출력한다.
- 손쉽게 클래스를 사용할 수 있다.

<br>

![image](https://user-images.githubusercontent.com/79950504/181182979-a50b818d-3ad7-4d9c-84b2-98aecfdf1bb1.png)
- extand 키워드를 통해 클래스를 상속받아 확장할 수 있다.
- 다른 클래스를 확장하고 생성자를 실행하는 경우엔 아니지만, 만약 그렇다면 생성자 함수 내에 super() 메소드를 추가해야한다.

<br>
<br>

##### Propertie
- 클래스와 객체에 추가되는 변수를 의미한다.
```JavaScript
constructor() {
  this.myProperty= 'value'
}
```
```JavaScript
  myProperty= 'value'
  // 최신 JS는 클래스에 바로 프로퍼티를 할당할 수 있다.
```


##### Method
- 클래스와 객체에 추가되는 함수를 의미한다.
```JavaScript
myMethod() {...}
```
```JavaScript
myMethod= () => {...}
// 프로퍼티 값으로 화살표 함수를 사용하기 때문에 this 키워드를 사용하지 않아도 된다.
```


<br>

#### ES7
```JavaScript
class Human{
  gender= 'male';
 
  printGender = () => {
    console.log(this.gender);
  }
}


class Person extends Human {
    name= 'Max';
    gender= 'female';
  
  
  printMyName = () => {
    console.log(this.name);
  }
}

const person= new Person();
person.printMyName();
person.printGender();
```


