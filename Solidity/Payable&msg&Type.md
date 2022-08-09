## Payable
- 이더, 토큰과 상호작용 시 필요한 키워드 (= send, transfer, call을 이용하여 이더를 보낼 때 payable이 필요)
- 주로 함수, 주소, 생성자에 붙여 사용한다.

<br>

## msg.value
- 송금한 코인의 값을 의미한다.

<br>

## 이더 전송 방법
#### send
- 2300 gas 소비, 성공 여부를 true/false로 return 한다.
#### transfer
- 2300 gas 소비, 실패 시 에러를 발생(return) 시킨다.
#### call 
- 가변적인 gas 소비 (gas 값 지정 가능), 성공 여부를 true/false로 return 한다.
- 재진입 공격 위험성 존재.

<br>

#### ETH 전송 예제
```solidity
contract ETHSendExam {
  
  event howMuch(uint256 _value);
  
  // _to: ETH를 받을 주소, SmartContract 주소도 가능하다 (= SmartContract도 ETH를 받을 수 있다)
  // ETH 전송을 위한 코드이기 때문에 payable 키워드를 사용해야한다.
  
  // send 방식
  function sendNow(address payable _to) public payable {
    bool sent= _to.send(msg.value); // true 혹은 false return
    require(sent, "Failed to send ETH"); // false
    emit howMuch(msg.value); // true
  }
  
  // transfer 방식
  function transferNow(address payable _to) public payable {
    _to.transfer(msg.value); // transfer의 경우 require문과 다르게 명료하게 사용이 가능하다. (= error를 return)
    emit howMuch(msg.value); // true
  }
  
  // call 방식
  function callNow (address payable _to) public payable {
   
    // 0.7 ver 이하
    // (bool sent, ) = _to.call.gas(1000).value(msg.value)("");
    // require (sent, "Failed to send ETH");
    
    // 0.7 ver 이상
    (bool sent, ) = _to.call {value: msg.value, gas: 1000} ("");
    require(sent, "Failed to send ETH"); // false
    emit howMuch(msg.value); // true
  }
}
```
![image](https://user-images.githubusercontent.com/79950504/183629766-15546f53-2182-42e0-a5b3-ad62b25f0b1f.png)
- 위와 같은 방식으로 전송할 이더의 갯수를 기제해 ETH를 전송한다. (VALUE = msg.value= ETH)

![image](https://user-images.githubusercontent.com/79950504/183631620-73e10dc4-f772-426c-a917-15278bc0c309.png)
- ETH 전송


