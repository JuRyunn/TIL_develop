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

<br>

#### 외부 SmartContract 함수를 부를 경우 try/catch
```solidity
contract math {
    
    // dividion: 256 함수를 받고 나눈다.
    function division(uint256 _num1,uint256 _num2) public pure returns (uint256) {
        require(_num1<10,"num1 shoud not be more than 10");
        return _num1/_num2;
    }
}

contract runner { // Math contract의 division 함수를 호출
    event catchErr(string _name,string _err);
    event catchPanic(string _name,uint256 _err);
    event catchLowLevelErr(string _name,bytes _err);
 
    // instance
    math public mathInstance = new math() ;
    
    function playTryCatch(uint256 _num1, uint256 _num2) public returns(uint256,bool){
        
        try mathInstance.division(_num1, _num2) returns(uint256 value){
            return(value,true);
        } catch Error(string memory _err) {
            emit catchErr("revert/require",_err);
            return(0,false);
        } catch Panic(uint256 _errorCode) {
            emit catchPanic("assertError/Panic",_errorCode);
            return(0,false);
        } catch (bytes memory _errorCode) {
            emit catchLowLevelErr("LowlevelError",_errorCode);
            return(0,false);
        }       
    } 
}
```

<br>

#### 외부 SmartContract을 생성할 경우 try/catch
```solidity
contract character {
    string private name;
    uint256 private power;
    constructor(string memory _name, uint256 _power) {
        name = _name;
        power = _power;
    }
}

contract runner {
    event catchOnly(string _name,string _err);
    function playTryCatch(string memory _name, uint256 _power) public returns(bool successOrFail) {
        
        try new character(_name,_power) {
            return(true);
        }
        catch {
            emit catchOnly("catch","ErrorS!!");
            return(false);
        }   
    } 
}
```

<br>

#### 내부 SmartContract에서 함수를 호출할 경우 try/catch
- 내부에서 try/catch를 사용하기 위해서는 this문이 필수적이다.
```solidity
contract runner2 {
    function simple() public returns(uint256) {
        return 4;
    }
    
    event catchOnly(string _name,string _err);
    function playTryCatch() public returns(uint256,bool) {
        
        try this.simple() returns(uint256 _value) {
        // this는 현재 smartContract를 나타냄.
        // this.simple() = SmartContract의 simple 함수
        
            return(_value,true);
        }
        catch {
            emit catchOnly("catch","ErrorS!!");
            return(0,false);
        }   
    } 
}
```

<br>

#### 함수 return 값 변수 명시
- return 값 변수를 명시해주면 변수가 여러개일 때 어떤 변수인지 기억하기 편리하다.
```solidity
contract returnExam {
    function add(uint256 _num1, uint256 _num2) public pure returns (uint256) { // return명 없음
       uint256 total= _num1 + _num2;
       return total;
    }
    
    function add2 (uint256 _num1, uint256 _num2) public pure returns (uint256 total) { // return명 정의 : total
        total= _num1 + _num2; // return 명이 있다면,  total 변수 명을 새로 명시할 필요가 없다.
        return total;
    }
 }
        
```

## Modifier
- ErrorHandler require와 함께 사용된다.
- module과 같이 여러 함수에 한번에 적용이 가능하다.
```solidity
contract modifierExam {
  
  // modifier 정의: modifier 이름 
  // 파라미터 값이 없을때 ()를 사용하지 않고 다음과 같이 쓰기도한다.
  modifier onlyAdults { 
    revert ("You are not allowed to pay for the cigarette");
    _; // BuyCigarette() 함수가 어디에 적용이 되는지 확인
  }
  
  function BuyCigarette() public onlyAdults returns(string memory) {
    return "your payment is success";
  }
  
  // modifier가 파라미터 값을 받는 경우
  // 위의 구문들과는 다르게 파라미터 값(_age)이 존재한다.
  modifier onlyAdults2(uint256 _age) {
    require (_age>18, "You are not allowed to pay for the cigarette");
    _;
  }
  
  function BuyCigarette2(uint256 _age) public onlyAdults2(_age) returns(string memory) {
    return "You payment is success";
  }
  
  uint256 public num= 5;
  modifier numChange {
    _; // function numChangeFunction() {...} 구문과 같음
    num= 10;
  }
  
  // modifier (numChange) 적용
  function numChangeFunction() public numChange {
    num= 15;
    // _; 때문에 num= 10  
   }
 }
```


