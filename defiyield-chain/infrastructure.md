# Infrastructure

{% hint style="warning" %}
The DeFiYield Chain is still under development. Information on this page may change.
{% endhint %}

The DeFiYield Chain is how we decentralize our safety tools and smart contract scanning capabilities. Join us in order to be a part of the future of safety in DeFi!

![Basic DeFiYield Chain Infrastructure](<../.gitbook/assets/image (36).png>)

## Roles

The chain functions as a delegated proof of stake blockchain, where the following roles are present:

### Indexers

Indexers are node operators in the DeFiYield Chain - scanning smart contracts and verifying the accuracy of other indexers' scans.

In order to become an indexer, one needs to stake DEFI tokens, which also serve as an incentive to keep indexers honest towards their scan results. Slashing is enabled for those that manipulate their results in order to deceive others with any contract's fake security score.

Not only will the indexer gain DEFI tokens for their scanning services, but when the contract an indexer has scanned is queried by a user in order to gauge its safety, they gain a portion of query fees in the form of DEFI as well.

### Delegators

Delegators can stake DEFI alongside any indexers' stake - essentially adding their stake to theirs without having to run a node of their own. When indexers gain DEFI tokens, delegators to that indexer would gain a portion of those tokens based on how much they had delegated.

### Developers / Contributors

Developers and/or contributors can provide and contribute to the code indexers use to scan smart contracts. This can lead to the developer to gain a portion of query fees in DEFI for their contribution.

## Functionality

Our infrastructure facilitates a decentralized manner with which to deal with verifiably scanning smart contracts and making them available for others to query at any time.

### Submissions

Much like transactions in a traditional blockchain, users are able to submit smart contracts in order to have them scanned through our indexers. This will cost some DEFI tokens - essentially as gas fees - which are then distributed to our indexers and delegators.

### Queries

Our chain will expose the verified results of any of our scans in order to have them able to be queried at any moment. Querying the safety score/report of any of our scanned contracts will cost some DEFI tokens for its execution, which are then distributed to our indexers, delegators and developers as query fees.

