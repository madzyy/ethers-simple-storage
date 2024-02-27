# Ethers Simple Storage

This is a basic smart contract built with solidity and and the ethers framework to store numbers and retrieve them.

First compile the smart contract SimpleStorage.sol probably with solcjs.

```yarn
yarn solcjs --bin --abi --include-path node_modules/ --base-path . -o . SimpleStorage.sol
```

A number of abi and binary files will be created which will then need to be deployed.
Run
```node
node deploy.js 
```
to deploy the function using ethers js.
These javascript code will be run
```javascript
const currentFavoriteNumber = await contract.retrieve();
console.log(
    `the current favorite number is ${currentFavoriteNumber.toString()}`
);

const transactionResponse = await contract.store("7");
const receipt = transactionResponse.wait(1);
const updatedFavoriteNumber = await contract.retrieve();
```
And this triggers the solidity functions store() and retrieve() 
```solidity
function store(uint256 _favoriteNumber) public virtual{
    favoriteNumber = _favoriteNumber;
}
    
function retrieve() public view returns(uint256){
    return favoriteNumber;
}
```
Like that