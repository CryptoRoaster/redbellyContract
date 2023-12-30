# FunctionTypes Smart Contract Documentation

## Overview

This documentation provides guidelines on how to interact with the `FunctionTypes` smart contract deployed on the Redbelly Blockchain. The contract contains various types of functions demonstrating different capabilities such as modifying state variables, pure computations, viewing data, and handling payments.

### Smart Contract Information

- **Name:** FunctionTypes
- **Version:** 1.0
- **License:** MIT
- **Solidity Version:** ^0.8.4

## Contract Functions

### 1. Default Function

#### Description

The default function (`add`) increments the `number` state variable by 1.

#### Usage

```solidity
function add() external
```

## 2. Pure Function
Description

The **`addPure`** function is a pure function that performs a simple arithmetic operation on the provided parameter and returns the result.

Usage

```
function addPure(uint256 _number) external pure returns(uint256 new_number)
```

## 3. View Function
Description

The **`addView`** function is a view function that retrieves the current state variable **`number`** and returns its incremented value.

Usage
```function addView() external view returns(uint256 new_number)
```

## 4. Internal Function
Description

The **`minus`** function is an internal function that decrements the number state variable by 1.

Usage

```function minus() internal
```

## 5. Internal Function Call
Description

The **`minusCall`** function is an external function that calls the internal function minus.

Usage
```function minusCall() external
```

## 6. Payable Function
Description

The **`minusPayable`** function is an external payable function that decrements the **`number`** state variable by 1 and returns the current balance of the contract.

Usage
```function minusPayable() external payable returns(uint256 balance)
```

## Interacting with the Contract
To interact with the **`FunctionTypes`** smart contract, you can follow these general steps:

1. #### Deploy the Contract:
- Deploy the contract on the Redbelly Blockchain.
2. #### Invoke Functions:

- Call the desired functions using the appropriate method based on the function's visibility (external, internal) and type (pure, view, payable).
3. #### Transaction Execution:

- Some functions might require a transaction to be executed, especially if they modify the state or involve payments. Ensure you provide the necessary gas and any required parameters.
4. #### Retrieve Results:

- For functions with return values, capture the returned data as needed.

## Example Usage
Below is a simple example demonstrating how to interact with the deployed contract using a hypothetical Ethereum JavaScript library. Ensure you replace placeholders such as **`<contract_address>`** with the actual deployed contract address.

```
const Web3 = require('web3');
const web3 = new Web3('https://redbelly.blockchain.com');

const contractAddress = '<contract_address>';
const contractABI = <contract_abi>; // Replace with the actual ABI

const contract = new web3.eth.Contract(contractABI, contractAddress);

// Example 1: Call add function
contract.methods.add().send({ from: '<your_wallet_address>', gas: 300000 });

// Example 2: Call addView function
const result = await contract.methods.addView().call();

// Example 3: Call minusPayable function with payment
const payment = web3.utils.toWei('1', 'ether');
const transaction = await contract.methods.minusPayable().send({ from: '<your_wallet_address>', gas: 300000, value: payment });

// Retrieve the transaction balance
const balance = await web3.eth.getBalance(contractAddress);
console.log('Current Contract Balance:', web3.utils.fromWei(balance, 'ether'));
```

Ensure that you have a compatible web3 library installed and replace placeholder values with actual wallet addresses and ABI data.
