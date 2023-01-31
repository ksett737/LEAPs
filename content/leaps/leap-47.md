---
leap: 47
title: Camelot Round Table - LYRA liquidity on Arbitrum
status: Draft
author: <0xmyrddin> (@0xmyrddin) 

created: 2023-01-31
---

## Simple Summary
Camelot is a custom-built protocol aiming to become the native Arbitrum native DEX. It’s currently based on Univ2 for volatile pairs and a Solidly-type curve for stable ones. By building sustainable and adaptable liquidity, Camelot moves away from the high-emission yield farm approach to create a DEX that can genuinely support native builders with bespoke features.
Camelot currently has $20m TVL with $2m daily volume, and we are officially partnered with GMX, Umami, Sperax, Buffer, Lido, Liquity, Vela, Dsquared, Jones, Factor, Lexer, Bond Protocol, JustBet and many more.
By welcoming Lyra to the Round Table, we propose to support Lyra's liquidity on Camelot and, by extension, formally welcome Lyra into the Arbitrum ecosystem alongside our core partners.

## Abstract
With Lyra’s recent deployment to Arbitrum, having token liquidity on the chain is essential in broadening your exposure to new users and expanding your community of token holders to one of the most active L2 ecosystems. Therefore, Camelot aims to build deep and sustainable liquidity for LYRA through a structured and measured approach. 
Camelot proposes that Lyra seeds initial liquidity of $100k worth of LYRA/ETH on Camelot and, in addition, allocates $5k of incentives per month. In return, Camelot is committed to offering an allocation of 0.2% total supply of [$xGRAIL](https://docs.camelot.exchange/tokenomics/grail-token) (worth equiv $60k) and matching the incentives 1:1 in dollar value in LYRA or stkLYRA with xGRAIL.
The $100k protocol-owned liquidity serves the vital role of seeding the pool. With a combined total of $10k incentives per month, we target $400k of community liquidity, assuming an estimated 30% APR. This is a reasonable and achievable first step that would allow us to monitor the pool's performance and remain adaptable to prevent overspending emissions.
Camelot has been thoroughly audit by [Paladin](https://docs.camelot.exchange/references/audits):

## Motivation
Through building custom infrastructure, Camelot is committed to supporting the entire Arbitrum ecosystem to achieve more sustainable and deep liquidity. In addition to providing incentives and token allocations, Camelot emphasizes the bespoke support it can provide to partners.
For example, several features allow us to tailor a strategy specific to each partner. We can adjust the fees of every pool, including bidirectionally, allowing partners to generate real value on their PoL. Most importantly, our Nitro pool tech enables partners to incentivize liquidity in highly structured ways, such as only to LPs that have been locked for a certain time.
Every part of Camelot is designed to incentivize long-term and sustainable behavior that captures value to the protocol. Our goal is to extend this philosophy to our partners too.
The Round Table plays a significant part in our approach, intending to foster collaboration and innovation within the Arbitrum ecosystem. Camelot is deeply connected with the key Arbitrum builders; therefore, by being on the Round Table, Lyra would also have access to this network.

## Specification

- LYRA/ETH pool (pair) w/ the fee settings - it is recommended to use the .3-.5% fee tier initially
- Farming emissions (in GRAIL/xGRAIL) - $5,000 worth of incentives in xGRAIL matched 1:1 in dollar value with stkLYRA or LYRA
- Nitro Pools - Council can consider adding a Nitro pool as an additional layer of incentives, w/ optional custom requirements to be eligible

The fee tier and trading pair to be incentivized can be updated by Council via discord consensus. Council may subsequently decide to split rewards between a regular Lyra pool and a Nitro Pool. 


### Overview
This proposal intends to bring significant value to the Lyra protocol by building deep and sustainable liquidity for $LYRA on Arbitrum. In return for seeding the initial liquidity, we allow the Lyra protocol to have direct exposure to Camelot through a partner token allocation. We aim to achieve a highly effective return on liquidity incentives through a structured and bespoke approach.

### Proposal summary
Camelot is committed to formally welcoming Lyra to the Round Table, supporting $LYRA liquidity as the native DEX on Arbitrum:
- In return for bringing $100k of LYRA/ETH PoL, Camelot is committed to providing Lyra Protocol with a $xGRAIL allocation of 0.2% total supply. (Vested over two years with a six-month cliff. xGRAIL currently earns 20% APR in mostly ETH/USDC and would therefore be a productive asset for the Lyra treasury).
- In return for incentivizing liquidity with $5k per month of LYRA rewards, Camelot is committed to matching this 1:1 in dollar value. This will be done through our custom Nitro pools, allowing Lyra to add additional requirements for these rewards, such as only for LPs that have been locked for a certain duration. 
- Camelot is committed to formally welcoming Lyra to the Round Table alongside our existing partners, such as GMX, Jones, Umami, Lido, Liquity, Vela, and more.
- Camelot is committed to marketing and community support, allowing Lyra to capture new users within the Arbtrium ecosystem. In addition, this includes AMAs, Twitter spaces, and other forms of engagement that benefit both protocols.

Camelot is committed to forming a long-term partnership that will provide Lyra with bespoke support for its liquidity requirements on Arbitrum. 

### Configurable Values
- Lyra Rewards = $5,000 USD worth of stkLYRA per month
- xGRAIL Rewards $5,000 USD worth of xGRAIL per month
- xGRAIL allocation = .2% total supply 
- Protocol Owned Liquidity = $100k 
- Initial Fee Tier = .5% 

## Copyright
Copyright and related rights waived via [CC0](https://creativecommons.org/publicdomain/zero/1.0/).
