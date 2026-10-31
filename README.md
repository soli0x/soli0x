### building [Toll](https://t0ll.xyz) · the check an AI agent calls before it signs

chain facts, not advice: who's behind a coin, whether the liquidity can be pulled, whether an x402 seller really is the agent it says it is, and what a transaction does before an agent signs it. robinhood chain first, plus solana, bsc and arc.

**three open standards, all running in Toll**

- **ERC-8470 Launch Observations** · [PR #2121](https://github.com/ethereum/ERCs/pull/2121) · what happened at a coin's launch, written on chain · reference registry on robinhood chain: [`0x730e…9af3`](https://robinhoodchain.blockscout.com/address/0x730e3c356299c9203cb042f6c0a9274aeabf9af3?tab=contract)
- **ERC-8478 x402 Payee Verification** · [PR #2132](https://github.com/ethereum/ERCs/pull/2132) · is the payTo really the agent you mean to pay, checked against its ERC-8004 identity · first outside implementation already live
- **Agent Pre-Sign Risk Report** (draft) · [PR #2134](https://github.com/ethereum/ERCs/pull/2134) · typed facts about an unsigned request, each read or not read at one block, digest-bound and EIP-712 signed

**use it**

- **x402 facilitator** · <https://x402.t0ll.xyz> · keyless, free, USDG on robinhood chain · checks the payTo against the seller's ERC-8004 identity (ERC-8478) before it settles, signs a receipt for every payment · [x402 Register](https://x402.t0ll.xyz/#register): every agent selling over x402 on robinhood chain, checked
- **guard** · `npm i @tollxyz/guard` · one line in front of a viem or ethers wallet: a BLOCK never reaches the signer, a swapped x402 payTo never reaches the payer
- **MCP server** · [`t0ll-xyz/toll-mcp`](https://github.com/t0ll-xyz/toll-mcp) · remote at `https://t0ll.xyz/api/mcp` · `check_tx`, `presign_risk_report`, `check_coin`, `check_agent` and more
- **plugins** · [`t0ll-xyz/toll-plugins`](https://github.com/t0ll-xyz/toll-plugins) · ElizaOS, AgentKit, Vercel AI SDK, GOAT, LangChain, Mastra · `npm i @tollxyz/mcp`
- **HTTP** · `POST https://t0ll.xyz/api/tx/check` (ALLOW / WARN / BLOCK) · `POST https://t0ll.xyz/api/presign` (the signed report)
- **Toll is ERC-8004 agent #20030** on robinhood chain · paid checks over x402 in USDG or USDC on base · [agent page](https://t0ll.xyz/agents)

[![checked by Toll](https://t0ll.xyz/agents/census/20030/badge.svg)](https://t0ll.xyz/agents/census/20030?utm_source=badge)

[t0ll.xyz](https://t0ll.xyz) · [@Tollxyz_](https://x.com/Tollxyz_)
