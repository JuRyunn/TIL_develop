### Module
- 문장을 내보내고 가져오는 모듈이라는 것은 JavaScript 파일 내에 있는 것으로 다른 파일에서 컨텐츠를 불러올 수 있고 JS 파일은 그 컨텐츠가 어디에서 온 것인지 알고 있다. 
- JavaScript에는 모듈 방식의 코드를 작성할 수 있는 기능이 존재해 여러개의 파일로 코드를 분할 할 수 있으며 코드를 여러개로 나누고 HTML 파일에 순서대로 코드를 가져오면 된다.

< br>

>> Example
#### person.js
```JavaScript
const person= {
  name: 'Max'
}
export default person
```
