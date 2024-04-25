# SuperCert- Transcript Verification System for Engineering Colleges

SuperCert is a web application that can used to store academic transcripts issued by University immutably in blockchain in form of CID (CID is generated by storing the transcript in an IPFS prior to storing in blockchain.) The CID generated will be shared with students in form of raw hash (here we have done it using email) or QR Code. 
Students can share the recieved form of transcript (CID or QR code) with the university (higher education institutes) and they can use the same website to efficiently verify the same. 
Removes intermediary (here it is university where the student is affiliated with) and makes the process quick, simple and efficient for both student and verification authority.

This project uses following tools and technologies
- **Ethereum (Sepolia)**
- **React (frontend)**
- **ExpressJs (Backend)**
- **Pinata (IPFS)**
- **Hardhat and EtherJs (for interacting with blockchain)**
- **MongoDB (for logging trasactions)**
- **Solidity and Chainlinkfor smart contract**

## Architecture 

<img src="https://github.com/midnight-mira/SuperCert--Transcript-Verification-System-for-Engineering-Colleges-using-Blockchain/blob/main/img/architecture.png" align="center">

___________________
There are 3 main folders viz:
1. Client (for frontend)
2. Server (for mongoDB and RestAPIs)
3. Parent file (which contains contracts and abis)

Follow along with _README_ in each folder to correctly configure and execute the contract files.

__STEP 1. Install the npm file (parent directory)__

   ```js
   npm install
   ```
__STEP 2. Create metamask account and create web3 sepolia account on alchemy.__

after setting up metamask account, download the metamask extension. Create an alchemy account, create a project and copy its https api key. paste it in _hardhat.config.js_ file

```js

url: `https://eth-sepolia.g.alchemy.com/v2/your-api-key`,
accounts: [SEPOLIA_PRIVATE_KEY] //private key is one time key that you can see only once when the project is created, be sure to store it somewhere safe.

```

for get faucet ether use the following website:
https://learnweb3.io/faucets/sepolia/

__STEP 3. compile and deploy smart contract.__

Compile contract using

```shell

$ npx hardhat compile

```
This creates a artifacts and abi-file.

For deploying the contract exceute _scripts/deploy.js_

```bash

$ npx hardhat deploy scripts/deploy.js --network sepolia

```
The above command logs the sepolia testnet address for both the smart contracts.Replace this address in _client/components/user/Verify.jsx_ and _client/components/admin/AddDocument.jsx_

```js

const paymeAddr = 'Your testnet address for payme contract'
const Address = 'Your testnet address for IPFSHashStorage contract'

```
for checking and verifying transactions on the testnet go to:

https://sepolia.etherscan.io/address/your-testnet-address

**TO DO**
1. Fix automatic conversion chainlink contract
2. Add Struct and map both the hash and sender for preventing duplicate charges





