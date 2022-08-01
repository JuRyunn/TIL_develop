### Gwei
- 가스단위를 의미한다.
- SmartContract를 사용할 때 지불하는 금액이다.
- 개발자가 SmartContract를 어떻게 작성했는지에 따라 가스비용이 달라진다. (코드가 길수록 비싼 가스비용, 적을수록 낮은 가스비용)

### Ether
- 1 ether= 10^18 wei = 10&9 Gwei
- 0.01 ether= 10^16wei

<Br>
  
```solidity
pragma solidity >= 0.7.0 < 0.9.0;
contract lec3 {

    uint256 public value= 1 ether;
    uint256 public value2= 1 wei;
    uint256 public value3= 1 gwei;

}                       
```
![image](https://user-images.githubusercontent.com/79950504/182095162-1ed49199-794c-4b50-bc94-b14d462e2ea9.png)
