## Balance
- 0xAb8483F64d9C6d1EcF9b849Ae677dD3315835cb2.balance와 같은 형태로 사용한다.
- 해당 특정 주소의 현재 가지고 있는 ETH 잔액을 나타낸다.

## msg.sender
- SmartContract를 사용하는 주체이다.

<br>

#### Balance & msg.sender Example
```solidity
contract BalanceMsgExam {
    
    event SendInfo(address _msgSender, uint256 _currentValue);
    event MyCurrentValue(address _msgSender, uint256 _value);
    event CurrentValueOfSomeone(address _msgSender, address _to,uint256 _value);
   
    function sendEther(address payable _to) public payable {
        require(msg.sender.balance>=msg.value, "Your balance is not enough");
        _to.transfer(msg.value); // transfer를 통해 ETH 전송
        emit SendInfo(msg.sender,(msg.sender).balance); // msg.snder 주소를 가지고 있는 잔액을 알 수 있음
    }
    
    function checkValueNow() public {
        emit MyCurrentValue(msg.sender, msg.sender.balance);
    }
    
    function checkUserMoney(address _to) public {
        emit CurrentValueOfSomeone(msg.sender,_to ,_to.balance);
    }  
}
```
![image](https://user-images.githubusercontent.com/79950504/183672992-b4600d03-7e69-4545-9e10-828fb09fe7f1.png)

<br>

#### msg.sender 응용
```solidity
contract BalanceMsgExam {
    
    address owner;
    
    // smartcontract이 배포되는 경우 가장 먼저 실행되며 payable을 생성자에 삽입한다.
    constructor() payable {
        owner= msg.sender; // 배포한 주소를 owner에 삽입
    }
    
    // owner address만이 아래 모든 함수(SendInfo, sendEther, checkValueNow, checkUserMoney)를 사용할 수 있다.
    modifier onlyOwner {
        require(msg.sender == owner, "Only owner");
        _;
    }
    
    event SendInfo(address _msgSender, uint256 _currentValue);
    event MyCurrentValue(address _msgSender, uint256 _value);
    event CurrentValueOfSomeone(address _msgSender, address _to,uint256 _value);
   
    function sendEther(address payable _to) public payable {
        require(msg.sender == owner, "only owner"); // owner address만 sendEther() 함수 사용이 가능하다.
        require(msg.sender.balance>=msg.value, "Your balance is not enough");
        _to.transfer(msg.value); // transfer를 통해 ETH 전송
        emit SendInfo(msg.sender,(msg.sender).balance); // msg.snder 주소를 가지고 있는 잔액을 알 수 있음
    }
    
    function checkValueNow() public {
        emit MyCurrentValue(msg.sender, msg.sender.balance);
    }
    
    function checkUserMoney(address _to) public {
        emit CurrentValueOfSomeone(msg.sender,_to ,_to.balance);
    }  
}
```

