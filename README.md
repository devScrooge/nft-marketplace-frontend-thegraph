# NFT MARKETPLACE FRONTEND THEGRAPH 🦄

This is a one of the two Frontend implementation of a NFT Marketplace from Patrick Alpha's fcc. The backend repo can be found [here](https://github.com/JMariadlcs/nft-marketplace-backend).

The frontend of this project is being implemented in two different ways:

1. Using [Moralis Indexer Frontend](https://github.com/JMariadlcs/nft-marketplace-frontend-moralis).
2. Using [TheGraph Indexer](https://github.com/JMariadlcs/nft-marketplace-frontend-thegraph).

The workshop followed to complete this repo is [this one](https://www.youtube.com/watch?v=gyMwXuJrbJQ&t=15996s).

The repo that we are going to implement is like [this one](https://github.com/PatrickAlphaC/nextjs-nft-marketplace-thegraph-fcc) and [this one](https://github.com/PatrickAlphaC/graph-nft-marketplace-fcc).

## PROJECT

Objetives of the frontend project:

1. Home Page: ✅
    1. Show recently listed NFTs.
        1. If you are the owner, you can update the listing.
        2. If you are NOT the owner, you can buy de listing.
2. Sell Page: ✅
    1. You can list your NFT to be sold.
    2. Withdraw proceeds.

## CREATE SIMILAR PROJECT FROM SCRATCH

-   Create Next.js project:

```bash
yarn create next-app .
```

-   Add Moralis to interact with front-end:

```bash
yarn add moralis react-moralis
```

-   Add Moralis web3uikit to interact with front-end:

```bash
yarn add web3uikit

```

-   Add tailwindcss (CSS formarter):

```bash
yarn add --dev tailwindcss postcss autoprefixer
```

-   Initialize tailwindcss:

```bash
yarn tailwindcss init -p
```

-   Override [tailwind.config.js](https://github.com/JMariadlcs/nft-marketplace-frontend-moralis/blob/main/tailwind.config.js) with the code inside this file.
-   Override [global.css](https://github.com/JMariadlcs/nft-marketplace-frontend-moralis/blob/main/styles/globals.css)

## RUN LOCAL SERVER

```bash
yarn dev
```

You will have your local server running at: `http://localhost:3000`.

-   Open new bash terminal to use while yarn server is running

## USE THEGRAPH

We are using TheGraph for reading the events. Steps:

1. Index events with TheGraph ✅.
2. Read indexed events from TheGraph ✅.

¿ How to use TheGraph ? -> Contracts must be verified on Etherscan.

-   Go to [TheGraph](https://thegraph.com/studio/).
-   Connect Metamask
-   Change to Smart Contracts deployed network (maybe Rinkeby)
-   Create subGraph
-   Create a new git repository for your subGraph
-   Install Graph CLI:

```bash
sudo yarn global add @graphprotocol/graph-cli
```

-   Initialize subGraph (change the name):

```bash
graph init --studio marketplace-nft-fcc
```

-   Execute (change name):

```bash
mv marketplace-nft-fcc/* ./
and marketplace-nft-fcc folder.
```

-   Modify `schema.graphql` with your events info and new tables that you want to create.
-   Every time you modify `schema.graphql` -> Execute:

```bash
graph codegen
```

-   Modify `nft-marketplace.ts` inside `src`.
-   Go to `subprah.yaml` and include after abi:

    ```bash
    startBlock: deployedcontractBlock -1
    ```

-   Deploy subGraph (change name last command):

```bash
graph auth --studio f4633ff08ae2b7ba89bad0099f8a6e8c
graph codegen && graph build
graph deploy --studio marketplace-nft-fcc
```

-   Version label: v0.0.1

✅ SUBGRAPH DEPLOYED!!

-   You can now start executing scripts from your backend and now your subGraph should be able to listen to these events.
