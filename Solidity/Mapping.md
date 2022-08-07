## Mapping
- 특정한 키값을 정의하고 대응되는 value 값을 반환 받을 수 있도록 해준다.
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
