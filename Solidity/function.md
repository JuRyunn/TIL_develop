## 함수 정의하기
```solidity
function 이름() public { 
  // public, private, internal, external 사용 가능
  // 내용
}
```

#### Parameter와 return 값이 없는 function 정의
```solidity
uint256 public a= 3;
function changeA1() public {
  a= 5;
}
```


#### Parameter는 없고 return 값이 있는 function 정의
```solidity
function changeA2(uint256 _value) public {
  a= _value;
}
```

#### Parameter, retrun 둘 다 있는 function 정의
```solidity
function changeA3(uint256 _value_ returns(uint256) {
  a= _value;
  return a;
}
```

<br>

## 접근제한자
#### public
```solidity
contract public_example {
  uint256 public a=3;
  
  function changeA(uint256 _value) public {
    a= _value;
  }
  
  function get_a() view public returns (uint256) {
    return a;
  }
}

contract public example_2 {
  public_example instance= new publiC_example(); 
  // public_example에 접근하기 위해 instance화 사용
  
  function changeA2(uint256 _value) public {
    instance.changeA2(_value);
  }
  
  function use_public_example_a() view public returns (uint256) {
    return instance.get_a();
  }
}
```
- 모든 곳에서 접근이 가능하다.


#### external
- public처럼 모든 곳에서 접근이 가능하지만 external이 정의된 자기 자신 contract 내에서 접근이 불가능하다.
```solidity
contract public_example {
  uint256 public a=3;
  
  function changeA(uint256 _value) external {
    a= _value;
  }
  
  function get_a() view external returns (uint256) {
    return a;
  }
}

contract public example_2 {
  public_example instance= new publiC_example(); 
  // public_example에 접근하기 위해 instance화 사용
  
  function changeA2(uint256 _value) public {
    instance.changeA2(_value);
  }
  
  function use_public_example_a() view public returns (uint256) {
    return instance.get_a();
  }
}
```

#### private
- 오직 private이 정의된 자기 contract에서만 가능하다 (private이 정의된 contract를 상속 받은 자식도 불가능)
```solidity
string private a2= 5;
```

#### internal
- private처럼 오직 internal이 정의된 자기 contract에서만 가능하고 internal이 정의된 contract를 상속한다.
- 상속받은 contract가 있을 때 internal에 정의된 contract에 접근이 가능하다.

