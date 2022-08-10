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
