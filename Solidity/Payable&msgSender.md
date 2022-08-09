## Payable
- 이더, 토큰과 상호작용 시 필요한 키워드 (= send, transfer, call을 이용하여 이더를 보낼 때 payable이 필요)
- 주로 함수, 주소, 생성자에 붙여 사용한다.

<br>

## msg.sender
- 송금한 코인의 값을 의미한다.

<br>

## 이더를 보내는 방법
#### send
- 2300 gas 소비, 성공 여부를 true/false로 return 한다.
#### transfer
- 2300 gas 소비, 실패 시 에러를 발생시킨다.
#### call 
- 가변적인 gas 소비 (gas 값 지정 가능), 성공 여부를 true/false로 return 한다.
- 재진입 공격 위험성 존재.
