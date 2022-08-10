## fallback
- 대비책 함수이며 이름이 없는 무기명 함수이다.
- external을 필수로 사용하며 payable을 붙여줘야한다.
- SmartContract가 ETH를 받을 수 있도록 한다.
- ETH를 받고 난 후 어떠한 행동을 취하도록 할 수 있다.
- call 함수로 없는 함수가 호출될 경우 어떠한 행동을 취하게 할 수 있다.


#### 0.6ver 이하 fallback
 - SmartContract에게 ETH를 받을 수 있는 기능을 부여하기 때문에 payable 사용
 - 외부에서 ETH를 보내기 때문에 external 사용
```solidity
function() external payable {...}
```



#### 0.6ver 이상 fallback
- 해당 버전에선 receive, fallback으로 나뉜다.
- receive: 순수하게 ETH를 받을 경우 작동한다.
- fallback: 함수를 실행하면서 ETH를 전송할 때, 호출된 함수가 없을 때 작동한다.
```solidity
// 기본형: 호출된 함수가 특정 SmartContract이 없을 때 fallback 함수가 발동.
fallback() external {...} //payable을 써주지 않는다. receive에서 해당 기능이 있기 때문.

// payable 적용 시 : 이더를 받고 나서도 fallback 함수가 발동.
fallback() external payable {...} // payalbe을 씀으로써 ETH를 받고 함수를 실행할 수 있음.


receive() external payable {...} // ETH를 받고 난 후 행동.
```

```solidity

```
