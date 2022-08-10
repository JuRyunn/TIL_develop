## fallback
- 대비책 함수이며 이름이 없는 무기명 함수이다.
- external을 필수로 사용하며 payable을 붙여줘야한다.
- SmartContract가 ETH를 받을 수 있도록 한다.
- ETH를 받고 난 후 어떠한 행동을 취하도록 할 수 있다.
- call 함수로 없는 함수가 호출될 경우 어떠한 행동을 취하게 할 수 있다.


#### 0.6ver 이하 fallback
```solidity
  // SmartContract에게 ETH를 받을 수 있는 기능을 부여하기 때문에 payable 사용
  // 외부에서 ETH를 보내기 때문에 external 사용
  function() external payable {...}
```



#### 0.6ver 이상 fallback
