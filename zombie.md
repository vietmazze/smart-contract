# Crypto Zombie

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



