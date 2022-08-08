## Error Handler
- require: 특정한 조건에 부합하지 않으면 에러를 발생시키며 gas를 환불해준다.
- revert: 조건 없이 에러를 발생시키고 gas를 환불해준다.
- assert: gas를 전부 소비한 후 특정한 조건에 부합하지 않으면 에러를 발생시킨다.

<br>

## Example
``` solidity
function assetNow() public pure { 
    // assert( 조건문 )을 써준다.
    assert(false); 
}

function revertNow() public pure {
    revert("error");
}

function requireNow() public pure {
    require(false, "occurred");
}
```
![image](https://user-images.githubusercontent.com/79950504/183363386-b2946f09-c23c-4eb8-865f-9b9cc3fcab79.png)
- asset와 revert/require의 gas값 차이.
- assert는 비효율적이기 때문에 test 용도로 사용한다.

<br>

## require, revert에 if 사용
```solidity
function onlyAdults(uint256 _age) public pure returns (string memory) {
    if(_age < 19) {
        revert ("You are not allowed to pay for the cigarette");
    }
    return "Your payment is success";
}

function onlyAudlts2(uint256 _age) public pure returns(string memory) {
    require(_age>19, "You are not allowed to pay for the cigarette);
    return "Your payment is success";
}
```

<br>

## Try, Catch
- assert, revert, require는 에러를 발생시키고 프로그램을 끝내지만 try/catch로 에러가 발생해도 프로그램을 종료 시키지 않고 대처 가능하게 만들 수 있다.
- try/catch문 내에서 assert, revert, require를 통해 에러가 발생하면 catch는 에러를 잡지 못하고 개발자가 의도한 것으로 알고 정상적으로 프로그램을 종료한다.
- try/catch문 밖에서 assert, revert, require를 통해 에러가 발생하면 catch는 에러를 잡고 에러를 핸들할 수 있다.
```solidity
catch Error(string memory reason) {...} // revert 혹은 require를 통해 생성된 에러 용도
catch Panic(uint errorCode) {...} // assert를 통해 생성된 에러가 발생할 때 catch에 의해 잡힘
```
