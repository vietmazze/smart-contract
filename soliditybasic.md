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
-	Integers int/uint with various bits, uint8 uint256
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

`contract SimpleAuction {
    event HighestBidIncreased(address bidder, uint amount); // Event

    function bid() public payable {
        // ...
        emit HighestBidIncreased(msg.sender, msg.value); // Triggering event
    }
}`
