REMIX DEFAULT WORKSPACE

Remix default workspace is present when:
i. Remix loads for the very first time 
ii. A new workspace is created with 'Default' template
iii. There are no files existing in the File Explorer

This workspace contains 3 directories:

1. 'contracts': Holds three contracts with increasing levels of complexity.
2. 'scripts': Contains four typescript files to deploy a contract. It is explained below.
3. 'tests': Contains one Solidity test file for 'Ballot' contract & one JS test file for 'Storage' contract.

SCRIPTS

The 'scripts' folder has four typescript files which help to deploy the 'Storage' contract using 'web3.js' and 'ethers.js' libraries.

For the deployment of any other contract, just update the contract's name from 'Storage' to the desired contract and provide constructor arguments accordingly 
in the file `deploy_with_ethers.ts` or  `deploy_with_web3.ts`

In the 'tests' folder there is a script containing Mocha-Chai unit tests for 'Storage' contract.

To run a script, right click on file name in the file explorer and click 'Run'. Remember, Solidity file must already be compiled.
Output from script will appear in remix terminal.

Please note, require/import is supported in a limited manner for Remix supported modules.
For now, modules supported by Remix are ethers, web3, swarmgw, chai, multihashes, remix and hardhat only for hardhat.ethers object/plugin.
For unsupported modules, an error like this will be thrown: '<module_name> module require is not supported by Remix IDE' will be shown.


###Payments.sol
This is a Solidity smart contract written in Ethereum programming language. This particular contract allows for the creation of payments with associated metadata (amount, timestamp, sender address, and message) to be stored on the blockchain. 

Here's an explanation of each section:

1. `// SPDX-License-Identifier: MIT` - This is a license identifier comment. It indicates that this contract is licensed under the MIT License.

2. `pragma solidity ^0.8.0;` - The pragma statement specifies the version of Solidity compiler to use. Here it's set to any version 0.8.x.

3. `contract Payments { ... }` - This is a smart contract named "Payments". It contains several functions and data structures for managing payments and balances.

4. Inside the `Payments` contract, there are three structs:
   - `Payment` which represents a single payment with properties like amount (in wei), timestamp, sender address, and message.
   - `Balance` which contains totalPayments and a mapping of payments to their index (uint). 

5. There is also a state variable called `balances` that maps addresses to Balance structs. This allows us to keep track of each user's balances and payments.

6. The function `currentBalance() public view returns(uint)` - Returns the current contract balance in wei. 

7. The function `getPayment(address _addr, uint _index) public view returns(Payment memory)` allows users to retrieve a specific payment by its index from a specified address. It does not modify any state variables.

8. The payable function `pay(string memory message) public payable` is used for making payments. It increases the sender's total payment count, creates a new Payment struct and stores it in their balance mapping with timestamp as current block time. This function can be called by sending Ether to this contract. 

This contract could be considered as an advanced form of accounting or logging where all transactions are recorded on the public ledger thanks to Solidity's immutable nature of smart contracts. It provides transparency and traceability, making it suitable for financial applications such as peer-to-peer payments, decentralized exchanges (DEX), etc.
