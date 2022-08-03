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
