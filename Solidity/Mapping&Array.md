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
- Mapping에선 길이를 구할 수 없지만 Array는 구할 수 있다.
- 배열의 장점 중 하나는 배열 내 값들을 한번씩 순회할 수 있다 => 하지만 Ddos 공격에 취약하다. (특정 배열을 악의적으로 무한반복 시키면, 가스비용과 ETH 네워크가 과부화 되기 때문)
```Solidity
contract ArrayExam {


}
```
