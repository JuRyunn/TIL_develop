## Modifier
- ErrorHandler require와 함께 사용된다.
- module과 같이 여러 함수에 한번에 적용이 가능하다.
```solidity
contract modifierExam {
  
  // modifier 정의: modifier 이름 
  // 파라미터 값이 없을때 ()를 사용하지 않고 다음과 같이 쓰기도한다.
  modifier onlyAdults { 
    revert ("You are not allowed to pay for the cigarette");
    _; // BuyCigarette() 함수가 어디에 적용이 되는지 확인
  }
  
  function BuyCigarette() public onlyAdults returns(string memory) {
    return "your payment is success";
  }
  
  // modifier가 파라미터 값을 받는 경우
  // 위의 구문들과는 다르게 파라미터 값(_age)이 존재한다.
  modifier onlyAdults2(uint256 _age) {
    require (_age>18, "You are not allowed to pay for the cigarette");
    _;
  }
  
  function BuyCigarette2(uint256 _age) public onlyAdults2(_age) returns(string memory) {
    return "You payment is success";
  }
  
  uint256 public num= 5;
  modifier numChange {
    _; // function numChangeFunction() {...} 구문과 같음
    num= 10;
  }
  
  // modifier (numChange) 적용
  function numChangeFunction() public numChange {
    num= 15;
    // _; 때문에 num= 10  
   }
 }
```
