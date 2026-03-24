# Robinhood Chain — Developer Skill

> Read this file before building on Robinhood Chain Testnet.

Robinhood Chain is a permissionless, EVM-compatible Layer-2 blockchain built on **Arbitrum Orbit** technology, secured by Ethereum. It is currently **testnet only** — all tokens have no real monetary value and balances may be reset at any time.

---

## Network Parameters

| Parameter | Value |
|---|---|
| Network Name | Robinhood Chain Testnet |
| Chain ID | `46630` |
| Native Token | ETH |
| Public RPC | `https://rpc.testnet.chain.robinhood.com` |
| Alchemy RPC | `https://robinhood-testnet.g.alchemy.com/v2/<YOUR_API_KEY>` |
| Alchemy WebSocket | `wss://robinhood-testnet.g.alchemy.com/v2/<YOUR_API_KEY>` |
| Sequencer Feed | `wss://feed.testnet.chain.robinhood.com` |
| Sequencer | `https://sequencer.testnet.chain.robinhood.com` |
| Block Explorer | `https://explorer.testnet.chain.robinhood.com` |
| Faucet | `https://faucet.testnet.chain.robinhood.com` |

> Use the public RPC for light usage. Use an Alchemy API key for production or heavy traffic.

---

## L2 Token Contracts (Testnet)

| Token | Address |
|---|---|
| WETH | `0x7943e237c7F95DA44E0301572D358911207852Fa` |
| TSLA | `0xC9f9c86933092BbbfFF3CCb4b105A4A94bf3Bd4E` |
| AMZN | `0x5884aD2f920c162CFBbACc88C9C51AA75eC09E02` |
| PLTR | `0x1FBE1a0e43594b3455993B5dE5Fd0A7A266298d0` |
| NFLX | `0x3b8262A63d25f0477c4DDE23F83cfe22Cb768C93` |
| AMD | `0x71178BAc73cBeb415514eB542a8995b82669778d` |

---

## Core Protocol Contracts (L1 Ethereum)

| Contract | Address |
|---|---|
| Rollup | `0xdc5F8E399DBd8a9F5F87AeC4C23Beb12431b386D` |
| Sequencer Inbox | `0xA0D9dB3DC9791D54b5183C1C1866eFe1eCA7D414` |
| CoreProxyAdmin | `0x20d5d542c1bF0a3c295524Eaef336fC07e890622` |
| Delayed Inbox | `0xF2939afA86F6f933A3CE17fCAB007907B6b0B7a4` |
| Bridge | `0x96295BDad104eaD97cC08797b3dC68efF59CcF30` |
| Outbox | `0x8D180Caf588f3Da027BEf1F42a106Da93F90b166` |

---

## Fraud Proof Contracts (L1)

| Contract | Address |
|---|---|
| ChallengeManager | `0xE877c5d3a6829d1D8b06badf309Fc294f3F51ed6` |
| OneStepProver0 | `0x6fE84aC811EBEcd888Eca93757fEa378Bb03b00c` |
| OneStepProverMemory | `0x665CEA1cA6C36aB701f4C6AE895b156f79C51c35` |
| OneStepProverMath | `0x4B15E064d5d55705E89080bDEA4BFe4cF20D6114` |
| OneStepProverHostIo | `0xe1aAfAfBde42f043495B39d1a15a58E91c894Fbf` |
| OneStepProofEntry | `0x5087a6fD526eFD5c6770d94D0c325de0e2A2c44D` |

---

## Token Bridge Contracts

### L1 Gateways (Ethereum)

| Contract | Address |
|---|---|
| L1 Gateway Router | `0xF6F11aAEE80875776C264d93B37B34cE437382D1` |
| L1 ERC20 Gateway | `0x52C2976cbDEf48BcC51d07d3c523769F76ECBd09` |
| L1 Arb-Custom Gateway | `0xFB4aa8024F70B00121723A9C923BaD0Dd2dFaf8F` |
| L1 WETH Gateway | `0x8f8A6799F2b1978c6586318543c73D8Fb12f218f` |

### L2 Gateways (Robinhood Chain)

| Contract | Address |
|---|---|
| L2 Gateway Router | `0x77bF00A6A90c600f214b34BAFBB7918c0cF113A8` |
| L2 ERC20 Gateway | `0x8689aFB9086734e12beA6b5DF541a1da252Ea32a` |
| L2 Arb-Custom Gateway | `0xE4EE9C15e2cA44136796342e31b67d953E67a70b` |
| L2 WETH Gateway | `0x5A8F55202A625D12FFCb76F857FE4563bC8Ce413` |

---

## Deploy Smart Contracts (Foundry)

### 1. Install Foundry

```bash
curl -L https://foundry.paradigm.xyz | bash
foundryup
```

### 2. Create a project

```bash
forge init my-project
cd my-project
```

### 3. Set environment variables

```bash
export RH_RPC_URL=https://rpc.testnet.chain.robinhood.com
export PRIVATE_KEY=<your_private_key>
```

### 4. Deploy

```bash
forge create src/MyContract.sol:MyContract \
  --rpc-url $RH_RPC_URL \
  --private-key $PRIVATE_KEY \
  --broadcast
```

### 5. Verify on explorer

```bash
forge verify-contract <DEPLOYED_ADDRESS> \
  src/MyContract.sol:MyContract \
  --chain-id 46630 \
  --rpc-url $RH_RPC_URL \
  --verifier blockscout \
  --verifier-url https://explorer.testnet.chain.robinhood.com/api/
```

### Get testnet ETH

Visit `https://faucet.testnet.chain.robinhood.com` to fund your wallet.

---

## Wallet Setup

### MetaMask (or any EVM wallet)

Add network manually:
- **Network Name**: Robinhood Chain Testnet
- **RPC URL**: `https://rpc.testnet.chain.robinhood.com`
- **Chain ID**: `46630`
- **Currency Symbol**: `ETH`
- **Block Explorer**: `https://explorer.testnet.chain.robinhood.com`

### Robinhood Wallet (iOS / Android)

Enable developer testnet settings in the app to connect natively.

---

## Alchemy Services

When using an Alchemy API key, these services are available on Robinhood Chain Testnet:

- **Node API** — standard JSON-RPC access
- **Bundler API** — ERC-4337 UserOperation submission
- **Smart Wallets** — account abstraction with gas sponsorship
- **Gas Manager** — fee sponsorship for end users

---

## Support & Resources

| Resource | Link |
|---|---|
| Docs | `https://docs.robinhood.com/chain` |
| Block Explorer | `https://explorer.testnet.chain.robinhood.com` |
| Faucet | `https://faucet.testnet.chain.robinhood.com` |
| Developer Email | `chain-developers-group@robinhood.com` |
| Interest Form | `https://go.robinhood.com/chain-interest-form` |

---

## Key Reminders

- **Testnet only** — no real value, no real assets
- Testnet token balances can be modified, reset, or deleted at any time
- Robinhood Chain is built on Arbitrum Orbit — consult Arbitrum docs for advanced node/infrastructure topics
- For security issues, bugs, or partnership inquiries: `chain-developers-group@robinhood.com`
