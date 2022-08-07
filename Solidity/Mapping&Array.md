## Mapping
- 특정한 키값을 정의하고 대응되는 value 값을 반환 받을 수 있도록 해준다.
- Length 기능은 없다.
```solidity
contract MappingExam {
   // (키값 / Value 값의 type) 
   mapping(uint256 => uint256) private ageList; // ageList: mapping명
   mapping(string => uint256) private priceList;
   mapping(uint256 => string) private nameList;
   
   function setAgeList(uint256 _index, uint256 _age) public {
    ageList[_index]= _age;
  }
  
    function getAge(uint256 _index) public view returns(uint256) {
      return ageList[_index];
    }
      
    function setNameList(uint256 _index, string memory _name) public {
      nameList[_index]= _name;
    }
    
    function setPriceList(string memory _itemList, uint256, price) public {
      priceList[_itemName]= _price;
    }
    
    function getPriceList(uint256 _index) public view returns(uint256) {
      return priceList[_index];
    }     
}
```

<br>

## Array
- 배열 내 값들을 추가, 삭제, 길이를 구할 수 있다.
- 배열의 장점 중 하나는 배열 내 값들을 한번씩 순회할 수 있다 => 하지만 Ddos 공격에 취약하다. (특정 배열을 악의적으로 무한반복 시키면, 가스비용과 ETH 네워크가 과부화 되기 때문)
```Solidity
contract ArrayExam {
   
   // 배열의 타입 , [] , 접근제한자 , 배열명 기제
   uint256[] public ageArray;
   
   // 배열 사전 정의 방법 | Length: 3
   string[] public nameArray= ["A", "B", "C"];
   
   function AgeLength() public view returns(uint256) {
      return ageArray.length;
   }

   // ex: 최초의 값 삽입 0 -> 50 | 1 -> 70 | Length: 2
   function AgePush(uint256 _age) public {
      ageArray.push(_age);
   }

   // 1 -> 70 | uint256= 70
   function AgeGet(uint256 _index) public view returns(uint256) {
      return ageArray[_index];
   }

   // 0 -> 50 | Length: 1
   // pop을 사용하면 제일 최신 값이 지워진다 ->  배열의 값이 줄어든다.
   function AgePop() public {
      ageArray.pop();
   }
   
   // 0 -> 0 | 1 -> 70 | Length: 2
   // delete를 사용하면 원하는 index 값을 넣어 지우는 것이 가능하지만 
   // 완전히 지워지는 것이 아니라 0으로 채워지는 것이고 Length는 그대로다.
   function AgePop(uint256 _index) public {
      delete ageArray[_index];
   }
   
   // 0 -> 90 | 1 -> 70 | Length: 2 
   function AgeChange(uint256 _index, uint256 _age) public {
      ageArray[_index]= _age;
   }
}
```

<br>

## Mapping & Array 주의점
```solidity
contract lec19{
   uint256 num = 89;
   mapping(uint256 => uint256) numMap;
   uint256[] numArray;
   
   function changeNum(uint256 _num) public{
       num = _num;
   }
   function showNum() public view returns(uint256){
      return num;
   }
   
   function numMapAdd() public{
       numMap[0] = num;
   }
   function showNumMap() public view returns(uint256){
       return numMap[0];
   }
   function UpdateMap() public{
       numMap[0] = num;
   }
   
   function numArrayAdd() public{
       numArray.push(num);
   }
   function showNumArray() public view returns(uint256){
       return numArray[0];
   }
   function updateArray() public {
       numArray[0] = num;
   }   
}
```
![image](https://user-images.githubusercontent.com/79950504/183281919-cd29cd10-4b29-4ca4-86e5-b3ebc07f1775.png)
- Mapping과 Array는 Reference Type으로 저장하는 것이 아니라 당시의 값을 캡처해 그것을 저장하기 때문에 Num값을 변경해도 업데이트가 되지 않는 것이다
- 변경된 값은 따로 업데이트 해주어야한다. ( = numMapAdd, update Array 참고 )
