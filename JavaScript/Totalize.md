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
