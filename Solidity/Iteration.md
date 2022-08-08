### 반복문

## for
```solidity
for (초기값; 값이 얼마나 forloop를 돌아야 하는지; forloop 한번 돌 때마다 값의 변화) {
  // forloop 내용
}
```
```solidity
event CountryIndexName(uint256 indexed _index, string _name);
string[] private countryList= ["Korea", "USA", "JAPAN"];

function forLoopEvents() public {
  for(uint256 i= 0; i<countryList.Length; i++) {
    emit CountryIndexName(i, countryList[i]); // i= 배열의 index 값
  }
}
```

<br>

## while
```solidity
while (값이 얼마나 while loop 돌아야 하는지) {
  // whileloop 내용
  // whileloop 한번 돌 때마다 값의 변화;
}
```

```solidity
function whileLoopEvents() public {
  uint256 i= 0;
  while (i < countryList.Length) {
    emit CountryIndexName(i, countryList[i]);
    i++;
  }
}
```

<br>

## do while
```solidity
do { 
  // dowhileloop 내용
} while (값이 얼마나 do while loop를 돌아야 하는지)
```

```solidity
function doWhileLoopEvents() public {
  uint256 i= 0;
  do {
    emit CountryIndexName(i, countryList[i]);
    i++;
    }
  while(i<countryList.length);
  }
}

```
<br>

## Continue
- 다음 반복문으로 이동시킨다.
```solidity
event CountryIndexName(uint256 indexed _index, string _name);
string[] private countryList= ["KOREA", "USA", "JAPAN"];

function useCountinue() public {
  for(uint256 i= 0; i<countryList.length; i++) {
    if(i%2==1) { // 홀수일 때 
      continue; // countinue 실행
      }
        emit CountryIndexName(i, countryList[i]);
    }
  }
}
```

<br>

## Break
- 반복문을 끝낸다.
```solidity
function useBreak() public {
  for(uint256 i=0; i<countryList.length; i++) {
    if(i == 2) {
      break;
      }
      emit CountryIndexName(i, countryList[i]);
    }
  }
}
```

<br>

## Linear search
![image](https://user-images.githubusercontent.com/79950504/183356316-f2a069a2-6665-4859-a565-df9d5e590968.png)
- 배열에서 search를 해야함 > 특정한 값을 입력받아 해당 배열 안의 값을 검색한다 > search 값으로 6을 입력받고 for loop은 index 0 부터 시작해 값을 하나하나 비교하여 찾는다.
- Search 값을 10으로 입력한다면 해당 배열에 그 값이 없기 때문에, 값이 나오지않으며 return된다.
```solidity
contract linearSearchExam {
    string[] private countryList = ["Korea", "USA", "JAPAN"];
    
    function linearSearch(string memory _search) public view returns(int256,string memory) {
        
        for(uint256 i=0; i<countryList.length; i++) {
        // solidity 내에선 string과 string을 비교하기 위해선
        // string을 byte화 시켜 변환 -> 내장함수를 이용해 Hash화 시켜야한다.
        // └> 값이 같으면 똑같은 Hash가 나온다. (값이 틀리면 return으로 나간다)
            if(keccak256(bytes(countryList[i])) == keccak256(bytes(_search))) {
                return (i,countryList[i]);
            }
        }
        
        return(99,"Nothing");
    }
}
```

