---
leap: 39
title: LEAP Generalized Rebate Whitelist
status: Approved
author: Taminater (@taminater), Muir (@paulvaden), Domrom (@0xdomrom) 
created: 2022-11-23
---

## Simple Summary
Define a process for adding integrators to a rebate whitelist

## Abstract
This proposal is for creating a temporary whitelisting policy for integrator rebates that allows the council to quickly add/remove whitelisted integrators via Discord.

## Motivation
Providing a fee rebate to integrators benefits Lyra via increased volume and usage of Lyra.  Currently it is not possible for integrators to stake Lyra to earn rebates for their vaults, and the process to add whitelisted integrators via LEAPs is cumbersome.

## Rationale
Lyra does not currently offer delegation of boosting from staked Lyra which puts integrators at a disadvantage. Integrators will hold an amount of stkLYRA that would otherwise earn traders a rebate. Lyra should support integrators and partnership by ensuring they receive an appropriate rebate while evaluating delegation models in future tokenomics.

## Specification
The Lyra council will approve rebate requests for integrators on a case by case basis via Discord.  The integrator list will be maintained manually and the rewards script will be adjusted to provide rebates for the whitelisted integrators, based on their staked amount. The program will last until it is terminated by the Lyra Council.

The whitelisting proposals will include
- Amount staked
- Rebate tier
- Designated vaults (Max per table specified below)
- Claimant address
- Rebate duration

The maximum amount of vaults that can be delegated to are based on the amount of lyra staked. Addresses provided by the integrator will be delegated to in the order of addresses provided. (e.g. if 3 addresses are provided [a,b,c] and only 250k lyra is staked, only [a,b] will receive the boost).

The vote to approve whitelisted integrators will occur on Discord via an emoji snap vote, requiring a simple majority to pass. There are no time constraints for the snap vote.

At any time the Lyra Council reserves the right to revoke whitelist spots, or to cancel the entire program. The Lyra Council also reserves the right to deny any integrator payouts if it is shown that this program was abused.

## Configurable Values
Rewards Period = Variable as set by Lyra Council
Rebate table:

| lyra staked  | reward | max accounts |
|--------------|--------|--------------|
| 0            | 5%     | 1            |
| 1k           | 20%    | 1            |
| 5k           | 30%    | 1            |
| 10k          | 35%    | 1            |
| 20k          | 40%    | 1            |
| 50k          | 45%    | 1            |
| 100k         | 47.5%  | 1            |
| 250k         | 50%    | 2            |
| 500k         | 52.5%  | 3            |
| 1M           | 55%    | 6            |
| 2M           | 57.5%  | 11           |
| 3M           | 60%    | 20           |

