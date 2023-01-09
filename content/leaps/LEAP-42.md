---
leap: 42
title: Migrate LYRA staking to mainnet
status: Proposed
author: dappbeast
created: 2022-12-19
---

## Simple Summary
This LEAP proposes migrating LYRA staking from Optimism to Ethereum mainnet in anticipation of the Lyra Protocol's multi-chain deployment. It also includes modifications to reward programs to support mainnet staking.

## Abstract
With the Arbitrum deployment following [LEAP 38](https://leaps.lyra.finance/leaps/leap-38/), the Lyra DAO needs to manage a multi-chain protocol on Optimism and Arbitrum. This LEAP proposes Ethereum mainnet as a secure and unbiased home for staking.

The major changes from this migration are:
- Staking rewards are only earned for mainnet stkLYRA balances. Traders and LPs will continue to earn stkLYRA on L2s directly, but must bridge to mainnet (and wait [7 days](https://help.optimism.io/hc/en-us/articles/4411895558171-Why-do-I-need-to-wait-a-week-when-moving-assets-out-of-Optimism-)) to earn staking rewards on their stkLYRA balance.
- stkLYRA can only be unstaked on mainnet. This means stkLYRA holders must bridge their stkLYRA to mainnet to unstake it to LYRA.
- Staking rewards will only be rewarded in stkLYRA, and there is no 6 month lock on claims.
- Locked staking rewards from previous epochs will be immediately unlocked at the start of the migration epoch. As of writing, this is approximately 5m stkLYRA earned over 6 months.

## Motivation

For a multi-chain protocol, mainnet is a secure and unbiased home for LYRA staking. The move to mainnet unlocks important benefits:

- A fully on-chain staking program (with no off-chain components).
- Unlocking on-chain governance to manage deployments across multiple L2s (in future proposals).
- Improved staking UX.

### On-Chain Staking

Staking rewards are currently calculated via an off-chain script and seeded in a distributor contract on Optimism in 2 week epochs. A move to mainnet staking allows us to run a fully on-chain staking program using Aave's battle-tested [security module contract](https://docs.aave.com/developers/v/2.0/protocol-governance/staking-aave).

### On-Chain Governance

As Lyra DAO migrates its governance processes on-chain, mainnet is a natural home for a multi-chain protocol that requires cross-chain messaging. Ability to send messages in [10-15 minutes](https://community.optimism.io/docs/developers/bridge/messaging/#for-ethereum-l1-to-optimism-l2-transactions) from mainnet to an L2 is essential for time-sensitive actions like parameter updates and reward distributions. For optimistic rollups like Optimism and Arbitrum, a 7 day challenge period to send messages between L2s is unacceptable for these processes.

Governance involving token holders therefore requires LYRA and stkLYRA token liquidity on mainnet.

### Staking UX

Most users are choosing a specific L2 for their DeFi activity. A [dune query](https://dune.com/queries/1765281?tx_count_n26d66=10 "https://dune.com/queries/1765281?tx_count_n26d66=10") shows that of 276k active Arbitrum users, 155k are also active on mainnet compared to only 85k also active on Optimism. We can attribute this to a few reasons:
- Popular protocols like Uniswap and Aave are available on many L2s, meaning users don't need to bridge to a specific L2 to use them.
- Difficult UX to bridge and manage assets across L2s.
- Different security and decentralization tradeoffs on different L2s.
- Alignment with L2 communities and their native projects.

Mainnet staking gives stakers the security of Ethereum mainnet and makes the Lyra DAO neutral to all L2s and their communities. The staking contract (which is a fork of [Aave's security module](https://docs.aave.com/developers/v/2.0/protocol-governance/staking-aave)) is optimized for mainnet, ensuring a reasonable level of accessibility in the short to medium term. Additionally, stkLYRA will be bridgeable from L2s to mainnet, meaning L2-native users won't need to transact on mainnet to earn staking rewards, they will only need to bridge their stkLYRA to mainnet (they will need to transact to unstake).

## Specification

### Overview
<!--This is a high level overview of *how* the LEAP will solve the problem. The overview should clearly describe how the new feature will be implemented.-->

Migration will require users to swap current "OP stkLYRA" to new "mainnet stkLYRA" on Optimism. Mainnet stkLYRA will be deployed on mainnet but bridgeable from Optimism, allowing users to bridge from Optimism and stake on mainnet.

Migration will happen at the start of a new epoch referred to as the "migration epoch" to ensure a smooth transition. The steps taken are:

1. New staking and migration contracts deployed.
2. Initialization of stkLYRA bridges between mainnet and Optimism / Arbitrum.
3. Rewards distributed for previous epoch (in OP stkLYRA).
4. Locked staking rewards distributed for all previous epochs (in OP stkLYRA).
5. Reward distribution starts for mainnet staking.

Changes to staking UX are as follows:

- Staking rewards are only earned for mainnet stkLYRA balances. Traders and LPs continue to earn and claim stkLYRA rewards on L2s, but must bridge stkLYRA to mainnet to earn staking rewards. Staking rewards are calculated on-chain using balances of stkLYRA, and with the staking contract on mainnet, it can only read mainnet balances. Bridging stkLYRA from L2s to mainnet will take 7 days on Optimistic rollups due to the [challenge period](https://help.optimism.io/hc/en-us/articles/4411895558171-Why-do-I-need-to-wait-a-week-when-moving-assets-out-of-Optimism-).
- Staking rewards on mainnet will only be rewarded in stkLYRA, and there is no 6 month lock on claiming stkLYRA rewards. These are functional limitations of the staking contract.
- stkLYRA can only be unstaked on mainnet. Because the staking contract will live on mainnet and not Optimism, users must bridge any stkLYRA earned on L2s to unstake and claim their LYRA. During the migration, users can abstain from migrating their stkLYRA and unstake on an L2 directly (but they will no longer accrue rewards for that LYRA).
- Stakers must swap their OP stkLYRA to mainnet stkLYRA to earn staking and trading / LP rewards on mainnet and L2s. Migration requires an `approve()` and `migrate()` transaction. Trading / LP rewards will only be earned for mainnet stkLYRA balances in the migration epoch. 
- All of these changes will be enforced immediately at the start of the migration epoch.

Beyond this, staking features defined in [LEAP 26](https://leaps.lyra.finance/leaps/leap-26) including the 14 day cooldown period on staking rewards remain unchanged.

### Rationale
<!--This is where you explain the reasoning behind how you propose to solve the problem. Why did you propose to implement the change in this way, what were the considerations and trade-offs. The rationale fleshes out what motivated the design and why particular design decisions were made. It should describe alternate designs that were considered and related work. The rationale may also provide evidence of consensus within the community, and should discuss important objections or concerns raised during discussion.-->

There are a few key decisions to justify:

- Immediate migration: A phased migration where stakers can earn staking rewards on Optimism and mainnet for a grace period (e.g. 1 epoch) introduces complexity to reward scripts and staking UX for little user benefit. All stakers face the same 7 day challenge period regardless of immediate or phased migration. We should aim to simplify migration work where we can.
- Removal of 6 month lock: Maintaining this lock would require adding features to the staking contract and a subsequent audit, increasing cost and delaying migration timelines.
- Immediate unlock of staking rewards: An immediate unlock will distribute appriximately 5m stkLYRA earned over the last 6 months. Abiding by the 6 month lock would require fortnightly distribution of stkLYRA to Optimism over the next 6 months. This would increase overhead via continued use and maintenance of off-chain scripts to calculate and distribute staking rewards, and add a 6 month wind down period to the migration.

### Technical Specification
<!--The technical specification should outline the public API of the changes proposed. That is, changes to any of the interfaces Lyra currently exposes or the creations of new ones.-->

A new fork of Aave's staking contract will be deployed. Documentation on the staking contract can be found [here](https://docs.aave.com/developers/v/2.0/protocol-governance/staking-aave).

Additionally, a simple migration contract to swap OP stkLYRA for mainnet stkLYRA 1:1 will be deployed.

## Copyright
Copyright and related rights waived via [CC0](https://creativecommons.org/publicdomain/zero/1.0/).
