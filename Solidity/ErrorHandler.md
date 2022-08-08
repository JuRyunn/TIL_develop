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

