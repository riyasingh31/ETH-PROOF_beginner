# ETH-PROOF_beginner
This contract provides basic functionality for a token system, allowing tokens to be created (minted) and destroyed (burned) while keeping track of the total supply and individual balances.
The contract, named `MyToken`, represents a simple token system on the Ethereum blockchain. It includes basic functionalities for minting and burning tokens, as well as public variables to store token details and a mapping to keep track of token balances for different addresses.

1. License and Pragma Statement
```solidity
// SPDX-License-Identifier: MIT
pragma solidity 0.8.18;
```
This line specifies the license type for the contract, which is MIT in this case.
This specifies the Solidity compiler version to be used, ensuring compatibility with version 0.8.18.

2. Contract Definition
```solidity
contract MyToken {
```
- This line declares a new contract named `MyToken`.

3. Public Variables
```solidity
    // Public variables for token details
    string public TokenName = "RIYA";
    string public TokenAbbrv = "RS";
    uint public TotalSupply = 0;
```
- **TokenName**: Stores the name of the token, which is "RIYA".
- **TokenAbbrv**: Stores the abbreviation for the token, which is "RS".
- **TotalSupply**: Keeps track of the total supply of the tokens in circulation, initialized to 0.

The `public` keyword makes these variables accessible outside the contract, meaning anyone can read their values.

 4. Mapping for Balances
```solidity
    // Mapping to store balances
    mapping(address => uint) public balances;
```
- **balances**: This is a mapping from addresses to unsigned integers (`uint`). It is used to store the balance of tokens for each address. The `public` keyword makes the mapping readable from outside the contract.

5. Mint Function
```solidity
    // Mint function to create new tokens
    function mint(address addr, uint value) public {
        TotalSupply += value;
        balances[addr] += value;
    }
```
- **mint**: This function allows the creation of new tokens.
  - **Parameters**:
    - `address addr`: The address to which the newly minted tokens will be assigned.
    - `uint value`: The number of tokens to be minted.
      
6. Burn Function
```solidity
    // Burn function to destroy tokens
    function burn(address addr, uint value) public {
        require(balances[addr] >= value, "Insufficient balance");
        TotalSupply -= value;
        balances[addr] -= value;
    }
```
- **burn**: This function allows the destruction of tokens.
  - **Parameters**:
    - `address addr`: The address from which the tokens will be burned.
    - `uint value`: The number of tokens to be burned.
