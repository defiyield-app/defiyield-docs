# New Integration Guide

Looking to add a new integration through the **DeFiYield Workshop**? You came to the right place! Here you'll find everything you need to know to integrate a new dapp. Feel free to check out repository's [**readme**](https://github.com/defiyield-app/defiyield-workshop/blob/main/README.md) for more details.

## Supported Blockchains

The DeFiYield Workshop currently supports new integrations in the following blockchains:

* Arbitrum
* Aurora
* Avalanche
* Binance
* Boba
* Celo
* Cronos
* Ethereum
* Fantom
* Fuse
* Gnosis
* Harmony
* Heco
* Iotex
* Kava
* Klaytn
* Kucoin
* Metis
* Milkomedia
* Moonbeam
* Moonriver
* Okx
* Optimism
* Polygon

## Supported Integration Categories

These are the current categories for integrations on the DeFiYield Workshop. If you have an integration that doesn't fit into any of the following, open up an issue on our repository!

* DEX
* Yield
* Lending
* CDP
* Yield Aggregator
* Cross Chain
* Liquid Staking
* POS Staking
* Derivatives
* Algo-stable
* Insurance
* Synthetics
* Gaming
* Governance
* NFT Marketplace
* NFT Lending
* Other

## Configuring New Integration

To quickly start up a new integration, run the following commands after forking our repo:

```bash
yarn install
yarn workshop make YOUR_INTEGRATION_NAME_HERE
```

Instead of `YOUR_INTEGRATION_NAME_HERE`, use the name of the dapp you are integrating! For example, if you were integrating `Aave`, use `yarn workshop make Aave`.

This command will create several files in the `/apps/workshop/projects/` directory, under the name of your integration.

* The `index.ts` file is the main entry to your integration, including the following info:
  * `name` - The name of the project you are integrating.
  * `categories` - Any categories appropriate for displaying your integration throughout the app.
  * `links` - Any links to the project's app, social media, etc.
  * `modules` - An array of your integration's modules (explained below).
* The `modules` folder should include files for each your integration's features, such as staking, LPing, etc.
* The `abis` folder should include any ABI json files specific to your integration. More common ABIs such as UniV2 or ERC20 ABIs can be otherwise found in the `/packages/abis/` directory.
* The `icons` folder should include any icons/images specific to your integration, such as token icons, logos, etc.
* The tests folder should include any test scripts to verify the functionality of your integration. Learn more about testing [**here**](testing-integrations.md).

You can start a dev server to view your integration at any point by using the following command:

```bash
yarn workshop start YOUR_INTEGRATION_NAME_HERE
```

Once this command is running, simply navigate to [**http://localhost:8070**](http://localhost:8070) on your browser of choice to see it in action. You'll be able to see a UI to help you test and debug your integration:

<figure><img src="../.gitbook/assets/image (1).png" alt=""><figcaption><p>Example Testing UI</p></figcaption></figure>

## Module Creation

A module should query for user balances in whatever aspect of your project you are integrating, as well as return the relevant pools and token addresses. Every module should have the following structure:

```typescript
interface ModuleDefinitionInterface {
  name: string
  chain: SupportedChain
  type: SupportedProtocolType
  preloadTokens: (context: Context) => Promise<string[]>
  fetchPools: (context: FetchPoolsContext) => Promise<(Pool | void)[]>
  fetchUserPositions: (context: FetchUserPositionsContext) => Promise<(UserPosition | void)[]>
}
```

In order to facilitate development of your modules, we expose the following interface with additional context:

```typescript
interface Context {
  axios: axios
  BigNumber: BigNumber
  logger: {
    debug: (msg: string) => void
    info: (msg: string) => void
    warn: (msg: string) => void
    error: (msg: string) => void
  }
  ethers: ethers
  provider: ethers.provider
  ethcall: ethcall
  ethcallProvider: ethcall.Provider
}
```

This context should be passed to any of your methods inside your module, and provide them with instances of the most common frameworks to query, format or otherwise manipulate on-chain data (or off-chain with `axios`).

The `logger` instance should be used instead of console logs.

The following interfaces are also available if you wish to work with any assets more complex than a traditional ERC20, or wish to add extra data to the basic `Context` object:

```typescript
interface ComplexAsset {
  address: string
  decimals: number
  categories: { code: string }[]
  underlying: { address: string; decimals: number; price: number }[]
  metadata: { [key: string]: unknown }
}

interface FetchPoolsContext extends Context {
  tokens: Token[];
}

interface FetchUserPositionsContext extends Context {
  pools: Pool[];
}

interface FetchTokenDetailsContext extends Context {
  address: string;
}

interface FetchTokenPricesContext extends Context {
  assets: ComplexAsset[];
}
```

## Troubleshooting

#### TypeScript Errors

If you're seeing TypeScript resolution errors throughout your local repository, make sure you set your TypeScript version to the one used by the workspace. Modern IDEs may prompt you to do this when loading it:

<figure><img src="../.gitbook/assets/image (2).png" alt=""><figcaption><p>Example TypeScript version prompt</p></figcaption></figure>

If not, you might still be able to set it manually. On VSCode, for example, use `Ctrl+Shift+P` and search for `TypeScript: Select TypeScript Version...` where you can select the workshop's version.

#### Missing Token Details

If a token you are trying to get details for is not available, try waiting a few minutes as the API will try to resolve the token's details over time. If it remains unavailable, please [**open a new issue**](https://github.com/defiyield-app/defiyield-workshop/issues/new?assignees=\&labels=i%3A+bug%2C+i%3A+needs+triage\&template=token-bugs.md\&title=Missing%20Token:).

#### Incorrect Token Details

If the data for any token you are using in your integration seems incorrect, such as its decimals, symbol, pricing information, etc. please [**open a new issue**](https://github.com/defiyield-app/defiyield-workshop/issues/new?assignees=\&labels=i%3A+bug%2C+i%3A+needs+triage\&template=token-bugs.md\&title=Incorrect%20Token:).
