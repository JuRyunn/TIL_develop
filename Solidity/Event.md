## Event
- Solidity 내부엔 print문이 없기 때문에 event를 사용해 값을 출력한다.
- 출력한 값은 block에 저장되며 언제든 꺼내서 사용할 수 있다.
``` Solidity
contract eventExam {
  // event 정의 -> eventName -> (출력하고 싶은 값)
  event info(string name, uint256 money);
  
  function sendMoney() public {
    emit info("ALEX", 1000);
  }
}
```

![image](https://user-images.githubusercontent.com/79950504/183248121-dbb67a4f-13a7-41ca-9341-47c66602f98a.png)
- event info가 Block에 각인되었음을 알 수 있다.
- 언제든 info의 값을 가져와 사용이 가능하다.
