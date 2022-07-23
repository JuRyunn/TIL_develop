### Module
- 문장을 내보내고 가져오는 모듈이라는 것은 JavaScript 파일 내에 있는 것으로 다른 파일에서 컨텐츠를 불러올 수 있고 JS 파일은 그 컨텐츠가 어디에서 온 것인지 알고 있다. 
- JavaScript에는 모듈 방식의 코드를 작성할 수 있는 기능이 존재해 여러개의 파일로 코드를 분할 할 수 있으며 코드를 여러개로 나누고 HTML 파일에 순서대로 코드를 가져오면 된다.

<br>

> Example
#### person.js
```JavaScript
const person= {
  name: 'Max'
}

export default person
```
- 상수형의 person에는 JS 객체가 저장되어 있다.
- default 키워드를 통해 person을 내보낼 수 있다.
- default는 파일에서 어떤 것을 가져오면 항상 default export가 내보낸 것을 기본값으로 가져온다는 것을 의미한다 (=const person)

#### Utility.js
```JavaScript
export const clean= () => { ... }
export const baseData= 10;
```
- 상수형의 clean에는 함수가 들어있고 또 다른 baseData에는 숫자가 들어 있다.

#### app.js
```JavaScript
import person from './person.js'
import prs from './person.js'

import {baseData} from './utlity.js'
import {clean} from './utility.js'
// import {baseData, clean} 으로 한 문장에 사용 가능
```
- 위의 Person.js, Utlity.js에서 무엇인가를 가져오기 위해 "Import"문이 필요하다.
- Person.js에서 person을 import하면 원하는대로 객체의 이름을 지정할 수 있다.
- Utlity.js에서 두개의 다른 상수를 불러오는데 그 파일에서 특정한 것을 정확하게 가리키기 위해 {}를 사용한다 (= named export라고 부른다)
- 우리가 가리키려는 것을 정확하게 명시해야 JS가 알 수 있다.
