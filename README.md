# MyToken Contract

This project features a basic token contract written in the Solidity programming language. It supports minting and burning tokens, tracks the total supply, and maintains account balances. This contract serves as an excellent starting point for those new to Solidity.

## Description

The MyToken contract facilitates essential operations such as minting and burning tokens. It includes a mechanism to modify the total token supply and adjust balances accordingly. This contract can be utilized to generate unique tokens on the blockchain.

1. **Token Details**: The contract has public variables to store the details about your token:
    - Token Name
    - Token Abbreviation
    - Total Supply

2. **Balances Mapping**: The contract has a mapping of addresses to balances.

3. **Mint Function**: The contract includes a mint function that:
    - Takes two parameters: an address and a value.
    - Increases the total supply by the given value.
    - Increases the balance of the given address by the same amount.

4. **Burn Function**: The contract includes a burn function that:
    - Takes two parameters: an address and a value.
    - Decreases the total supply by the given value.
    - Decreases the balance of the given address by the same amount.
    - Ensures the balance of the given address is greater than or equal to the amount to be burned.

## Contract Details

### Solidity Version

```solidity
pragma solidity 0.8.18;
```

### Contract Code

```solidity
// SPDX-License-Identifier: MIT

pragma solidity 0.8.18;

contract MyToken {

    // Public variables here
    string public tokenname = "Abhishek";
    string public tokenAbbre = "abhi";
    uint public TotalSupply = 0;

    // Mapping variable here
    mapping(address => uint) public balances;

    // Mint function
    function mint(address _address, uint _value) public {
        TotalSupply += _value;
        balances[_address] += _value;
    }

    // Burn function
    function burn(address _address, uint _value) public {
        require(balances[_address] >= _value, "Insufficient balance to burn");
        TotalSupply -= _value;
        balances[_address] -= _value;
    }
}
```

### Functions

1. **mint**:
    - **Parameters**: `address _address`, `uint _value`
    - **Description**: Increases the total supply by `_value` and increases the balance of `_address` by `_value`.

2. **burn**:
    - **Parameters**: `address _address`, `uint _value`
    - **Description**: Decreases the total supply by `_value` and decreases the balance of `_address` by `_value` if `_address` has enough balance.

## Getting Started

### Prerequisites

- Solidity compiler version 0.8.18

### Compiling the Contract

To compile the contract, use the following command:

```bash
solc --optimize --bin --abi MyToken.sol -o build
```

### Author

Abhishek Srivastava

## License

This project is licensed under the MIT License.

