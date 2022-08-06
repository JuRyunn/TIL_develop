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

<br>


## Index
- event 내에서만 사용 가능한 키워드로 특정한 event의 값들을 가져올 때 사용한다.
```solidity
contract IndexExample {
  
  event numberTracker(uint256 num, string str);
  event numberTracker2(uint256 indexed num, string str); // indexed를 통해 특정 이벤트 값을 가져올 수 있다.
  
  uint256 num= 0;
  function PushEvent(string memory _str) public {
    emit numberTracker(num, _str);
    emit numberTracker2(num, _str);
    num ++;
  }
}
```

<br>

## Super
- 함수를 오버라이딩 할 때 사용하며 원래의 함수를 가져온다.
```solidity
contract Father {
  event FatherName(string name);
  
  // Example: who() function이 엄청나게 길다고 가정했을 경우 하나하나 써주는것은 불가능하다.
  function who() public virtual {
    emit FatherName("ALEX");
    //emit fatherName("ALEX2");
    //emit fatherName("ALEX3");
    //emit fatherName("ALEX4");
    //emit fatherName("ALEX5");
    // ...
  }
}

contract Son is Father {
  event sonName(string name);
  function who() public override { // who() function을 Father로부터 상속받음
    super.who(); // super를 사용하여 FatherName 전체를 쉽게 가져올 수 있다.
    emit FatherName("ALEX");
  }
}
```  
![image](https://user-images.githubusercontent.com/79950504/183257938-109badd8-c078-4a23-95be-4aa7ffed291f.png)
- 2개의 event가 출력된것을 확인할 수 있다.

<br>

## 상속의 순서
- 맨 오른쪽(예: Father)부터 super를 통해 상속이 진행된다.
```solidity
contract Father {
  event FatherName(string name);
  function who() public virtual {
    emit FatherName("ALEX");
  }
}

contract Mother {
  event MotherName(string name);
  function who() public virtual {
    emit MotherName("Alice");
  }
}

contract Son is Father, Mother {
  function who() public override(Father, Mother) {
    super.who(); // Father, Mother의 who()를 오버라이딩한 형태에서 super를 통해 가져온다.
  }
}
```
![image](https://user-images.githubusercontent.com/79950504/183258232-64cec7ab-4730-4004-8563-17336cff55da.png)



