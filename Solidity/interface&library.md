## interface
- SmartContract 내에서 정의되어야할 필요한 것을 의미한다.
- 함수는 external로 표시한다.
- enum, structs 사용이 가능하다.
- 변수, 생성자 사용이 불가능하다.
```solidity
interface ItemInfo {
    struct item {
        string name;
        uint256 price;
    }
    
    // 무조건 external을 써줘야한다.
    // 파라미터 값을 써줘야한다.
    function addItemInfo(string memory _name,uint256 _price) external;
    function getItemInfo(uint256 _index) external view returns(item memory);
}

contract interfaceExam is ItemInfo { // interfaceExam SmartContract는 is를 통해 interface 적용받음.
    item[] public itemList;
    uint256[] public a;
    
    // 함수명 (= addItemInfo)과 return 값을 필수로 써줘야한다. 
    // 함수를 정의할땐 override를 써줘야한다.
    function addItemInfo(string memory _name,uint256 _price) override public {
        itemList.push(item(_name,_price));
    }
    function getItemInfo(uint256 _index) override public view returns(item memory) {
        return itemList[_index];
    }
}
```

<br>

## library
- 기존에 만들던 SmartContract와 다른 종류의 SmartContract이다.

#### 장점
- 재사용: 블록체인에 라이브러리가 배포되면, 다른 SmartContract에 적용이 가능하다.
- 가스 소비 절약: 여러개의 SmartContract에서 공통으로 쓰이는 코드를 따로 라이브러리를 통해 배포하기 때문에 다른 SmartContract에 명시해주는 것이 아니라 라이브러리를 적용만 하면 되기 때문에 가스비가 절약된다.
- 데이터 타입 적용: 라이브러리의 기능들은 데이터 타입에 적용이 가능하기 때문에 조금 더 쉽게 사용할 수 있다.

#### 단점
- fallback 함수를 라이브러리 내에 정의하지 못하기 때문에 ETH를 가지고 있을 수 없다.
- payable 함수 정의가 불가능하다.
- 상속이 불가능하다


