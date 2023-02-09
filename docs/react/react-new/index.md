---
title: thirdweb React SDK
hide_title: true
displayed_sidebar: react
---

import Tabs from "@theme/Tabs";
import TabItem from "@theme/TabItem";
import CodeBlock from "@theme/CodeBlock";

<p align="center">
  <br />
  <a href="https://thirdweb.com">
    <img
      src="https://github.com/thirdweb-dev/js/blob/main/packages/sdk/logo.svg?raw=true"
      width="200"
      alt=""
    />
  </a>
  <br />
</p>
<h1 align="center">thirdweb React SDK</h1>
<p align="center">
  A collection of React hooks and UI components for your web3 apps, on{" "}
  <i>any </i>
  blockchain.
</p>
<br />
<div
  align="center"
  style={{
    display: "flex",
    alignItems: "center",
    justifyContent: "center",
  }}
>
  <Tabs>
    <TabItem value="npm" label="npm" default>
      <CodeBlock
        language={"bash"}
      >{`npm i @thirdweb-dev/react @thirdweb-dev/sdk ethers`}</CodeBlock>
    </TabItem>
    <TabItem value="yarn" label="yarn">
      <CodeBlock
        language={"bash"}
      >{`yarn add @thirdweb-dev/react @thirdweb-dev/sdk ethers`}</CodeBlock>
    </TabItem>
    <TabItem value="pnpm" label="pnpm">
      <CodeBlock
        language={"bash"}
      >{`pnpm i @thirdweb-dev/react @thirdweb-dev/sdk ethers`}</CodeBlock>
    </TabItem>
  </Tabs>
</div>
<p align="center" style={{ marginTop: 16 }}>
  <a href="https://github.com/thirdweb-example#starter-kits">Starter Kits</a> •{" "}
  <a href="/templates">Templates</a> •{" "}
  <a href="https://github.com/thirdweb-dev/js"> GitHub Repository</a>
</p>

<hr />

<h2>Get Started</h2>

Wrap your application with the `ThirdwebProvider` component like so:

```jsx title="App.jsx"
import { ThirdwebProvider } from "@thirdweb-dev/react";
const App = () => {
  return (
    <ThirdwebProvider activeChain="ethereum">
      <YourApp />
    </ThirdwebProvider>
  );
};
```

Below are examples of where to set this up in your application.

<p>
  <a href="https://github.com/thirdweb-example/cra-javascript-starter/blob/main/src/index.js">
    Create React App
  </a>{" "}
  •{" "}
  <a href="https://github.com/thirdweb-example/next-javascript-starter/blob/main/pages/_app.js">
    Next.js
  </a>{" "}
  •{" "}
  <a href="https://github.com/thirdweb-example/vite-javascript-starter/blob/main/src/main.jsx">
    Vite
  </a>
</p>

### Using the SDK

That&rsquo;s it! You're now ready to use all the hooks and components in the SDK.

The first thing you likely want to do is connect to a smart contract:

```jsx title="index.jsx"
import { useContract } from "@thirdweb-dev/react";

const Home = () => {
  const { contract, isLoading, error } = useContract(
    "0x6604bd9D7770035f26B4ACeab2C746fdCE16473",
  );

  if (isLoading) return <div>Loading...</div>;
  if (error) return <div>Error: {error.message}</div>;
  return <h1>Contract found!</h1>;
};
```