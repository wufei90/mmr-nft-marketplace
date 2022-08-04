# MMR NFT Marketplace

Digital Marketplace to list and purchase NFTs, deployed on Polygon.

The marketplace logic consists of two smart contracts:

**NFT Contract** - This contract allows users to mint unique digital assets.
**Marketplace Contract** - This contract allows users to put their digital assets for sale on an open market.

### Prerequisites

The followings are required for this project:

1. Node.js installed on your machine
2. Metamask wallet extension installed as a browser extension

### The Stack

This is a full stack application using:

- **Web application framework** - [Next.js](https://nextjs.org/)
- **Solidity development environment** - [Hardhat](https://hardhat.org/)
- **File Storage** - [IPFS](https://ipfs.io/)
- **Ethereum Web Client Library** - [Ethers.js](https://docs.ethers.io/v5/)

## Getting Started

Clone the project and install all dependencies:

```sh
npm install
```

Then, save the private key for your wallet (exported from Metamask) into the `.secret` file, using the template file in the project.

Finally, configure and connect to the **Polygon Mumbai** test network on Metamask, and get some Matic from the [Matic Faucet](https://faucet.matic.network/) so that you can interact with the application.

## Running the Project

Execute the following command to deploy to the Polygon network:

```sh
npx hardhat run scripts/deploy.js --network mumbai
```

When the deployment is complete, the CLI should print out the addresses of the contracts that were deployed. Replace the content of `config.js` with these values.

You can now test out the app by running the command:

```sh
npm run dev
```

> If you run into an error, the contract address printed out to the console by hardhat could be incorrect due to a bug. You can get the correct contract addresses by visiting [https://mumbai.polygonscan.com/](https://mumbai.polygonscan.com/) and pasting in the address from which the contracts were deployed to see the most recent transactions and getting the contract addresses from the transaction data.

### Deploying to Mainnet

To deploy to the mainnet on the Polygon network, replace the configuration in the `hardhat.config.js` and the `loadNFTs` function in `pages/index.js` with the value of the mainnet RPC endpoint.

```javascript
/* hardhat.config.js */

/* adding Matic main network config to existing config */
...
matic: {
  url: "https://rpc-mainnet.maticvigil.com",
  accounts: [privateKey]
}
...
```

Public RPCs like the one listed above may have traffic or rate-limits depending on usage. You can sign up for a dedicated free RPC URL using services like Infura, MaticVigil, QuickNode, Alchemy, Chainstack, or Ankr.

### Next Steps

For the next steps, we could port over the queries implemented in this app using [The Graph](https://thegraph.com/). The Graph will open up many more data access patterns including things like pagination, filtering, and sorting which are necessary for more advanced applications.

We can also add additional steps to prepare for a deployment in production, such as veryfing the contracts that have been deployed.
