# DegenGaming
The `DegenGaming` smart contract is designed for a gaming platform that utilizes blockchain technology to manage in-game tokens and rewards. The contract is built using Solidity and allows the creation, transfer, burning, and redemption of ERC20-like tokens. Below is a detailed description of its functionality:

### Overview

The `DegenGaming` contract manages a custom token called "Degen" (symbol: DGN) and provides functionalities for minting, transferring, burning tokens, and redeeming in-game rewards (NFTs).

### Key Features

1. **Token Management**
   - **Minting**: Only the contract owner can mint new tokens and assign them to specific addresses.
   - **Transferring**: Users can transfer tokens to other addresses.
   - **Burning**: Users can burn their tokens, reducing the total supply.

2. **Rewards System**
   - Users can redeem tokens for in-game rewards (NFTs) such as "Emerald Boots," "Emerald Sword," and "Identity Change Card."
   - Each reward has a specific price in tokens.

3. **Balance and Rewards Tracking**
   - Users can check their token balances.
   - The contract keeps track of the items each user has redeemed.

### Detailed Description

#### State Variables

- **commandCenter**: Stores the address of the contract owner.
- **tokenName**: The name of the token, "Degen."
- **symbol**: The symbol of the token, "DGN."
- **totalSupply**: The total number of tokens in circulation.

#### Mappings

- **balances**: Maps addresses to their respective token balances.
- **rewards**: Maps reward IDs to their corresponding NFT details (name and price).
- **redeemedItems**: Tracks the rewards redeemed by each address.

#### Structs

- **NFT**: Represents an in-game reward with a name and price.

#### Constructor

Initializes the contract by setting the deployer's address as the `commandCenter` and defining three in-game rewards.

#### Modifiers

- **onlyOwner**: Ensures that only the contract owner can execute certain functions.

#### Functions

1. **mint**
   - Allows the contract owner to create new tokens and assign them to a specified address.
   - Parameters: `amount` (number of tokens to mint), `receiver` (address to receive the tokens).
   - Ensures the minting amount is greater than zero.

2. **transfer**
   - Allows users to transfer tokens to another address.
   - Parameters: `amount` (number of tokens to transfer), `receiver` (address to receive the tokens).
   - Ensures the sender has enough balance to cover the transfer.

3. **burn**
   - Allows users to burn their tokens, reducing the total supply.
   - Parameters: `amount` (number of tokens to burn).
   - Ensures the user has enough balance to cover the burn amount.

4. **checkBalance**
   - Allows anyone to check the token balance of a specific address.
   - Parameters: `user` (address to check the balance of).
   - Returns the balance of the specified address.

5. **redeem**
   - Allows users to redeem tokens for in-game rewards.
   - Parameters: `rewardID` (ID of the reward to redeem).
   - Ensures the user has enough tokens and that the reward ID is valid.
   - Updates the user's balance and records the redeemed item.
   - Returns the name of the redeemed reward.

6. **getRedeemedItems**
   - Allows anyone to view the list of items a specific user has redeemed.
   - Parameters: `user` (address to get the redeemed items of).
   - Returns an array of strings representing the names of the redeemed items.

### Use Case

This contract is suitable for a gaming platform that wants to implement a blockchain-based token system. It ensures secure token management, facilitates user interactions, and tracks in-game rewards, making it an integral part of a decentralized gaming ecosystem.
