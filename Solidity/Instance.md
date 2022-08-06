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

## Instance: constructor
- 변수의 값을 초기화 하는 경우 주로 사용하는 생성자이다.
- 처음 생성/배포/instance화 되는 경우 초기 변수 파라미터 값을 받고 SmartContract가 생성된다. 
- 가스를 많이 소비하지만, SmartContract가 가볍다면 사용해도 무관하다. 
- 비용적인 측면보단 블록에선 가스를 소비할 수 있는 양이 제한적이다. (제한하는 양을 초과한다면, ETH 내에서 에러가 발생하고 SmartContract를 배포할 수 없다)
```solidity
contract A {
  string public name;
  uint256 public age;
  
  constructor (string memory _name, uint256 _age) {
    name= _name;
    age= _age;
  }
  
  function change(string memory _name, uint256 _age) public {
    name= _name;
    age= _age;
  }
}

contract B {
  A instance= new A("Alice", 52);
  
  function change(string memory _name, uint256 _age) public {
    instance.change(_name, _age);
  }
  
  function get() public view returns(string memory uint256) {
    return (instance.name(), instance.age());
  }
}
```
