# MyERC20Token

MyERC20Token is a simple ERC20 token implementation using Solidity. The token contract allows the owner to mint new tokens, and any user can burn their tokens and transfer tokens to others.

## Contract Details

- **Token Name**: MyToken
- **Token Symbol**: MTK
- **Initial Supply**: 1000 MTK

## Features

- **Minting**: Only the contract owner can mint new tokens.
- **Burning**: Any user can burn their tokens.
- **Transferring**: Any user can transfer their tokens to another address.

## Prerequisites

- **Node.js** and **npm**: Ensure you have Node.js and npm installed.
- **MetaMask**: A MetaMask wallet for deploying and interacting with the contract.
- **Remix IDE**: An online Solidity IDE for writing, compiling, and deploying smart contracts.

## Setup and Deployment

1. **Open Remix IDE**:
   - Go to [Remix IDE](https://remix.ethereum.org/).

2. **Create a New File**:
   - In the File Explorer pane, click on the "+" button to create a new file.
   - Name the file `Token.sol`.

3. **Copy and Paste the Solidity Code**:
   - Copy the Solidity code provided below and paste it into the `Token.sol` file.

   ```solidity
   // SPDX-License-Identifier: MIT
   pragma solidity ^0.8.0;

   import "@openzeppelin/contracts/token/ERC20/ERC20.sol";

   contract Token is ERC20 {
       address public owner;

       constructor() ERC20("MyToken", "MTK") {
           _mint(msg.sender, 1000 * 10 ** decimals()); // Mint initial supply to contract deployer
           owner = msg.sender;
       }

       function mint(address to, uint256 amount) public {
           require(msg.sender == owner, "Only owner can mint tokens");
           _mint(to, amount);
       }

       function burn(uint256 amount) public {
           _burn(msg.sender, amount);
       }
   }
