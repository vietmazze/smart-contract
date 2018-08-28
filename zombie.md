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
