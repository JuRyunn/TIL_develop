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
