# SONIC Tokenomics

Version: 1.0.0
Status: Pre-deployment
Network: Solana
Token Standard: Token-2022

> SONIC is the native Token-2022 asset of SONIC NETWORK, designed for creator rewards, ecosystem participation, tokenized content, platform utility, and on-chain creator commerce.

## Token specification

|Property                              |Value                   |
|--------------------------------------|------------------------|
|Token                                 |SONIC                   |
|Network                               |Solana                  |
|Standard                              |Token-2022              |
|Initial maximum supply                |**18,446,000,000 SONIC**|
|Decimals                              |TBA                     |
|Production mint address               |**TBA**                 |
|Token-2022 transfer fee               |**3% / 300 bps**        |
|Maximum transfer fee                  |TBA                     |
|Quarterly burn                        |**2%**                  |
|Burn calculation base                 |**TBA**                 |
|Locked supply                         |**3,000,000,000 SONIC** |
|Locked share of initial maximum supply|**16.26%**              |
|Lock infrastructure                   |**Streamflow Finance**  |
|Streamflow contract / stream ID       |**TBA**                 |

## Supply accounting

SONIC treats these states separately:

Initial Maximum Supply → Allocated Supply → Locked / Unlocked Supply → Circulating Supply

A token being allocated does not make it unlocked or circulating.

Distribution

|Allocation            |Share   |SONIC             |Release model   |
|----------------------|-------:|-----------------:|----------------|
|Ecosystem & Community |20%     |3,689,200,000     |Programmatic    |
|Protocol Treasury     |20%     |3,689,200,000     |Controlled      |
|Core Contributors     |15%     |2,766,900,000     |Vesting         |
|Creator Rewards       |10%     |1,844,600,000     |Reward programs |
|Liquidity & Markets   |10%     |1,844,600,000     |Liquidity policy|
|Strategic Partners    |10%     |1,844,600,000     |Vesting         |
|Community Distribution|10%     |1,844,600,000     |Programmatic    |
|Foundation & Grants   |5%      |922,300,000       |Milestone-based |
|**Total**             |**100%**|**18,446,000,000**|                |

> **3,000,000,000 SONIC (16.26% of initial maximum supply)** is designated for Streamflow-based locking. This is a supply state, not an additional allocation. Source allocation(s), lock type, dates and verified on-chain identifier remain TBA.

## Token-2022 transfer fee

Applicable SONIC transfers use a 3% / 300 bps Token-2022 transfer fee.

This must be reported separately from:

• Solana network fees
• priority fees
• marketplace service fees
• SONIC Swap service fees
• DEX, routing and provider fees

Production deployment must publish:

• maximum transfer fee
• transfer-fee configuration authority
• withdraw-withheld authority
• verified mint address

## Quarterly burn

SONIC has a 2% quarterly burn policy.

The 2% calculation base remains TBA and must be finalized before activation. Do not describe the burn as 2% of total, circulating, treasury, or fee inventory until the policy explicitly selects one.

Lifecycle:

SCHEDULED → CALCULATED → AUTHORIZED → SUBMITTED → CONFIRMED → BURNED → RECONCILED

Every burn should publish the burn amount, calculation base, supply before/after, transaction signature, authority and confirmation timestamp.

## Locked supply

3,000,000,000 SONIC is designated for lock/vesting infrastructure through Streamflow Finance.

Required production disclosure:

• source allocation(s)
• lock vs vesting type
• beneficiary
• start date
• cliff / unlock date
• release schedule
• Streamflow contract / stream ID
• creation transaction

Creator Rewards

10% = 1,844,600,000 SONIC

Lifecycle:

ESTIMATED → ELIGIBLE → ALLOCATED → CLAIMABLE → SUBMITTED → CONFIRMED → SETTLED → RECONCILED

Leaderboard position, engagement, token ownership, or community participation alone does not create an entitlement. Eligibility and a funded allocation are required.

## Fee separation

|Fee domain                   |Policy                 |
|-----------------------------|----------------------:|
|Token-2022 transfer fee      |**3% / 300 bps**       |
|Marketplace service fee      |**3% where applicable**|
|SONIC Swap service fee       |**2% / 200 bps**       |
|Solana network fee           |Variable               |
|Priority fee                 |Variable               |
|DEX / routing / provider fees|Provider-defined       |

The checkout and transaction UI should quote each fee separately before wallet signature.

## Authority matrix

|Authority                    |Production value|
|-----------------------------|----------------|
|Mint authority               |TBA             |
|Freeze authority             |TBA             |
|Transfer-fee config authority|TBA             |
|Withdraw-withheld authority  |TBA             |
|Burn execution authority     |TBA             |
|Metadata update authority    |TBA             |

If SONIC is presented as fixed-supply after genesis, the production documentation should state whether the mint authority is revoked after the intended supply is minted.

## Production status

SONIC is currently documented as pre-deployment. The mint address, Streamflow identifier, Token-2022 authorities, maximum transfer fee, decimals, quarterly burn calculation base, lock schedule and related transaction references must be published only after deployment and verification.
