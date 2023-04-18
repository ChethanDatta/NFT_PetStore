# NFT_PetStore
A BlockChain based pet store

------
### Pre-requisites

NPM
```
https://docs.npmjs.com/downloading-and-installing-node-js-and-npm
```

Flow
```
https://developers.flow.com/tools/flow-cli/install
```

NFT.storage account
```
https://nft.storage/
```
------
### Steps 

Open new terminal and start an emulator
```
flow emulator
```
Open new terminal and test the project
```
flow project deploy

// Mint first NFT
flow transactions send src/flow/transaction/MintToken.cdc '{"name": "Max", "breed": "Bulldog"}'

// Store the below keys to reuse
flow keys generate

// Create new account
flow accounts create --key <PUBLIC_KEY> --signer emulator-account

// Store the Address and Private key in flow.json
"accounts": {
  "emulator-account": {
    "address": "f8d6e0586b0a20c7",
    "key": "5faa55effec5876b0f4cfa018ddefdf73acc2d4f7009aebc2aaec88233d1ab0e"
  },
  "test-account": {
    "address": "0x01cf0e2f2f715450",
    "key": "68eb742e787ce096cb7767241958c3f40ac949b8fb0c0255f2e975052846b6c8"
  }
},

// Init collection
flow transactions send src/flow/transaction/InitCollection.cdc —-signer <ACCOUNT_NAME_IN_FLOW.JSON>

// Transfer NFT to test-account
flow transactions send src/flow/transaction/TransferToken.cdc 1 <ADDRESS>

// Get token owner
flow scripts execute src/flow/script/GetTokenOwner.cdc <TOKEN_ID>

// Get token metadata
flow scripts execute src/flow/script/GetTokenMetadata.cdc <TOKEN_ID>

// Get all token ids
flow scripts execute src/flow/script/GetTokenIds.cdc
```

### Reference 
https://nftschool.dev/tutorial/flow-nft-marketplace/#building-pet-store <br/>
https://github.com/jochasinga/flowwow/
