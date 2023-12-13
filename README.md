# Treasury

A treasury contract that helps interact with other DeFi protocols.

The Treasury smart contract is designed to manage funds by depositing USDC tokens into
Uniswap and Aave protocols. The deposited funds are then swapped for USDT and DAI
tokens, respectively. The contract allows the owner to set the distribution ratios for Uniswap
and Aave, deposit funds, withdraw funds, and calculate the yield.

## Constructor

The constructor initializes the contract with the following parameters:

- \_uniswapRouter: Address of the Uniswap V2 Router

- \_aaveLendingPool: Address of the Aave Lending Pool

- \_usdcToken: Address of the USDC token
- \_
  usdtToken: Address of the USDT token
- \_
  daiToken: Address of the DAI token
  These addresses are

## Functions

1. setRatios: Allows the contract owner to set the distribution ratios for Uniswap and Aave.
   The sum of both ratios must equal 100. This function ensures that the total allocation of
   funds is always 100%, preventing any loss or mismanagement of funds.

2. deposit: Accepts an amount of USDC tokens from the sender, calculates the distribution
   amounts based on the set ratios, and deposits the funds into Uniswap and Aave. The USDC
   tokens are then swapped for USDT and DAI tokens, respectively.

3. withdraw: Allows the contract owner to withdraw a specified amount of USDT and DAI
   tokens based on the set ratios. This function ensures that the owner can retrieve their funds
   when needed.

4. calculateYield: Returns the total balance of USDT and DAI tokens held by the contract. This
   function allows the owner to monitor the performance of their investments.

## Flow of Interaction

1. The owner deploys the contract with all the interacting addresses passed into the constructor.
2. The contract owner sets the distribution ratios for Uniswap and Aave using the setRatios
   function.
3. Users deposit USDC tokens into the Treasury smart contract using the deposit function.
4. The deposited USDC tokens are split based on the set ratios and sent to Uniswap and
   Aave.
5. In Uniswap, USDC tokens are swapped for USDT tokens.
6. In Aave, USDC tokens are deposited and swapped for DAI tokens.
7. The contract owner can withdraw USDT and DAI tokens using the withdraw function.
8. Anyone can check the total yield (USDT and DAI token balances) using the
   calculateYield function.
