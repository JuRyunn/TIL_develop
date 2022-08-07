## Struct [구조체]
- 나만의 Type을 만드는 것.
```Solidity
contract StructExam {
    
    // Character 구조체 생성 -> 내부의 값들을 입력해줘야 Character가 생성됨
    struct Character {
       uint256 age; 
       string name; 
       string job; 
    }
    
    mapping(uint256=>Character) public CharacterMapping;
    Character[] public CharacterArray;
    
    function createCharacter(uint256 _age,string memory _name,string memory _job) pure public returns(Character memory) {
        return Character(_age,_name,_job); // Character(파라미터 값) return
    }
    
    function createChracterMapping(uint256 _key, uint256 _age,string memory _name,string memory _job ) public {
       CharacterMapping[_key] = Character(_age,_name,_job);
    }
    
    function getChracterMapping(uint256 _key) public view returns(Character memory) {
       return CharacterMapping[_key];
    }
    
    function createChracterArray(uint256 _age,string memory _name,string memory _job ) public {
       CharacterArray.push(Character(_age,_name,_job));
    }
    
    function getChracterArray(uint256 _index) public view returns(Character memory) {
       return CharacterArray[_index];
    }
}
```
