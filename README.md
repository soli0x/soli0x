<h1 align="center">Toll</h1>

<p align="center"><b>the safety layer for agentic finance on Robinhood Chain (chain 4663).</b><br/>the check an AI agent calls before it buys, signs or pays. chain facts, not advice.</p>

<p align="center">
<a href="https://t0ll.xyz"><img alt="t0ll.xyz" src="https://img.shields.io/badge/t0ll.xyz-live-0b0b0b?style=for-the-badge"/></a>
<a href="https://t0ll.xyz/agents"><img alt="ERC-8004 agent #20030" src="https://img.shields.io/badge/ERC--8004-agent%20%2320030-6250d6?style=for-the-badge&logo=ethereum&logoColor=white"/></a>
<a href="https://x.com/Tollxyz_"><img alt="X @Tollxyz_" src="https://img.shields.io/badge/X-%40Tollxyz__-0b0b0b?style=for-the-badge&logo=x&logoColor=white"/></a>
</p>

<p align="center">
<a href="https://t0ll.xyz/llms.txt"><img alt="MCP: 24 tools, no auth" src="https://img.shields.io/badge/MCP-24%20tools%20%C2%B7%20no%20auth-2f6feb?style=for-the-badge"/></a>
<a href="https://x402.t0ll.xyz"><img alt="x402 facilitator" src="https://img.shields.io/badge/x402-facilitator%20%C2%B7%20USDG-1f883d?style=for-the-badge"/></a>
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

we build Toll. an agent about to trade on Robinhood Chain asks Toll first and gets one word back: **BLOCK**, **WARN**, **ALLOW** or **WAIT**, with the reasons read from the chain. the same check runs before a transaction is signed and before an x402 payment goes out.

we also write the standards behind it, so any wallet, agent or facilitator can read the same facts. three ERC drafts are open at [ethereum/ERCs](https://github.com/ethereum/ERCs), all running in Toll today.

## Start here

| | |
|---|---|
| **remote MCP** | `https://t0ll.xyz/mcp` · 24 tools, no auth · official MCP registry: `io.github.t0ll-xyz/toll` |
| **guard a wallet** | `npm i @tollxyz/guard` · wraps viem wallets and x402 fetch, blocks high-risk by default |
| **REST** | [OpenAPI](https://t0ll.xyz/openapi.json) · [llms.txt](https://t0ll.xyz/llms.txt) |
| **A2A** | [agent card](https://t0ll.xyz/.well-known/agent-card.json) |
| **pay an agent safely** | [x402.t0ll.xyz](https://x402.t0ll.xyz) · USDG on Robinhood Chain |
| **alerts** | [t.me/t0ll_bot](https://t.me/t0ll_bot) · watch webhooks + Telegram |

## What it checks

| tool | what it reads | answer |
|---|---|---|
| `check_coin` / `pre_buy_check` | rug, bundles, snipers, dev record, LP pull, fee-trap v4 hooks, sells that fail | BLOCK / WARN / ALLOW / WAIT |
| `check_tx` | transactions, EIP-712 signatures, x402 payments, before they are signed | ERC-8265 RiskAssessment ALLOW / WARN / BLOCK + signed ERC-8481 report |
| `check_agent` | ERC-8004 agents: card, MCP/x402 endpoints, payee vs agentWallet | facts with date and source |
| `check_hook` | Uniswap v4 hooks: permissions, upgradability, failing sells | facts |
| `stock_token` | Robinhood Stock Tokens: Chainlink reference vs pool price | facts with source and time |
| `watch_coin` | webhooks + Telegram alerts when a watched coin changes | alert |

<details>
<summary>pre-sign rules worth knowing</summary>

- EIP-7702 delegations are blocked.
- undecoded calls that carry value are blocked.
- every report is EIP-712 signed and bound to the request digest (ERC-8481).
- transaction simulation is coming.

</details>

## x402 facilitator

[x402.t0ll.xyz](https://x402.t0ll.xyz) settles USDG on Robinhood Chain. before it settles, it checks that the payee is the seller's registered ERC-8004 agentWallet (ERC-8478), so a swapped payTo never gets paid.

## Open source

Everything an agent needs to call Toll lives in [t0ll-xyz/toll-plugins](https://github.com/t0ll-xyz/toll-plugins).

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
| examples | OpenAI Agents SDK, CrewAI · Hermes agent catalog |

also: [soli0x/toll-launch-check](https://github.com/soli0x/toll-launch-check), a Uniswap v4 hook that refuses buys in bundled launches, read from the ERC-8470 registry.

</details>

## ERC updates

All Draft at [ethereum/ERCs](https://github.com/ethereum/ERCs). dates are the PR's last update (UTC).

| ERC | title | status | PR | last update |
|---|---|---|---|---|
| ERC-8470 | Token Launch Observations | Draft · PR open | [#2121](https://github.com/ethereum/ERCs/pull/2121) · [forum](https://ethereum-magicians.org/t/pre-erc-launch-observations-the-check-an-agent-reads-before-it-buys-a-token/30112) | 2026-11-04 |
| ERC-8478 | x402 Payee Verification for ERC-8004 Agents | Draft · PR open | [#2132](https://github.com/ethereum/ERCs/pull/2132) | 2026-11-02 |
| ERC-8481 | Agent Pre-Sign Risk Report | Draft · PR open | [#2134](https://github.com/ethereum/ERCs/pull/2134) | 2026-11-05 |

<details>
<summary>other contributions</summary>

| repo | PR | status | last update |
|---|---|---|---|
| x402-foundation/x402 | [#4084 docs: add Toll Facilitator (Robinhood Chain, USDG)](https://github.com/x402-foundation/x402/pull/4084) | open | 2026-11-05 |
| priors-agents/priors | [#26 x402: beforePay hook + optional payee check](https://github.com/priors-agents/priors/pull/26) | approved, credited in their next release | 2026-11-07 |

</details>

## Integrations

- [hookr.fun/integrations](https://hookr.fun/integrations) · listed in the Hookr universe, Agents.
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

<p align="center"><sub><a href="https://t0ll.xyz">t0ll.xyz</a> · ERC-8004 agent #20030 on Robinhood Chain · ERC table last refreshed 2026-11-08 UTC</sub></p>
