## If
- 특정 조건을 만들고 해당 조건이 발동될때 if 내의 내용을 실행해준다.
```solidity
// Case 1: if else
if (if가 발동되는 조건) {
  
} else { // if가 발동 안될 경우
  
}

// Case 2: if else if else
if (if가 발동되는 조건) {
  
} else if (else if가 발동되는 조건) {
  
}
else if { // if else if가 발동 안되면

}
```

```solidity
contract IfExam {

  string private outcome= "";
  
  function isIt5(uint256 _number) public returns (string memory) {
    if(_number == 5) {
      outcome= "Yes, it is 5";
      return outcome;
    }
   
   outcome= "No it is not 5";
   return outcome;
  }
}   
```
![image](https://user-images.githubusercontent.com/79950504/183348521-63a44a1c-efe4-4021-b606-383218b85473.png)  
![image](https://user-images.githubusercontent.com/79950504/183348472-b9516c94-ad87-4990-ad4e-bb366a5ed41b.png)

