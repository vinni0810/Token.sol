# MyToken Smart Contract
This Solidity smart contract "MyToken"  is a basic ERC20-like token. The contract allows for minting and burning of tokens, and keeps track of balances associated with addresses.

## Prerequisites

Solidity compiler version: 0.8.26

## Description

The MyToken contract is written in Solidity, a programming language specifically designed for developing smart contracts on the Ethereum blockchain. This contract includes public variables to store details about the token, a mapping to keep track of balances,
and functions to mint and burn tokens. This program serves as an introductory example to help you understand how to create and manage a custom token.

## Getting Started

### Executing program

To run this program, you can use Remix, an online Solidity IDE. To get started, go to the Remix website at https://remix.ethereum.org/.

Once you are on the Remix website, create a new file by clicking on the "+" icon in the left-hand sidebar. Save the file with a .sol extension (e.g., ETHProof.sol). Copy and paste the following code into the file:

```javascript
// SPDX-License-Identifier: MIT
pragma solidity 0.8.18;

/*
       REQUIREMENTS
    1. Your contract will have public variables that store the details about your coin (Token Name, Token Abbrv., Total Supply)
    2. Your contract will have a mapping of addresses to balances (address => uint)
    3. You will have a mint function that takes two parameters: an address and a value. 
       The function then increases the total supply by that number and increases the balance 
       of the “sender” address by that amount
    4. Your contract will have a burn function, which works the opposite of the mint function, as it will destroy tokens. 
       It will take an address and value just like the mint functions. It will then deduct the value from the total supply 
       and from the balance of the “sender”.
    5. Lastly, your burn function should have conditionals to make sure the balance of "sender" is greater than or equal 
       to the amount that is supposed to be burned.
*/

contract MyToken {

    // public variables here
    string public tokenName = "CRAFTERS";
    string public tokenAbbrv = "CVE";
    uint public totalSupply = 0;

    // mapping variable here
    mapping(address => uint) public balances;

    // mint function
    function mint(address _address, uint _value)public{
        totalSupply += _value;
        balances[_address] += _value;
    }

    // burn function
    function burn(address _address, uint _value)public{
        if (balances[_address] >= _value){
            totalSupply -= _value;
            balances[_address] -= _value;
        }
    }

}

```

To compile the code, click on the "Solidity Compiler" tab in the left-hand sidebar. Make sure the "Compiler" option is set to "0.8.26" (or another compatible version), and then click on the "Compile ETHProof.sol" button.

Once the code is compiled, you can deploy the contract by clicking on the "Deploy & Run Transactions" tab in the left-hand sidebar. Select the "MyToken" contract from the dropdown menu, and then click on the "Deploy" button.

Once the contract is deployed, you can interact with it by calling the mint and burn function. Click on the "MyToken" contract in the left-hand sidebar, and then click on the "mint" and "burn" function.

## Explaination

### mint Function

It takes two parameters: an address (_address) and a value (_value).

It increases the totalSupply by the amount specified in val.

It also increases the balance of the address _address by the same amount.

### burn Function

It takes two parameters: an address (_address) and a value (_value).

It first checks if the balance of the address _address is greater than or equal to the amount specified in _value.

If the condition is met, it decreases the totalSupply by the amount specified in _value.

It also decreases the balance of the address _address by the same amount.

## License

This `README.md` provides an overview of the smart contract, details its features, explains how to use the mint and burn functions, and includes a section on checking balances. It also notes that the project is licensed under the MIT License.
