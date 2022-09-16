# API

{% hint style="warning" %}
The DeFiYield API is still under development! Details below may change prior to a full launch.
{% endhint %}

The DeFiYield API is the easiest way to integrate our expansive functionality into any app of your choosing. Whether you are interested in querying our audit or Rekt databases, querying a wallet's balances or details about the many blockchains we've integrated, our API is here for you.

Our API supports all the tokens, protocols and blockchains supported by our app - meaning you'll have access to data from 25+ blockchains, 270+ protocols and countless tokens.

## Querying

Queries should be made to the following URL:

`https://public-api.defiyield.app/`

You can test out your queries before setting them up in your app through our handy [**GraphQL playground**](https://public-api.defiyield.app/graphql/).

Before being able to query either one, make sure you have properly [**authenticated**](api.md#authentication) your queries!

### Available Queries

* **credits** - Credit information with regards to your API key.
  * `cost`, `remaining`, `resetAt`
* **chains** - Includes information about the many blockchains we have integrated into our dashboard ([**list here**](../dashboard/the-defiyield-dashboard/supported-blockchains.md)).
  * `id`, `absoluteChainId`, `abbr`, `name`, `type`
* **assets** - Paginated data about the many assets we have integrated into our dashboard.
  * `id`, `address`, `chainId`, `name`, `symbol`, `icon`, `decimals`, `categories`, `chain`
* **assetsPrices** - Price information regarding any of our integrated assets.
  * `id`, `address`, `chainId`, `price`
* **assetBalances** - Asset balances for any given wallet address.
  * `total`, `assets` (`asset`, `balance`, `price`, `total`)
* **protocols** - Includes information about the many dapps we have integrated into our dashboard ([**list here**](../dashboard/the-defiyield-dashboard/supported-protocols.md)).
  * `name`, `slug`, `features` (`list`, `chain`)
* **protocolBalance** - Protocol balances for any given wallet address.
  * `protocol`, `address`, `total`, `chains` (`chain`, `featureList`, `total`, `positions`)
* **rekts** - Paginated data about all hacks and exploits in our [**Rekt Database**](../audits/rekt-database.md).
  * `id`, `projectName`, `description`, `date`, `fundsLost`, `fundsReturned`, `chainIds`, `category`, `issueType`, `token`
* **shields** - Safety information from [**DeFiYield Shield**](../security-toolkit/shield.md) regarding any given wallet address(es).
  * `id`, `address`, `network`, `name`, `logo`, `inProgress`, `whitelisted`, `version`, `tags`, `token`, `issues` (`id`, `registryId`, `impact`, `title`, `description`, `category`, `data`)

## Authentication

In order to use our API, you must first get a valid API key. Get one by sending a request [**here**](https://defiyield.zendesk.com/hc/en-us/requests/new) with the "Public API Request" type.

You will have to use an `api_key` header with your key on every request. For example, on our GraphQL playground, you should test your key as follows:

<figure><img src="../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>

### Pricing

In order to make queries with your API key, you must purchase credits. The more complex your queries, the more credits may be used up when requesting data from our API.

* **credits** - 1 Credit
* **chains** - 1 Credit
* **assets** - 1 Credit
* **assetsPrices** - 1 Credit
* **assetBalances** - 10 Credits
* **protocols** - 1 Credit
* **protocolBalance** - 10 Credits
* **rekts** - 3 Credits
* **shields** - 10 Credits

### Rate Limits

Most queries have a rate limit of 100 requests per minute.

The following queries have a rate limit of 20 requests per minute:

* **assetBalances**
* **protocolBalance**
* **shields**
