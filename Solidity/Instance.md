## Instance
- 하나의 contract에서 다른 contract으로 접근하기 위해 사용한다.
```solidity
contract A {
  uint256 public a= 5;
  
  function change(uint256 _value) public {
    a= _value;
    }
  }
}

contract B {
  A InstanceName = new A(); // 사용하고자하는 instance명을 명시해준다. 
  
  function get_A() public view returns(uint256) {
    return InstanceName.a();
  }
  
  function change_A(uint256 _value) public {
    InstanceName.change(_value);
  }
}
```
