# Deploy & Verify Smart Contract (Hardhat)

NOTE: THIS IS NOT A COMPLETE PROJECT. I have listed only the files that are relevant. You must follow the YouTube Tutorial if you want to use this in your app.

Faucet: 

https://faucets.chain.link/rinkeby

## Steps

### 1. Create new project

`mkdir new_project`

`cd new_project`

### 2. Install and Init Hardhat

`npm install --save-dev hardhat`

`npx hardhat`

### 3. Add network configuration


Specify network (rinkeby, mainnet, ropsten, etc.)

You need to make an Infura account and create new project: https://infura.io

Export your private key from MetaMask:
https://metamask.zendesk.com/hc/en-us/articles/360015289632-How-to-Export-an-Account-Private-Key

#### File: `hardhat.config.js`
```
module.exports = {
  solidity: "0.8.4",

  networks: {
    rinkeby: {
      url: "https://rinkeby.infura.io/v3/YOUR_PROJECT_ID",
      accounts: [metamask_private_key],
    },
    mainnet: {
      url: "https://mainnet.infura.io/v3/YOUR_PROJECT_ID",
      accounts: [metamask_private_key],
    },
  },
  
}
```


### 4. Deploy onto target network (rinkeby, mainnet, etc.)

Rinkeby

`npx hardhat run scripts/sample-scripts.js --network rinkeby`

Mainnet (REAL ETH)

`npx hardhat run scripts/sample-scripts.js --network mainnet`

### 5. Verify and Publish

https://hardhat.org/plugins/nomiclabs-hardhat-etherscan.html

`npm install --save-dev @nomiclabs/hardhat-etherscan`

Add this to `hardhat.config.js`
```
require("@nomiclabs/hardhat-etherscan");
```

Add Etherscan API Key: https://etherscan.io/

```
module.exports = {
  networks: {
    mainnet: { ... }
  },
  etherscan: {
    // Your API key for Etherscan
    // Obtain one at https://etherscan.io/
    apiKey: "YOUR_ETHERSCAN_API_KEY"
  }
};
```

Verify contract:

`npx hardhat verify --network mainnet DEPLOYED_CONTRACT_ADDRESS "Constructor argument 1"`


