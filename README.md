<h1 align="center">Toll</h1>

<p align="center"><b>the safety layer for agentic finance on Robinhood Chain (chain 4663).</b><br/>the check an AI agent calls before it buys, signs or pays. chain facts, not advice.</p>

<p align="center">
<a href="https://t0ll.xyz"><img alt="t0ll.xyz" src="https://img.shields.io/badge/t0ll.xyz-live-0b0b0b?style=for-the-badge"/></a>
<a href="https://t0ll.xyz/agents"><img alt="ERC-8004 agent #20030" src="https://img.shields.io/badge/ERC--8004-agent%20%2320030-6250d6?style=for-the-badge&logo=ethereum&logoColor=white"/></a>
<a href="https://x.com/Tollxyz_"><img alt="X @Tollxyz_" src="https://img.shields.io/badge/X-%40Tollxyz__-0b0b0b?style=for-the-badge&logo=x&logoColor=white"/></a>
</p>

<p align="center">
<a href="https://t0ll.xyz/llms.txt"><img alt="MCP: 28 tools, no auth" src="https://img.shields.io/badge/MCP-28%20tools%20%C2%B7%20no%20auth-2f6feb?style=for-the-badge"/></a>
<a href="https://x402.t0ll.xyz"><img alt="x402 facilitator" src="https://img.shields.io/badge/x402-facilitator%20%C2%B7%20USDG-1f883d?style=for-the-badge"/></a>
<a href="#on-chain"><img alt="4 contracts on Robinhood Chain" src="https://img.shields.io/badge/contracts-4%20live%20%C2%B7%20Sourcify-0b7a75?style=for-the-badge"/></a>
<a href="#erc-updates"><img alt="3 ERC drafts" src="https://img.shields.io/badge/ERCs-3%20drafts%20open-cf222e?style=for-the-badge"/></a>
</p>

<p align="center">
<a href="https://www.npmjs.com/package/@tollxyz/sdk"><img alt="npm @tollxyz/sdk" src="https://img.shields.io/npm/v/@tollxyz/sdk?style=flat-square&label=%40tollxyz%2Fsdk&logo=npm"/></a>
<a href="https://www.npmjs.com/package/@tollxyz/guard"><img alt="npm @tollxyz/guard" src="https://img.shields.io/npm/v/@tollxyz/guard?style=flat-square&label=%40tollxyz%2Fguard&logo=npm"/></a>
<a href="https://www.npmjs.com/package/@tollxyz/mcp"><img alt="npm @tollxyz/mcp" src="https://img.shields.io/npm/v/@tollxyz/mcp?style=flat-square&label=%40tollxyz%2Fmcp&logo=npm"/></a>
<a href="https://pypi.org/project/toll-sdk/"><img alt="PyPI toll-sdk" src="https://img.shields.io/pypi/v/toll-sdk?style=flat-square&label=toll-sdk&logo=pypi&logoColor=white"/></a>
<a href="https://github.com/t0ll-xyz/toll-plugins"><img alt="toll-plugins stars" src="https://img.shields.io/github/stars/t0ll-xyz/toll-plugins?style=flat-square&logo=github&label=toll-plugins"/></a>
</p>

## About

we build Toll. an agent about to trade on Robinhood Chain asks Toll first and gets one word back: **BLOCK**, **WARN**, **ALLOW** or **WAIT**, with the reasons read from the chain. the same check runs before a transaction is signed and before an x402 payment goes out, and after the trade it keeps watching the coin and the wallet.

