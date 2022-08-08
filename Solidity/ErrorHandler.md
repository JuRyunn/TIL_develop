## Error Handler
- require: 특정한 조건에 부합하지 않으면 에러를 발생시키며 gas를 환불해준다.
- revert: 조건 없이 에러를 발생시키고 gas를 환불해준다.
- assert: gas를 전부 소비한 후 특정한 조건에 부합하지 않으면 에러를 발생시킨다.
- try/catch

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

```
![image](https://user-images.githubusercontent.com/79950504/183361852-788c1610-9fa1-4637-8851-03034fbc9a5c.png)
- asset와 revert의 gas값 차이.

<br>

