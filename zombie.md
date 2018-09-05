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
1. msg.sender: Refers to the address of the person, who called the current function. 
- msg.sender will always be on the left when you're doing require(msg.sender)
2. require: Makes it so that the function will throw an error and stop executing if some condition is not true.
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
  
### Function Visibility:  
1. internal is the same as private, except that it's also accessible to contracts that inherit from this contract. (Hey, that sounds like what we want here!).

2. External is similar to public, except that these functions can ONLY be called outside the contract — they can't be called by other functions inside that contract. We'll talk about why you might want to use external vs public later.
- In order to interact with external source, an interface is needed. Interface is applied when create a new contract and put the function of that external source in, and end with a semi colon. 
- `Contract Zombiefeeding is ZombieFactory{}`
- `contract NumberInterface {`
  `function getNum(address _myAddress) public view returns (uint);`
- We can use it in our contract by including it in our contract
- `Contract Zombiefeeding is ZombieFactory{}`
- `address NumberInterfaceAddress = 0xab38... 
-  // ^ The address of the FavoriteNumber contract on Ethereum
-  `NumberInterface numberContract = NumberInterface(NumberInterfaceAddress);`
-  // Now `numberContract` is pointing to the other contract

- ` function someFunction() public {`
-    // Now we can call `getNum` from that contract:
- `   uint num = numberContract.getNum(msg.sender);`
-    // ...and do something with `num` here

### Events:  
- are a way for your contract to communicate that something happened on the blockchain to your app front-end, which can be 'listening' for certain events and take action when they happen.
- Declare an event `event NewZombie( uint zombieId, string name, uint dna);`
- Then inside a function you want your front end to show/update, "fire" the event inside
- ` function _createZombie(string _name, uint _dna) private {`
- ` uint id = zombies.push(Zombie(_name, _dna)) - 1;` This is use, to record the id of the Zombie by using array's typical ID 
- ` NewZombie(id, _name, _dna);` This fires the event to JS front end


### Import: 
- import './somecontract.sol'; 
- Just to import a contract and make things look nicer.

### Storage and Memory:
1. Storage is stored permanently, and requires when dealing with structs and arrays

  - `Sandwich[] sandwiches;`

  - `function eatSandwich(uint _index) public {
  - ` // Sandwich mySandwich = sandwiches[_index];`

  - ` // ^ Seems pretty straightforward, but solidity will give you a warning`
-  `// telling you that you should explicitly declare `storage` or `memory` here.`

- ` // So instead, you should declare with the `storage` keyword, like:`
- `Sandwich storage mySandwich = sandwiches[_index];``
2. Memory is temporary and disappear when the function call ends

### Handling Multiple return Values:
- Imagine you have two functions, one with multiple returns... you can assign specific value inside another function by calling it.
- `function multipleReturns() internal returns(uint a, uint b, uint c) {`
  `return (1, 2, 3);`
`}`
- `function getLastReturnValue() external {`
 ` uint c;`
  `// We can just leave the other fields blank:`
 ` (,,c) = multipleReturns();`
