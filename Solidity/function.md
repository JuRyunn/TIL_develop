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
- 모든 곳에서 접근이 가능하다.

#### external
- public처럼 모든 곳에서 접근이 가능하지만 external이 정의된 자기 자신 contract 내에서 접근이 불가능하다.

#### private
- 오직 private이 정의된 자기 contract에서만 가능하다 (private이 정의된 contract를 상속 받은 자식도 불가능)

#### internal
- private처럼 오직 internal이 정의된 자기 contract에서만 가능하고 internal이 정의된 contract를 상속한다.

