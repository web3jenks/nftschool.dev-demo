# NFT School Tutorials Sample Code

## About

This is the companion sample code of the [Mint with NFT.storage and Polygon](https://nftschool.dev/tutorial/mint-nftstorage-polygon/#minting-your-nft) tutorial at NFTschool.dev.

Follow the detailed step by step guide [here](https://nftschool.dev/tutorial/mint-nftstorage-polygon/#minting-your-nft).

## Getting started quickly

If you would like to try this out quickly, follow the steps below:

### Step 1

Install npm dependencies. Make sure you your npm version is above 8 or executing scripts of hardhat will fail.

```shell
$ npm install
```

### Step 2

Update your `.env` environmnet variables. Replace `your_wallet_private_key` with your test account's private key ([here](https://metamask.zendesk.com/hc/en-us/articles/360015289632-How-to-Export-an-Account-Private-Key) is how). Replace `your_nftstroage_api_key` with your nft.storage account api key you created ([here](https://nft.storage/manage/) is a link to it).

```shell
PRIVATE_KEY=your_wallet_private_key
NFT_STORAGE_API_KEY=your_nftstroage_api_key
```

> Note: you can get some test MATICs from this [faucet](https://faucet.polygon.technology/).

### Step 3

Upload MyExampleNFT.png to NFT.stroage (to IPFS + Filecoin network) and save the ipfs://xxx/metadata.json link.

```shell
$ node scripts/store-asset.mjs
Metadata stored on Filecoin and IPFS with URL: ipfs://xxx/metadata.json
```

### Step 4

Deploy the contract to Polygon network by executing hardhat script. Save the deployed address for later.

```shell
$ npx hardhat run scripts/deploy-contract.mjs --network PolygonMumbai
Contract deployed to address: 0x00xxx
```

### Step 5

Update `mint-nft.mjs` with correct variables. Replace `your_deployed_contract_address` with the contract address you saved in Step 4. Replace `your_ipfs_nft_metadata_json_link` with the asset metadata json link you saved in Step 3.

```js
const CONTRACT_ADDRESS = "your_deployed_contract_address"
const META_DATA_URL = "your_ipfs_nft_metadata_json_link"
```

### Step 6

Mint the NFT and send NFT to your wallet by execuiting following script.

```shell
$ npx hardhat run scripts/mint-nft.mjs --network PolygonMumbai
NFT minted to:  0x00xxxx
```

If successful `0x00xxxx` should be your test wallet account address.

### Step 7

To verify, go to your metamask test account. You should see your MATIC amount reduced. If you connect your wallet to [Opensea Testnet](https://testnets.opensea.io/account) and authorise, you should see the NFT artwork displayed under your account.

Happy minting!
