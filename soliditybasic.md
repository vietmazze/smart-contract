# Function type:
 - public: For all
 - private: Only the contract can all this function
 - view: Function returns data and does not modify the contracts data.
   - function getMessage() public view returns(strings) (returns is use with view) 
 - constant: Function returns data and does not modify the contracts data
 - pure: Function will not modify or even read the contract's data.
 - payable: When someone call this function, they might send ether along.
 
## Structure of a Contract
-	State variables: are values which are permanently stored in the contract storage. 
-	Booleans (T/F)
-	Integers int/uint with various bits, uint8 uint256. int is positive or negative integer with no decimal/ uint is only positive with no decimal
-	Address: holds a 20 byte value (size of an Ethereum address) with members balance and transfer.
  
  `address myAddress = this;`
  	`if (x.balance < 10 && myAddress.balance >= 10) x.transfer(10)`
-	Enums: One way to create a user-defined type in Solidity. 
-	Mapping `mapping(_KeyType => _ValueType)` where Keytype can be any type except mapping, and valuetype can be any types. 

## Function Types: 
-	Executable units of code within a contract
    
    `function (<parameter types>) {internal|external} [pure|constant|view|payable] [returns (<return types>)]`
-	Function modifier: Use to easily change the behavior of functions, to check for a condition prior to executing the function.
    
    `modifier onlySeller() { // Modifier`
        `require(`
           ` msg.sender == seller,`
            `"Only seller can call this."`

## Events:
 When they are called, they cause the arguments to be stored in the transaction’s log, which can be used to “call” the JS user interface of a dapp. Events are produce by using `emit`, followed by the name of even and arguments. 

`contract SimpleAuction {
    event HighestBidIncreased(address bidder, uint amount); // Event

    function bid() public payable {
        // ...
        emit HighestBidIncreased(msg.sender, msg.value); // Triggering event
    }
}`


# Units and Globally Available Variables

## Ether Units: 
A subset of units are use to convert Ether, 2 ether == 2000 finney. 
-	Wei, finney, szable, or ether

## Special Variables and Functions:
 
- `block.blockhash(uint blockNumber) returns (bytes32)`: hash of the given block - only works for 256 most recent, excluding current, blocks - deprecated in version 0.4.22 and replaced by blockhash(uint blockNumber).
-	`block.coinbase (address)`: current block miner’s address
-	`block.difficulty (uint)`: current block difficulty
-	`block.gaslimit (uint)`: current block gaslimit
-	`block.number (uint)`: current block number
-	`block.timestamp (uint)`: current block timestamp as seconds since unix epoch
-	`gasleft() returns (uint256)`: remaining gas
-	`msg.data (bytes)`: complete calldata
-	`msg.gas (uint)`: remaining gas - deprecated in version 0.4.21 and to be replaced by gasleft()
-	`msg.sender (address)`: sender of the message (current call)
-	`msg.sig (bytes4)`: first four bytes of the calldata (i.e. function identifier)
-	`msg.value (uint)`: number of wei sent with the message
-	`now (uint)`: current block timestamp (alias for block.timestamp)
-	`tx.gasprice (uint)`: gas price of the transaction
-	`tx.origin (address)`: sender of the transaction (full call chain)


## Inheritance: 
-	A way to connect to contracts with each other, a contract can inherits from multiple contracts and only a single contract is created on the blockchain. 
`contract owned {
    constructor() { owner = msg.sender; }
    address owner;
}`
-	 Use `is` to derive from another contract. Derived
	 contracts can access all non-private members including
	 internal functions and state variables. These cannot be
	 accessed externally via `this`, though.
	
	`contract mortal is owned {
    	function kill() {
   	     if (msg.sender == owner) selfdestruct(owner);`
    
-	One problem with multiple inheritance is the Diamond Problem.
` contract X {}
contract A is X {}
contract C is A, X {}`

-	C requests X to override A, but A itself requests to override X, which is a contradiction.

## MSG object:
-  A global variable that is used to describe who just sent in a function invocation
-  msg.data : Data field from the call or transaction that invoked the current function. 
-  msg.sender: Address of the account that started the current function/ transaction
-  msg.value: Amount of ether that was sent along with the function invocation



# Reference Type:
- fixed array: Single type of element, unchanging length  `int[3] -> [1,2,3]`
- dynamic array: single type but can change in size. dont place a # in int[]  `int[] -> [1,2,3]`
- Solidity allows nested array but the bridge between JS/Web3 and Solidity does not allow nested dynamic array.. so we must convert.
- Strings in solidity is considered as nested array, so we cannot transfer array of strings to JS. We can stored but not move.
- mapping: Collection of key value pairs.
- Pseudo random number generator: Since solidity doesnt have random generator, we must make a "fake" generator. Keccak256/sha3/block.difficulty/now/ are global variable
	` function random() private view returns (uint) {
		`return uint(keccak256(block.difficulty, now, players));`
	  `}`	
	  
- players[1].transfer(this.balance): transfer is a global function that allow you to send this.balance to the player 1
- Inside a function, you can restart it by using `new` variable.

# Node JS:
`npm install -g solc` is Solidity compiler
- Contract ---> Solidity Compiler ---> ABI | Bytecode

# Compile.js
- Compile.js is use to read in solidity as JS in order to compile. 
	`const path = require('path')`  allow us to cross platform from solidity to JS
	`const fs = require('fs')`  link the list to the .sol file
	`const inboxtPath = path.resolve(___dirname, 'contracts', 'Inbox.sol')`
	`const source = fs.readFileSync(inboxPath,'utf8')`
	Afterward you can compile with: 
	`const solc = require('solc')`
	`olc.compile(source,1)`
	
