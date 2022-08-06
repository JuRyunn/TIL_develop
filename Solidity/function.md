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

<br>

## 접근제한자2
#### view
- function 밖의 변수들을 읽을 수 있으며 변경이 불가능함.
```solidity
uint256 public a= 1;

function read_a() public view returns(uint256) {
  return a+2;
  }
}
```


#### pure
- function 밖의 변수들을 읽지 못하고 변경 또한 불가능함.  
```solidity
uint256 public a= 1;

function read_a2() public pure returns(uint256) {
  uint b= 1;
  return 3+2+b;
```

#### view와 pure 둘 다 명시가 되지 않았을 경우
-  function 밖의 변수를 읽어 변경해야함.
``` solidity
function read_a3() public returns(uint256) {
  a= 13;
  return a;
  // a 값을 읽어왔고 변경하기 때문에 view, pure의 사용이 불가능하다.
}
```

<br>

## Solidity의 4가지 영역
#### storage
- 대부분의 변수, 함수들이 저장되며 영속적으로 저장이되며 가스 비용이 비싸다.

#### memory
- 함수의 파라미터, 리턴값, 레퍼런스 타입이 주로 저장되지만 stroage처럼 영속적이지 않고 함수 내에서만 유효하기 때문에 가스 비용이 저렴하다.

#### colldate
- 주로 external function의 파라메터에서 사용한다.

#### stack
- EVM (Ethereum Virtual Machine)에서 stack data를 관리할 때 쓰는 영역이며 1024mb로 제한적이다.
