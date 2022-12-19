
---
leap: 42
title: Migrate LYRA staking to mainnet
status: Draft
author: dappbeast
created: 2022-12-19
---

## Simple Summary
This LEAP proposes migrating LYRA staking from Optimism to Ethereum mainnet in anticipation of the Lyra Protocol's multi-chain deployment. It also includes modifications to reward programs to support mainnet staking.

## Abstract
With the Arbitrum deployment following [LEAP 38](https://leaps.lyra.finance/leaps/leap-38/), the Lyra DAO needs to manage a multi-chain protocol on Optimism and Arbitrum. This LEAP suggests Ethereum mainnet as a secure and unbias home for staking. This requires:

- Migration of LYRA staking contract from Optimism to Ethereum mainnet.
- Modification of the vault, fee rebate and short collateral programs on L2s to distribute rewards as native LYRA instead of stkLYRA which won't be bridgeable.

## Motivation

For a multi-chain protocol, mainnet is a secure and unbias home for LYRA staking. The move to mainnet unlocks important benefits:

- A fully on-chain staking program (with no off-chain components).
- Unlocking on-chain governance to manage deployments across multiple L2s (in future proposals).
- Improved staking UX.

### On-Chain Staking

Staking rewards are currently calculated via an off-chain script and seeded in a distributor contract on Optimism in 2 week epochs. A move to mainnet staking allows us to run a fully on-chain staking program using Aave's battle-tested [security module contract](https://docs.aave.com/developers/v/2.0/protocol-governance/staking-aave).

### On-Chain Governance

As Lyra DAO migrates its governance processes on-chain, mainnet is a natural home for a multi-chain protocol that requires cross-chain messaging. Ability to send messages in [10-15 minutes]([https://community.optimism.io/docs/developers/bridge/messaging/#for-ethereum-l1-to-optimism-l2-transactions](https://community.optimism.io/docs/developers/bridge/messaging/#for-ethereum-l1-to-optimism-l2-transactions)) from mainnet to an L2 is essential for time-sensitive actions like parameter updates and reward distributions. For optimistic rollups like Optimism and Arbitrum, a 7 day challenge period to send messages between L2s is unacceptable for these processes.

Governance involving token holders therefore requires LYRA and stkLYRA token liquidity on mainnet.

### Staking UX

Most users are choosing a specific L2 for their DeFi activity. A [dune query](https://dune.com/queries/1765281?tx_count_n26d66=10 "https://dune.com/queries/1765281?tx_count_n26d66=10") shows that of 276k active Arbitrum users, 155k are also active on mainnet compared to only 85k also active on Optimism. We can attribute this to a few reasons:
- Popular protocols like Uniswap and Aave are available on many L2s, meaning users don't need to bridge to a specific L2 to use them.
- Difficult UX to bridge and manage assets across L2s.
- Different security and decentralization tradeoffs on different L2s.
- Alignment with L2 communities and their native projects.

Mainnet staking gives stakers the security of Ethereum mainnet and makes the Lyra DAO neutral to all L2s and their communities. Additionally, the staking contract (which is a fork of [Aave's security module](https://docs.aave.com/developers/v/2.0/protocol-governance/staking-aave)) is optimized for mainnet, ensuring a reasonable level of accessibility to L2-native users in the short to medium term. 

## Specification

### Overview
<!--This is a high level overview of *how* the LEAP will solve the problem. The overview should clearly describe how the new feature will be implemented.-->

Migration of LYRA staking will happen at the start of a new epoch to ensure smooth migration. This process involves:

1. Deployment of staking contract on mainnet.
2. Pausing rewards on Optimism staking contract.
3. Enabling instant unstaking on Optimism by setting `UNSTAKE_WINDOW` to 0.
4. Migrating all L2 reward programs (vault LPs, fee rebates and short collateral) to be rewarded in native LYRA instead of staked LYRA.

There will also simplifications to the staking program:

- Removal of the 6 month lock on staking rewards.
- Immediate distribution of previously locked staking rewards.

Beyond this, staking features defined in [LEAP 26](https://leaps.lyra.finance/leaps/leap-26) including the 14 day cooldown period on staking rewards remain unchanged.

### Rationale
<!--This is where you explain the reasoning behind how you propose to solve the problem. Why did you propose to implement the change in this way, what were the considerations and trade-offs. The rationale fleshes out what motivated the design and why particular design decisions were made. It should describe alternate designs that were considered and related work. The rationale may also provide evidence of consensus within the community, and should discuss important objections or concerns raised during discussion.-->

There are a few key decisions to justify:
- Immediate vs phased migration: Allowing staking on Optimism and mainnet for a grace period (e.g. 1 epoch) introduces significant complexity to staking UX for little benefit. Stakers face the same bridging constraints regardless of migration window (7 day challenge period, limited fast bridge liquidity). We should aim to minimize migration work where we can.
- Rewarding native LYRA on L2s: Staked LYRA will not be bridgeable from Optimism to mainnet, meaning any program rewarding stkLYRA tokens on an L2 (vault LPs, fee rebates or short collateral) must now be rewarded in native LYRA which can then be bridged to mainnet and staked. The overhead required to make stkLYRA bridgeable (deploy staking contracts and provide fast bridge liquidity on all L2s) to impose the 14 day unstake window on rewards isn't a worthwhile tradeoff.
- Removal of 6 month lock on staking rewards: Maintaining this lock would require new contract work and an audit, increasing cost and delaying migration timelines.

### Technical Specification
<!--The technical specification should outline the public API of the changes proposed. That is, changes to any of the interfaces Lyra currently exposes or the creations of new ones.-->

There are no new contracts introduced in this LEAP. Documentation on the staking contract can be found [here](https://docs.aave.com/developers/v/2.0/protocol-governance/staking-aave).

## Copyright
Copyright and related rights waived via [CC0](https://creativecommons.org/publicdomain/zero/1.0/).
