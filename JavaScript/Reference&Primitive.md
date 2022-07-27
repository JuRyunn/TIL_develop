#### 기본형
```JavaScript
const number= 1; // Primitive Type (기본형)
const num2= number; // Reference Type (참조형)

console.log(num2); // 1 출력
```
- string, bool 등이 기본형 자료 타입이며 재할당하거나 변수를 다른 변수에 저장할 때 값을 복사한다. 객체와 배열은 참조형 자료 타입이다.


#### Example
![image](https://user-images.githubusercontent.com/79950504/181316755-4e0b1fef-4753-47a3-82df-47077beea3bf.png)
- 첫번째 person과 같은 값을 출력하는데, 이는 객체 person을 복사한 것이 아니다. (person은 메모리에 저장되어 있고 상수 person에는 메모리에 있는 주소를 가리키는 포인터를 저장한다)
- 이러한 이유로 person을 secondPerson에 할당하면 포인터가 복사되는 것이다.

![image](https://user-images.githubusercontent.com/79950504/181321912-4229b9be-71da-44dd-b516-dc851cae5c65.png)
- 'Max'가 아닌 'Manu'가 출력된 이유? : 단지 포인터를 복사했을 뿐이며 person이 가리키는 메모리에 존재하는 동일한 객체를 가리키기 때문이다.


![image](https://user-images.githubusercontent.com/79950504/181331572-274cabb0-482f-4ee9-87ad-6b482e2aa794.png)
- 스프레드: 객체로부터 프로퍼티와 프로퍼티의 값을 가져와 새롭게 생성한 객체에 추가한다. (중괄호를 써서 생성 가능) 
- 포인터가 아닌 진짜 복사본을 생성했기 때문에 'Manu'로 설정했지만 'Max'가 출력되는 것이다. 

<br>
<br>

※ 재할당한다면, 값이 아닌 "포인터를 할당"하는 것이다.
※ 진짜를 복사하고 싶다면 새로운 객체를 생성하여 전체 객체를 복사하는 것이 아닌 "프로퍼티를 복사"해야한다.
