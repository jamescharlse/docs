---
slug: /react.thirdwebprovider
title: ThirdwebProvider
displayed_sidebar: react
---

import Tabs from "@theme/Tabs";
import TabItem from "@theme/TabItem";
import CodeBlock from "@theme/CodeBlock";

The `ThirdwebProvider` is a wrapper component that provides access to all of the SDK&rsquo;s hooks and UI components.
It utilizes the [Provider Pattern](https://www.patterns.dev/posts/provider-pattern/)
to share data with all of the components that are nested within it.

Wrap your app in the `ThirdwebProvider` to access the SDK&rsquo;s functionality from anywhere in your app.

## Usage

If you are using one of our <code>default chains</code>, provide the `activeChain` prop to the `ThirdwebProvider` component.

For non-default chains, see [configuring active chains](#active-chain) or [custom chains](#custom-chains).

<details>
  <summary>View default chains</summary>
  <div>
    <ul>
      <li>
        <b>Ethereum</b>: <code>"ethereum"</code>
      </li>
      <li>
        <b>Goerli</b>: <code>"goerli"</code>
      </li>
      <li>
        <b>Polygon</b>: <code>"polygon"</code>
      </li>
      <li>
        <b>Mumbai</b>: <code>"mumbai"</code>
      </li>
      <li>
        <b>Arbitrum One</b>: <code>"arbitrum"</code>
      </li>
      <li>
        <b>Arbitrum Goerli</b>: <code>"arbitrum-goerli"</code>
      </li>
      <li>
        <b>Optimism</b>: <code>"optimism"</code>
      </li>
      <li>
        <b>Optimism Goerli Testnet</b>: <code>"optimism-goerli"</code>
      </li>
      <li>
        <b>Binance SmartChain</b>: <code>"binance"</code>
      </li>
      <li>
        <b>Binance SmartChain Testnet</b>: <code>"binance-testnet"</code>
      </li>
      <li>
        <b>Fantom Opera</b>: <code>"fantom"</code>
      </li>
      <li>
        <b>Fantom Testnet</b>: <code>"fantom-testnet"</code>
      </li>
      <li>
        <b>Avalanche C Chain</b>: <code>"avalanche-fuji"</code>
      </li>
      <li>
        <b>Avalanche Fuji Testnet</b>: <code>"avalanche-fuji-testnet"</code>
      </li>
      <li>
        <b>Localhost</b>: <code>"localhost"</code>
      </li>
    </ul>
  </div>
</details>

```jsx
import { ThirdwebProvider } from "@thirdweb-dev/react";
function App() {
  return (
    <ThirdwebProvider activeChain="ethereum">
      <YourApp />
    </ThirdwebProvider>
  );
}
```

## Configuration

### Active Chain

The `activeChain` prop determines which chain you want your app to be operating on.

:::info Available Chains
There are 700+ chains available in the [`@thirdweb-dev/chains`](https://github.com/thirdweb-dev/js/tree/main/packages/chains) package.

If your chain is not included, see [configuring custom chains](#custom-chains).
:::

```jsx
import { ThirdwebProvider } from "@thirdweb-dev/react";
// highlight-start
import { Gnosis } from "@thirdweb-dev/chains";
// highlight-end
function MyApp() {
  return (
    <ThirdwebProvider
      // highlight-start
      activeChain={Gnosis}
      // highlight-end
    >
      <YourApp />
    </ThirdwebProvider>
  );
}
```

### Custom Chains

If your chain is not included in the `@thirdweb-dev/chains` package,
you can provide the chain information yourself to the `activeChain` prop.

```js
import { ThirdwebProvider } from "@thirdweb-dev/react";
const App = () => {
  return (
    <ThirdwebProvider
      activeChain={{
        // === Required information for connecting to the network === \\
        chainId: 59140, // Chain ID of the network
        // Array of RPC URLs to use
        rpc: ["<your-rpc-url-here>"],
        // === Information for adding the network to your wallet (how it will appear for first time users) === \\
        // Information about the chains native currency (i.e. the currency that is used to pay for gas)
        nativeCurrency: {
          decimals: 18,
          name: "Consensys ETH",
          symbol: "crETH",
        },
        shortName: "czkevm", // Display value shown in the wallet UI
        slug: "consensys", // Display value shown in the wallet UI
        testnet: true, // Boolean indicating whether the chain is a testnet or mainnet
        chain: "ConsenSys", // Name of the network
        name: "ConsenSys zkEVM Testnet", // Name of the network
      }}
    >
      <YourApp />
    </ThirdwebProvider>
  );
};
```

<!-- ### Multiple Networks
The `chains` prop defines which networks your app supports.
Provide multiple networks to the `chains` prop to allow users to switch between them.
- If you provide both `network` and `chains` props, the SDK uses the `network` value as the network your app is **currently** operating on.
- If you do _not_ provide a `network`, the SDK will default to the first network in the `chains` array as the network your app is **currently** operating on.
```jsx
import { ThirdwebProvider } from "@thirdweb-dev/react";
// highlight-start
import { Mumbai, Polygon } from "@thirdweb-dev/chains";
// highlight-end
function MyApp() {
  return (
    <ThirdwebProvider
      // highlight-start
      activeChain={Mumbai.chainId} // The network that the SDK will use at this point in time.
      chains={[Polygon, Mumbai]} // Allow users to switch between Polygon and Mumbai networks.
      // highlight-end
    >
      <YourApp />
    </ThirdwebProvider>
  );
}
```
:::tip Helper Values
The `@thirdweb-dev/chains` package also exposes:
- `defaultChains`: An array that contains all of the most common networks.
- `allChains`: An array that contains all of the networks the SDK is aware of by default.
```jsx
import { defaultChains, allChains } from "@thirdweb-dev/chains";
```
::: -->

### Override Default Values

Override the default values (such as an RPC URL) for any given chain.

:::info Optional
By default, the SDK provides free-to-use RPCs. No configuration required!

[View the default RPC URLs for each network](https://github.com/thirdweb-dev/js/tree/main/packages/chains/chains).
:::

Using the [spread syntax](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Spread_syntax),
you can override any properties of a chain, such as the `rpc` field.

```jsx
import { ThirdwebProvider } from "@thirdweb-dev/react";
import { Dogechain } from "@thirdweb-dev/chains";
const App = () => {
  return (
    <ThirdwebProvider
      activeChain={{
        // highlight-start
        ...Dogechain,
        rpc: ["https://<your-rpc-to-use>.com"], // Override the "rpc" field.
        // ... Override any other fields you want to customize.
        // highlight-end
      }}
    >
      <YourApp />
    </ThirdwebProvider>
  );
};
```

### authConfig

The configuration object for setting up [Auth](/auth); allowing users to sign in with their wallet.

| Property  | Type   | Description                                                                                                                                                                |
| --------- | ------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `authUrl` | string | The backend URL of the authentication endpoints. For example, if your endpoints are at `/api/auth/login`, `/api/auth/logout`, etc. then this should be set to `/api/auth`. |
| `domain`  | string | The frontend domain used to generate the login payload. This domain should match the domain used on your auth backend.                                                     |

```jsx
import type { AppProps } from "next/app";
import { ThirdwebProvider } from "@thirdweb-dev/react";
function MyApp({ Component, pageProps }: AppProps) {
  return (
    <ThirdwebProvider
      // highlight-start
      authConfig={{
        authUrl: "/api/auth",
        domain: "https://example.com",
      }}
      // highlight-end
    >
      <YourApp />
    </ThirdwebProvider>
  );
}
```

### autoconnect

When the user has connected their wallet to your site before, this flag determines
whether or not you want the SDK to automatically connect to the wallet on page load (requires the user
to be logged in to the wallet).

Defaults to `true`.

```jsx
import { ThirdwebProvider } from "@thirdweb-dev/react";
function MyApp() {
  return (
    <ThirdwebProvider
      // highlight-start
      autoConnect={false}
      // highlight-end
    >
      <YourApp />
    </ThirdwebProvider>
  );
}
```

### dAppMeta

Metadata to pass to [WalletConnect](https://walletconnect.com/), shown in mobile wallets that support it.

Defaults to `thirdweb powered dApp`.

| Property      | Type    | Description                                                      |
| ------------- | ------- | ---------------------------------------------------------------- |
| `name`        | string  | the name of your app                                             |
| `description` | string  | optional - a description of your app                             |
| `logoUrl`     | string  | optional - a url that points to a logo (or favicon) of your app  |
| `url`         | string  | optional - the url where your app is hosted                      |
| `isDarkMode`  | boolean | optional - whether to show the connect dialog in darkmode or not |

```jsx
import { ThirdwebProvider } from "@thirdweb-dev/react";
function MyApp() {
  return (
    <ThirdwebProvider
      // highlight-start
      dAppMeta={{
        name: "My App",
        description: "My app description",
        logoUrl: "https://example.com/logo.png",
        url: "https://example.com",
        isDarkMode: true,
      }}
      // highlight-end
    >
      <YourApp />
    </ThirdwebProvider>
  );
}
```

### sdkOptions

Override any of the default values for the SDK.

Gas settings, gasless transactions, RPC configuration, and more.

```jsx
import { ThirdwebProvider } from "@thirdweb-dev/react";
function MyApp() {
  return (
    <ThirdwebProvider
      // highlight-start
      sdkOptions={{
        readonlySettings: {
          rpcUrl: "<rpc-url>", // force read calls to go through your own RPC url
          chainId: 1, // reduce RPC calls by sepcifying your chain ID
        },
        gasSettings: {
          maxPriceInGwei: 123, // Maximum gas price for transactions (default 300 gwei)
          speed: "fastest", // the tx speed setting: 'standard'|'fast|'fastest' (default: 'fastest')
        },
        gasless: {
          // By specifying a gasless configuration - all transactions will get forwarded to enable gasless transactions
          openzeppelin: {
            relayerUrl: "<open-zeppelin-relayer-url>", // your OZ Defender relayer URL
            relayerForwarderAddress: "<open-zeppelin-forwarder-address>", // the OZ defender relayer address (defaults to the standard one)
          },
          biconomy: {
            apiId: "biconomy-api-id", // your Biconomy API Id
            apiKey: "biconomy-api-key", // your Biconomy API Key
            deadlineSeconds: 123, // your Biconomy timeout preference
          },
        },
        infuraApiKey: "<infura-api-key>", // your Infura API key
        alchemyApiKey: "<alchemy-api-key>", // your Alchemy API key
        thirdwebApiKey: "<thirdweb-api-key>", // your thirdweb API key
      }}
      // highlight-end
    >
      <YourApp />
    </ThirdwebProvider>
  );
}
```

### walletConnectors

An array of connector types (strings) or wallet connector objects that your app supports.

If not provided, defaults to MetaMask (injected), WalletConnect and Coinbase Wallet.

Useful if you want to add support for [Gnosis Safe](https://gnosis-safe.io/) or [Magic Link](https://magic.link/).

```jsx title="Magic Link example"
import { ThirdwebProvider } from "@thirdweb-dev/react";
import { MagicConnector } from "@thirdweb-dev/react/evm/connectors/magic";
import { Mumbai } from "@thirdweb-dev/chains";
const magicLinkConnector = new MagicConnector({
  options: {
    apiKey: "<your-magic-link-public-key>" as string,
    rpcUrls: {
      [Mumbai.chainId]: "https://mumbai.magic.io/rpc",
    },
  },
});
function MyApp() {
  return (
    <ThirdwebProvider
      // highlight-start
      walletConnectors={[magicLinkConnector, "metamask", "walletConnect", "coinbaseWallet"]}
      // highlight-end
      activeChain={"mumbai"}
    >
      <YourApp />
    </ThirdwebProvider>
  );
}
export default MyApp;
```

### storageInterface

Override the default [Storage](/storage) interface used by the SDK.

Allows you to create an instance of `ThirdwebStorage` with your own customized config, and pass it to the SDK.

:::tip Storage

This requires the `@thirdweb-dev/storage` package to be installed.

[Learn more about Storage](/storage)

:::

```jsx
import { ThirdwebProvider } from "@thirdweb-dev/react";
import {
  ThirdwebStorage,
  StorageDownloader,
  IpfsUploader,
} from "@thirdweb-dev/storage";
// Configure a custom ThirdwebStorage instance
const gatewayUrls = {
  "ipfs://": [
    "https://gateway.ipfscdn.io/ipfs/",
    "https://cloudflare-ipfs.com/ipfs/",
    "https://ipfs.io/ipfs/",
  ],
};
const downloader = new StorageDownloader();
const uploader = new IpfsUploader();
const storage = new ThirdwebStorage({ uploader, downloader, gatewayUrls });
// Provide the custom storage instance to the SDK
function MyApp() {
  return (
    <ThirdwebProvider
      // highlight-start
      storageInterface={storage}
      // highlight-end
    >
      <YourApp />
    </ThirdwebProvider>
  );
}
```

### queryClient

If you are using [React Query](https://react-query.tanstack.com/) and have your own `QueryClient`,
you can pass it as the `queryClient` prop to use this client instead of the SDK's default client.

```jsx
import { ThirdwebProvider } from "@thirdweb-dev/react";
import { QueryClient, QueryClientProvider } from "@tanstack/react-query";
function MyApp() {
  // Your React Query client (or client from other library such as wagmi)
  const queryClient = new QueryClient();
  return (
    <QueryClientProvider client={queryClient}>
      <ThirdwebProvider
        // highlight-start
        queryClient={queryClient}
        // highlight-end
      >
        <YourApp />
      </ThirdwebProvider>
    </QueryClientProvider>
  );
}
```