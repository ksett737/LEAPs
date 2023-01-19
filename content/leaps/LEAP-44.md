---
leap: 44
title: Incentives for LYRA-ETH Mainnet Liquidity
status: Proposed
author: dappbeast (@dappbeast)
created: 2022-03-08
---
## Simple Summary
This LEAP proposes 5m LYRA in annual incentives for LYRA-ETH Uni v3 liquidity on Ethereum mainnet via [Arrakis](https://www.arrakis.finance/). It also proposes removing LYRA-ETH incentives for the same program on Optimism.

## Motivation
Following LEAP 42 and the migration of LYRA staking to mainnet, we need a liquid venue for users to acquire LYRA on mainnet to participate in governance. This is particularly important for migrating more DAO functions to on-chain governance (such as token voting) that will only be feasible on mainnet due to [cross-chain messaging constraints](https://leaps.lyra.finance/leaps/leap-42/#on-chain-governance).

Additionally, with majority of LYRA moving from Optimism to Ethereum mainnet, there is not presently a use case for holding native LYRA on Optimism or any L2. The DAO should save its OP tokens for programs with protocol utility.

## Specification

### Overview
- A LYRA-ETH Uni v3 pool will be incentivised with an annual rate of 5m LYRA.
- A liquidity range of (0.2x, 5x) spot will be used as a starting point.
- The Arrakis Protocol, which offers easy management of Uni v3 liquidity, will be used similar to the previous program proposed in [LEAP 21](https://leaps.lyra.finance/leaps/leap-21).
- To ensure smooth migration of token liquidity, when LYRA-ETH incentives on Ethereum mainnet start, LPs will be given 2 weeks to migrate before incentives on Optimism are disabled.

### Rationale
- At time of writing, 5m LYRA should attract ~$1.2m TVL for 50% APY, a reasonable depth to bootstrap token liquidity.
- A Uniswap v3 range of (0.2x, 5x) current spot offers a ~180% improvement in capital efficiency relative to Uniswap v2 (https://uniswap.org/blog/uniswap-v3).
- A 2 week migration window gives LPs 2x the 7 day challenge period to bridge their LYRA from Optimism to Ethereum mainnet.

### Test Cases
N/A

### Configurable Values
Proposed range for liquidity: \\((0.2spot, 5spot)\\ where _spot_ is the LYRA price on program launch.