we also write the standards behind it, so any wallet, agent or facilitator can read the same facts. three ERC drafts are open at [ethereum/ERCs](https://github.com/ethereum/ERCs), all running in Toll today.

## Start here

| | |
|---|---|
| **remote MCP** | `https://t0ll.xyz/mcp` · 28 tools, no auth · official MCP registry: `io.github.t0ll-xyz/toll` |
| **guard a wallet** | `npm i @tollxyz/guard` · wraps viem wallets and x402 fetch, blocks high-risk by default |
| **REST** | [OpenAPI](https://t0ll.xyz/openapi.json) · [llms.txt](https://t0ll.xyz/llms.txt) |
| **A2A** | [agent card](https://t0ll.xyz/.well-known/agent-card.json) |
| **protect RPC** | `https://rpc.t0ll.xyz` · a drop-in wallet RPC that refuses a transaction Toll would BLOCK |
| **pay an agent safely** | [x402.t0ll.xyz](https://x402.t0ll.xyz) · USDG on Robinhood Chain, `exact` and `upto` |
| **launch a paid agent** | [x402.t0ll.xyz/x402/launch](https://x402.t0ll.xyz/x402/launch) · 11 templates, verified from the first call, free test launch |
| **alerts** | [t.me/t0ll_bot](https://t.me/t0ll_bot) · watch webhooks + Telegram |

## What it checks

| tool | what it reads | answer |
|---|---|---|
| `check_coin` / `pre_buy_check` | rug, bundles, snipers, dev record, LP pull, fee-trap v4 hooks, sells that fail | BLOCK / WARN / ALLOW / WAIT |
| `check_tx` | transactions, EIP-712 signatures, x402 payments, before they are signed | ERC-8265 RiskAssessment ALLOW / WARN / BLOCK + signed ERC-8481 report |
| `check_agent` | ERC-8004 agents: card, MCP/x402 endpoints, payee vs agentWallet | facts with date and source |
| `check_hook` | Uniswap v4 hooks: permissions, upgradability, failing sells | facts |
| `stock_token` | Robinhood Stock Tokens: Chainlink reference vs pool price | facts with source and time |
| `watch_coin` / `watch_wallet` | webhooks + Telegram alerts when a watched coin or wallet changes (dev sold, new approval, risky token in) | alert |
| `wallet_approvals` | live ERC-20, NFT and Permit2 approvals, a risk for each, the revoke tx | facts + revoke |
| [blocklist](https://t0ll.xyz/blocklist) | every address Toll has flagged, open as json / csv / txt | list |

<details>
<summary>pre-sign rules worth knowing</summary>

- EIP-7702 delegations are blocked.
- undecoded calls that carry value are blocked.
- every report is EIP-712 signed and bound to the request digest (ERC-8481).
- every transaction is simulated at the current block (balance changes, approvals, revert) and can be checked against the agent's stated intent; a failed simulation is never ALLOW.

</details>

## x402 facilitator

[x402.t0ll.xyz](https://x402.t0ll.xyz) settles USDG on Robinhood Chain, schemes `exact` (EIP-3009 or Permit2), `upto` (Permit2: the buyer signs a maximum, the seller takes only the real cost), escrow with refunds, and batch settlement. before it settles, it checks that the payee is the seller's registered ERC-8004 agentWallet (ERC-8478), so a swapped payTo never gets paid, and every settlement gets a signed Toll receipt. outside sellers settle through it since 12 Nov 2026.

launch your own paid agent in 5 minutes at [x402.t0ll.xyz/x402/launch](https://x402.t0ll.xyz/x402/launch): pick one of 11 templates ([t0ll-xyz/toll-agent-templates](https://github.com/t0ll-xyz/toll-agent-templates)), set a price, sign. its ERC-8004 identity is minted, its payout wallet bound to it, and it is listed where agents buy.

## On-chain

All on Robinhood Chain (4663), source verified on Sourcify (exact match), no owner and no admin. code: [t0ll-xyz/toll-allow](https://github.com/t0ll-xyz/toll-allow).

| contract | what it does | address |
|---|---|---|
| `TollAllowEnforcer` | MetaMask delegation caveat: the delegated call needs Toll's signed ALLOW | [`0x6290…fdb5`](https://robinhoodchain.blockscout.com/address/0x6290dfc474f566b3bf612ad78e9dd3890473fdb5) |
| `TollGateHook` | Uniswap v4 hook: each swap in a pool that uses it needs an ALLOW for that exact swap | [`0x0832…4080`](https://robinhoodchain.blockscout.com/address/0x08324e1aDeC7a4047D2DA692d02B891179B14080) |
| `TollAllowModule` | ERC-7579 smart-account module: each executed call needs an ALLOW | [`0xa869…72fd`](https://robinhoodchain.blockscout.com/address/0xa86955745ff2caffed94ee3c363fd86091a972fd) |
| `TollAssert` | post-trade checks in the same tx: balances moved as simulated, no approval left behind | [`0x7623…e1b1`](https://robinhoodchain.blockscout.com/address/0x7623a849b2c5fa6f6765163bf4bf66aef16fe1b1) |

## Open source

All public code is in the [t0ll-xyz](https://github.com/t0ll-xyz) organization. Everything an agent needs to call Toll lives in [t0ll-xyz/toll-plugins](https://github.com/t0ll-xyz/toll-plugins); the MCP server is [t0ll-xyz/toll-mcp](https://github.com/t0ll-xyz/toll-mcp); the contracts are [t0ll-xyz/toll-allow](https://github.com/t0ll-xyz/toll-allow).

<details open>
<summary>packages and examples</summary>

| package | for |
|---|---|
| [`@tollxyz/sdk`](https://www.npmjs.com/package/@tollxyz/sdk) | typed client for every check |
| [`@tollxyz/guard`](https://www.npmjs.com/package/@tollxyz/guard) | wraps viem wallets + x402 fetch, blocks high-risk by default |
| [`@tollxyz/mcp`](https://www.npmjs.com/package/@tollxyz/mcp) | local MCP server |
| [`@tollxyz/agentkit`](https://www.npmjs.com/package/@tollxyz/agentkit) | Coinbase AgentKit |
| [`@tollxyz/ai-sdk`](https://www.npmjs.com/package/@tollxyz/ai-sdk) | Vercel AI SDK |
| [`@tollxyz/langchain`](https://www.npmjs.com/package/@tollxyz/langchain) | LangChain |
| [`@tollxyz/mastra`](https://www.npmjs.com/package/@tollxyz/mastra) | Mastra |
| [`@tollxyz/plugin-elizaos`](https://www.npmjs.com/package/@tollxyz/plugin-elizaos) | ElizaOS |
| [`toll-sdk`](https://pypi.org/project/toll-sdk/) | Python |
| examples | OpenAI Agents SDK, CrewAI · [toll-x402-examples](https://github.com/t0ll-xyz/toll-x402-examples) |
| Hermes Agent | `hermes plugins install toll` (Hermes plugin catalog) |

also: [t0ll-xyz/toll-launch-check](https://github.com/t0ll-xyz/toll-launch-check), a Uniswap v4 hook that refuses buys in bundled launches, read from the ERC-8470 registry.

</details>

## ERC updates

All Draft at [ethereum/ERCs](https://github.com/ethereum/ERCs). dates are the PR's last update (UTC).

| ERC | title | status | PR | last update |
|---|---|---|---|---|
| ERC-8470 | Token Launch Observations | Draft · PR open | [#2121](https://github.com/ethereum/ERCs/pull/2121) · [forum](https://ethereum-magicians.org/t/pre-erc-launch-observations-the-check-an-agent-reads-before-it-buys-a-token/30112) | 2026-11-09 |
| ERC-8478 | x402 Payee Verification for ERC-8004 Agents | Draft · PR open | [#2132](https://github.com/ethereum/ERCs/pull/2132) | 2026-11-09 |
| ERC-8481 | Agent Pre-Sign Risk Report | Draft · PR open | [#2134](https://github.com/ethereum/ERCs/pull/2134) | 2026-11-09 |

<details>
<summary>other contributions</summary>

| repo | PR | status | last update |
|---|---|---|---|
| x402-foundation/x402 | [#4084 docs: add Toll Facilitator (Robinhood Chain, USDG)](https://github.com/x402-foundation/x402/pull/4084) | open | 2026-11-09 |
| Hookr-fun/hookr-contracts | [#23 labs: toll-launch-check](https://github.com/Hookr-fun/hookr-contracts/pull/23) | open | 2026-11-09 |
| NousResearch/hermes-agent | [#155012 plugin catalog: toll 0.3.0](https://github.com/NousResearch/hermes-agent/pull/155012) | open | 2026-11-13 |
| priors-agents/priors | [#26 x402: beforePay hook + optional payee check](https://github.com/priors-agents/priors/pull/26) | approved, credited in their next release | 2026-11-07 |

</details>

## Integrations

- [hookr.fun/integrations](https://hookr.fun/integrations) · live app integrator: every call Hookr's MCP builds is checked by `check_tx` before it is signed.
- Hermes Agent · Toll plugin in the Hermes plugin catalog.
- Priors · x402 `beforePay` hook, credited in their next release.

## Pricing

| tier | price |
|---|---|
| free | free tier on every surface |
| per check | 0.005 USDG over x402 |
| integrators | free partner keys |

## Say hi

building an agent, wallet or launchpad on Robinhood Chain and want the check in front of it? reach us on [X @Tollxyz_](https://x.com/Tollxyz_) or at T0llxyz@outlook.com.

agents and LLM tooling can read Toll directly: [llms.txt](https://t0ll.xyz/llms.txt), [openapi.json](https://t0ll.xyz/openapi.json), [agent card](https://t0ll.xyz/.well-known/agent-card.json).

<p align="center"><sub><a href="https://t0ll.xyz">t0ll.xyz</a> · ERC-8004 agent #20030 on Robinhood Chain · last refreshed 2026-11-13 UTC</sub></p>
