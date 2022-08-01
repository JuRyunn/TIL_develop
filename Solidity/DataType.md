## Solidity
- DataType / ReferenceType / MappingType 총 세가지로 나뉜다.


##### DataType
- bool: true/false 두가지 값이 존재한다. 
```solidity
bool public b= false;
bool public b1= !false;
bool public b2= false || true;
bool public b3= false == true;
bool public b4= false && true;
```

<br>

- byte
```solidity
bytes4 public bt= 0x1234567;
bytes public bt2= "STRING";
```

<br>

- address: 이더를 송수신하는 계좌번호라고 생각하면된다. / SmartContract마다 배포될때 생성된다.  
```solidity
address public addr= 0x358AA13c52544ECCEF6B0ADD0f801012ADAD5eE3;
```
![image](https://user-images.githubusercontent.com/79950504/182088379-1a1e2068-2c25-4534-adb7-63e231f86d9e.png)

<br>

- int / uint: -가 있는지 없는지에 따라 차이가 발생한다.
