#### [let](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/let)&[const](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/const)
- let과 const는 기본적으로 var를 대체한다 (변수를 다시 할당하지 않을 경우 -> 효과적으로 constant로 변환한다)


<br>

#### [Arrow Function](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions)
- JS에서 함수를 생성하는 방법이다.
- this 키워드의 범위를 유지하는데 있어 [이점](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions#No_binding_of_this)을 제공한다.

```JavaScript
// Arrow Function의 구문
function animal(dog){
  console.log(dog);
}
```

```JavaScript
// Arrow Function의 구문: 2
const animal= function(dog)
  console.log(dog);
```

```JavaScript
// Arrow Function의 구문: 3
const animal= (dog) => {
  console.log(dog);
}
```

```JavaScript
// arguments가 없는 경우 함수 선언 시 빈 괄호를 사용해야한다.
const animal= () => {
  console.log('Bark!');
}
```

```JavaScript
// 하나의 argument가 있는 경우 괄호를 생략할 수 있다.
const animal= name => {
  console.log(dog);
}
```

```JavaScript
// 값을 return할 때 shortcut을 사용할 수 있다.
const returnMe= dog => dog

// 똑같다
const returnMe= dog => {
  return dog;
}
```


<br>


#### Exports&Imports
- React, JS에서 모듈이라 불리는 여러 JS 파일에 코드를 분할한다. (각 file/ 모듈의 목적을 명확하게 하며 관리가 용이하기 때문)
- 다른 파일의 기능에 접근하기 위해 export (available 하기 위해) 및 Import (access 확보하기 위해)가 필요하다.  

```JavaScript
// export엔 두가지 유형이 있는데 default와 named이다.

default => export default ...;
named => export const someData= ...;

import myNameChoice from './example/my/path/file.js'; //default exports를 import

import {ExampleData} from './example/my/path/file.js'; // Named export는 이름으로 import 되어야 한다.
// 파일 하나는 하나의 default, 무한한 named export를 가질 수 있다. 

// named export를 import할 경우 한번에 import 할 수 있다.
import * as upToMine from './example/my/path/file.js'; // upToMine은 모든 exported 변수, 함수를 하나의 JS 객체에 모은다.
```

<br>
<br>

#### Class
- 클래스는 constructor 함수와 prototypes를 대체하는 기능이다.
- JS 객체에 bluePrints를 정의할 수 있다.
```JavaScript
// 클래스뿐만 아니라 해당 클래스의 property (=name)가 정의된다. 
const Person {
  constructor() {
   this.name= 'SMU';
  }
}

const person= new Person();
console.log(person.name);  



// 위의 구문은 비효율적이기 때문에 다음과 같은 구문을 사용한다.
class Person {
  name= 'SMU';
}

const person= new Person();
console.log(this.name);  


// 메소드를 정의하는 것 또한 가능하다.
class Person {
  name= 'SMU';
  printName() {
    console.log(this.name);
  }
}

const person= new Person();
person.printName();  
 
 
// 또 다른 방법
class Person {
    name = 'SMU';
    printName = () => {
        console.log(this.name);
    }
}
 
const person = new Person();
person.printName();  


// 클래스 사용시 inheritance 사용이 가능하다.
class Human {
    species = 'human';
}
 
class Person extends Human {
    name = 'SMU';
    printName = () => {
        console.log(this.name);
    }
}
 
const person = new Person();
person.printName();
console.log(person.species);
```

<br>
<br>


#### Spread&Rest Operator
- 두개 모두 같은 구문을 사용한다. (...연산자)
- SpreadOperator는 배열에서 요소를 가져오거나 (= 배열을 요소의 리스트로 분해) 객체에서 속성을 가져온다.
- SpreadOperator는 배열과 객체를 복제하는데 유용하다.
- reference 유형이기 때문에 안정적으로 복사하는게 어려울 수 있다. (복사된 원본에 결함 발생 방지)

```JavaScript
// First Example
const FirstArray= [1, 2, 3];
const SecondArray= [...FirstArray, 4, 5]; // [1, 2, 3, 4, 5] 출력

// Spread Operator 사용
const FirstArray= {
  name= 'SMU'
};

const SecondArray= {
  ...FirstArray,
  num: 7
}; // {name: 'SMU', num: 7 } 출력
```

<br>
<br>

#### Destructuring
- 배열이나 객체의 값에 쉽게 접근할 수 있으며 변수에 할당할 수 있다.
```JavaScript
// Array Example
const Array = [1, 2, 3];
const [test1, test2] = array;
console.log(test1); // 1 출력
console.log(test2); // 2 출력
console.log(Array); // [1, 2, 3] 출력  


// Object Example
const Object = {
    name: 'SMU',
    age: 7
}
const {name} = Object;
console.log(name); // 'SMU' 출력
console.log(age); // undefined 출력
console.log(Object); // {name: 'SMU', age: 7} 출력  


// 인자를 가진 함수 처리
// 함수 내 name만을 출력하고 싶지만 person 객체를 보내고 있다.
// Object.name을 함수 내에서 호출해야한다.
const printName = (personObj) => {
    console.log(personObj.name);
}
printName({name: 'SMU', age: 7}); // 'SMU' 출력  


// Object.name을 destructuring으로 압축
// name propery를 가져와 name이라는 이름의 변수/인수에 저장하고 함수 본문에서 사용이 가능
const printName = ({name}) => {
    console.log(name);
}
printName({name: 'SMU', age: 7}); // 'SMU' 출력  
```
