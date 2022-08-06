## Inheritance
- 부모 클래스의 변수/메소드를 자식 클래스가 물려받아 그대로 사용 가능하게 하는 것을 의미한다.
```Solidity
contract Father {
  string public familyName= "PO";
  string public givenName= "KEMON";
  uint256 public money= 68000;
  
  function getFamilyName() view public returns(string memory) {
    return familyName;
  }
   
   function givenName() view public returns(string memory) {
    return givenName;
  }
  
   function getMoney() view public returns(uint256) {
    return money;
  }
}

contract Son is Father ("DIGIMON"){ // is 뒤에 상속 받고자 하는 contract의 이름을 선언한다
  
}
```

## Overriding
- 상위 클래스에서 가지고 있는 메소드를 하위 클래스에서 메소드에 재정의해 사용할 수 있는것을 의미한다. (= 덮어쓰기)
```Solidity
contract Father {
  uint256 public money= 68000;
  
   function getMoney() view virtual public returns(uint256) {
   // function getMoney() view  public virtual returns(uint256)
   // overriding 필요한 부분에 virtual을 써준다.
   return money;
  } 
}

contract Son is Father("DIGIMON") {
  uint256 public earning= 0;
  
  function work() public {
    earning += 100;
  }
  
  function getMoney() view public override returns(uint256) {
  // virtual과 override를 반드시 사용해야 overridng이 됐음을 solidity에게 알려줄 수 있다.
    
    return money+earning;
  }
}
```
