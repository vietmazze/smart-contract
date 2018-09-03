# Crypto Zombie


### Types of Data: 
1. Struct
2. Arrays
3. Mappings: A key value store for storing and looking up data. 
  - `mapping (address => uint) public accountBalance;`  the key is an address and the value is a uint
  - `mapping (uint => address) favoriteNumber;`
  - `function setMyNumber(uint _myNumber) public {`
  - `// Update our `favoriteNumber` mapping to store `_myNumber` under `msg.sender``
  - `favoriteNumber[msg.sender] = _myNumber;`
  - `// ^ The syntax for storing data in a mapping is just like with arrays`
 4. Inheritance: Use to split your contracts/ code logic into pieces and connect them together.
 - `contract Doge {}` 
 - `contract BabyDoge is Doge{}` 
 - This implies that BabyDoge will run all the functions of Doge before itself.
  

### Global Variables: 
- msg.sender: Refers to the address of the person, who called the current function. 
- require: Makes it so that the function will throw an error and stop executing if some condition is not true.
      - `require(zombieOwner[msg.sender] == 0;`

### Typecasting: 
- Convert between data types by adding the casting wanted in front.
- `uint8 c - a * uint(b)`

### Calling a function inside a function:

`function _createZombie(string _name, uint _dna) private {`
       ` zombies.push(Zombie(_name, _dna));`
  `  } `

   ` function _generateRandomDna(string _str) private view returns (uint) {`
   `     uint rand = uint(keccak256(_str));`
        `return rand % dnaModulus;`
  `  }`

  `  function createRandomZombie(string _name) public {`
  `      uint randDna= _generateRandomDna(_name);`
     `   _createZombie(_name,_randDna);``
  `  }`

### Events:  
- are a way for your contract to communicate that something happened on the blockchain to your app front-end, which can be 'listening' for certain events and take action when they happen.
- Declare an event `event NewZombie( uint zombieId, string name, uint dna);`
- Then inside a function you want your front end to show/update, "fire" the event inside
- ` function _createZombie(string _name, uint _dna) private {`
- ` uint id = zombies.push(Zombie(_name, _dna)) - 1;` This is use, to record the id of the Zombie by using array's typical ID 
- ` NewZombie(id, _name, _dna);` This fires the event to JS front end


###


