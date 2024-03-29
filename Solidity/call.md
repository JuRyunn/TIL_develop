## call
- Low level 함수.
- ETH 송금이 가능.
- 외부 SmartContract 함수 호출 가능.
- 가변적인 gas 소비 가능.
- re entrancy (재진입) 공격위험성이 있기 때문에 Checks_Effects_Interactions_pattern 사용.

```solidity
contract callExam {
  event JustFallback(string _str);
  event JustReceive(string _str);
  
  function addNumber(uint256 _num1, uint256 _num2) public pure returns(uint256) {
    return _num1 + _num2;
  }

  // 없는 함수를 호출할 경우 작동
  fallback() external {
    emit JustFallback("JustFallback is Called");
  }

  // SmartContract에서 ETH를 받을 수 있도록 한다.
  receive() external payable {
    emit JustReceive("JustReceive is Called");
  }
}

contract callExam2 {
  event calledFunction(bool1 _success, bytes _output);
  
  // 송금하기
  function transferETH(address payable _to) public payable {
    (bool success, )= _to.call{value: msg.value}("");
    require(success, "Failed to transfer ETH");
}

  // 외부 SmartContract 함수 호출
  function callMethond(address _contractAddr, uint256 _num1, uint256 _num2) public {
    
    // _num1+_num2; 가 byte화 되어 return 된다.
    // true, false & num1 + num2 값이 나온다.
    (bool success, bytes memory outputFromCalledFunction)= _contractAddr.call(
      abi.encodeWithSignature("addNumber(uint256, uint256)", _num1, _num2));
     
     require(sucess, "Failed to transfer ETH");
     emit calledFuction(success, outputFromCalledFunction);
  }
}
```
![image](https://user-images.githubusercontent.com/79950504/183799923-60aa056b-0c87-4103-b9b2-d3adcd449a86.png)
- 12와 3을 삽입하였을 경우 f가 출력된다 (16진수는0~f까지, 15번째 자리에 f가 써있는 것.) 

<br>

## ABI
- ETH 환경 내에서 SmartContract을 상호작용 시키는 표준방법.
- 데이터가 코드화 되어있으며, 설명이 되어있다.
- abi object 내에는 encodedWithSignature() 메소드가 있으며 해당 메소드로 외부 SmartContract의 함수를 호출한다.
![image](https://user-images.githubusercontent.com/79950504/183800809-765c581f-9cc9-495d-90d7-09a07c67d42e.png)

<br>

## Delegate Call
- msg.sender가 본래의 SmartContract 사용자를 나타낸다.
- delegate call이 정의된 SmartContract (=caller)이 외부 Contract의 함수들을 마치 자신인것 처럼 사용한다. (실질적인 값 또한 caller에 저장)
- 외부 SmartContract 그리고 caller SmartContract는 같은 변수를 가져야한다.

#### call
![image](https://user-images.githubusercontent.com/79950504/183897578-7065fa40-9219-4c15-8ec2-5502ac56d91a.png)

#### delegate call
![image](https://user-images.githubusercontent.com/79950504/183899752-c81da747-5662-4d94-a5b7-374a15824c5e.png)


#### Example
```solidity
contract add {
  uint256 public num= 0;
  event Info(address _addr, uint256 _num);
  
  function plusOne() public {
    num= num + 1;
    emit Info(msg.sender, num);
  }
}

contract caller {
  uint256 public num= 0;
  
  function callNow(address _contractAddr) public payable {
    (bool success, )= _contractAddr.call(abi.encodeWithSignature("plusOne()"));
    require(success, "Failed to transfer ETH");
  }
  
  function delcateCallNow(address _contractAddr) public payable {
    (bool success, )= _contractAddr.delegatecall(abi.encodeWithSignature("pluseOne()"));
    require(success, "Failed to transfer ETH");
  }
} 
```



