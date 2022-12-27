# Testing Integrations

Once your module has been setup, you should test it to see if it performs as expected. This can be done through usage of `createTestProject()` in any of your files in `/tests/`. When setting up your integration, a template file should have been created for you in that folder. Use that as a starting point.

{% hint style="info" %}
Feel free to check out other integrations' test files for example on how to test different aspects of your own integration!
{% endhint %}

## Setting Up Tests

Use `createTestProject()` as follows (we're using `Aave` as an example below) to set up the context for your future tests:

```typescript
beforeEach(async (context) => {
  context.project = await createTestProject({
    name: 'Aave',
    path: join(__dirname, "index.ts"),
    modules: [AaveLending, AaveStaking],
    contracts: mockContracts,
  });
});
```

The `mockContracts` variable should be an object containing mock contracts and their respective method responses for any contracts you'd like to emulate. Learn more about these below:

## Creating Mock Contracts

Here's an example of what a mock contract could look like:

```typescript
const mockContracts: MockContracts = {
  '0x8849f1a0cB6b5D6076aB150546EddEe193754F1C': {
    getAllMarkets: () => ['0xdeadbeef', '0xcafebabe'],
    markets: (market: string) => {
      const responses = {
        '0xdeadbeef': { collateralFactorMantissa: 960000000000000000 },
        '0xcafebabe': { collateralFactorMantissa: 630000000000000000 },
      }
      return responses[market]
  },
  fallback: {
    supplyRatePerTimestamp: () => '31500000000',
    borrowRatePerTimestamp: () => '12500000000',
  }
}
```

The mock contract above is for the `0x8849...4F1C` contract, containing mock responses for the `getAllMarkets()` and `markets()` methods.

Below that mock contract you can see some `fallback` responses were set, which are utilized if your integration tests a contract or method that is not included in your `mockContracts` object.

By using these mock contracts, you can also generate other mock data or even mock HTTP responses through the `createMockContext()` function:

## Creating Mock HTTP Calls

Here's an example of what a mock HTTP call could be setup and used within a test:

```typescript
describe("Utils", () => {
  test("fetches pool list from a third party API", async () => {
    const [mockContext, mockAxios] = createMockContext(mockContracts);

    mockAxios.onGet("https://api.beefy.finance/vaults").reply(200, [
      {
        id: "hermes-m.dai-m.usdc",
        tokenAddress: "0x5E985F09c6700FAebAaD4AedC07FA6e218A7ca04",
        earnedTokenAddress: "0x587895668a5db7B3b43F51b9F92460D5BbFD8D89",
        status: "active",
        network: "metis",
        strategy: "0xA15a91C3FB5304d53f9984d045d1B0e631f1E65C",
      },
      {
        id: "hermes-m.usdt-m.usdc",
        tokenAddress: "0xc7C7509D1A192F00C806A0793e5946aae7266D6a",
        earnedTokenAddress: "0xa9Fd735728d65a3D786bE9fEFeCF400d23F46907",
        status: "active",
        network: "metis",
        strategy: "0xcFd89b21405a4BbF9c5b380954BB4F3f55Bb72e5",
      }
    ]);

    const pools = await getPoolList(mockContext);

    expect(pools).toEqual(
      expect.arrayContaining([
        expect.objectContaining({
          id: expect.any(String),
          tokenAddress: expect.any(String),
          earnedTokenAddress: expect.any(String),
          status: expect.any(String),
          network: expect.any(String),
          strategy: expect.any(String),
        }),
      ])
    );
  });
});
```

## API Requests

Throughout your tests, you may notice that token prices are significantly cached. This is because the local repository is using the public API endpoint. If this is an issue for you, you may add your API key to your local setup's \`.env\` file.

To learn more about our API, check out our documentation [**here**](broken-reference).
