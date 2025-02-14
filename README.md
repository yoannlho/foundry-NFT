# Create NFT using openzeppelin Contract

This tutorial is about creating 2 differents kinds of NFTs.

1. An IPFS Hosted NFT 
2. An SVG NFT (Hosted 100% on-chain) 

- [Create NFT using openzeppelin Contract](#create-nft-using-openzeppelin-contract)
- [Getting Started](#getting-started)
  - [Requirements](#requirements)
  - [Quickstart](#quickstart)
- [Usage](#usage)
  - [Start a local node](#start-a-local-node)
  - [Deploy](#deploy)
  - [Deploy - Other Network](#deploy---other-network)
  - [Testing](#testing)
    - [Test Coverage](#test-coverage)
- [Deployment to a testnet or mainnet](#deployment-to-a-testnet-or-mainnet)
  - [Scripts](#scripts)
  - [Base64](#base64)
  - [Estimate gas](#estimate-gas)
- [Formatting](#formatting)
- [Thank you!](#thank-you)

# Getting Started

## Requirements

- [git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)
  - You'll know you did it right if you can run `git --version` and you see a response like `git version x.x.x`
- [foundry](https://getfoundry.sh/)
  - You'll know you did it right if you can run `forge --version` and you see a response like `forge 0.0.2 (1b49d91 2025-01-18T00:24:10.729819723Z)`

## Quickstart

```
git clone https://github.com/yoannlho/foundry-NFT
cd foundry-NFT
forge install
forge build
```

# Usage

## Start a local node

```
make anvil
```

## Deploy

This will default to your local node using Anvil. You need to have it running in another terminal in order for it to deploy.

```
make deploy
```

## Deploy - Other Network

[See below](#deployment-to-a-testnet-or-mainnet)

## Testing

1. Unit
2. Integration
3. Forked
4. Staging

This repo we cover #1 and #2.

```
forge test
```

or

```
forge test --fork-url $SEPOLIA_RPC_URL
```

### Test Coverage

```
forge coverage
```

# Deployment to a testnet or mainnet

1. Setup environment variables

You'll want to set your `SEPOLIA_RPC_URL` and `PRIVATE_KEY` as environment variables. You can add them to a `.env` file.

> However the best way to keep the private key secure is to use cast wallet : So use that command to encrypt the private key with a password : ``` cast wallet import defaultKey --interactive ```

- `PRIVATE_KEY`: The private key of your account (like from [metamask](https://metamask.io/)). **NOTE:** FOR DEVELOPMENT, PLEASE USE A KEY THAT DOESN'T HAVE ANY REAL FUNDS ASSOCIATED WITH IT.
  - You can [learn how to export it here](https://metamask.zendesk.com/hc/en-us/articles/360015289632-How-to-Export-an-Account-Private-Key).
- `SEPOLIA_RPC_URL`: This is url of the sepolia testnet node you're working with. You can get setup with one for free from [Alchemy](https://alchemy.com/?a=673c802981)

Optionally, add your `ETHERSCAN_API_KEY` if you want to verify your contract on [Etherscan](https://etherscan.io/). Just create an account and get your API key.

1. Get testnet ETH

Head over to [faucets.chain.link](https://faucets.chain.link/) and get some testnet ETH. You should see the ETH show up in your metamask. Be careful, now to get some testnet it requires to hold a minimum amount of token like chainlink token in that exemple (real money). **NOTE**: MAKE SURE THAT YOU HAVE ENOUGH SEPOLIA TESTNET IN YOUR ACCOUNT BECAUSE IF NOT, THE DEPLOYMENT WILL FAIL

2. Deploy (IPFS NFT)

```
make deploy ARGS="--network sepolia"
```

3. Deploy (SVG NFT) = It mints an NFT based on the mood

```
make deployMood ARGS="--network sepolia"
```


## Scripts

After deploying to a testnet or local net, you can run the scripts.

Using mint to mint an NFT:

```
make mint ARGS="--network sepolia"
```

Mint mood : 

```
make mintMoodNft ARGS="--network sepolia"
```

Flip mood : 

```
make flipMoodNft ARGS="--network sepolia"
```

## Base64

To get the base64 of an image, you can use the following command :

```
echo "data:image/svg+xml;base64,$(base64 -i img/sad.svg | tr -d '\n')"
```

## Estimate gas

You can estimate how much gas things cost by running:

```
forge snapshot
```

And you'll see an output file called `.gas-snapshot`

# Formatting

To run code formatting:

```
forge fmt
```

# Thank you!

If you appreciated this, feel free to follow me !

[![Yoann LHOMME Twitter](https://img.shields.io/badge/Twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white)](https://x.com/0xYoann)
[![Yoann LHOMME Linkedin](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/lhommeyoann/)

