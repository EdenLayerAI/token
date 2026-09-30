# EDEN Token — Public Tokenomics

**Version:** 1.0.0
**Network:** Solana
**Standard:** Token\-2022
**Decimals:** 9
**Canonical production mint address:** `EDENTZYUTprUgAHdNxrBLMHQDnM5Aw7Pt5XSpLkFhfYx`

**Fee account:** `fee4nF8g16g44NRF6ADqR5Cf9Yj942Ke2s2fbnHcU9p`

**Authority:** `FRYSb7iu48Jt7RAqzzMzu9nLiPKkFKtUabZQLsmoZiyR`

> **Deployment status:** the address above is the canonical EDEN production
> address, but public documentation must not treat it as a live mainnet mint
> until Solana mainnet-beta verification confirms that the account exists and
> matches the EDEN Token-2022 specification.

## Supply

EDEN uses a **maximum outstanding\-supply policy** of:

**18,446,000,000 EDEN**

Equivalent base units at 9 decimals:

`18,446,000,000,000,000,000`

The policy is designed so outstanding supply must never exceed the maximum\.
Mint authority is intended to remain governed rather than permanently revoked\.
Routine post\-genesis issuance is disabled by policy\. If tokens are permanently
burned, replacement issuance may only occur through the governed mint process
and must still satisfy the outstanding\-supply ceiling\.

This is a policy\-controlled maximum outstanding supply, not a claim that the
mint has already been initialized or that the full supply is circulating\.

## Genesis allocation

|Category                 |Share   |EDEN              |
|-------------------------|-------:|-----------------:|
|Community                |30%     |5,533,800,000     |
|Ecosystem                |20%     |3,689,200,000     |
|Team                     |15%     |2,766,900,000     |
|Liquidity & Market Making|15%     |2,766,900,000     |
|Treasury                 |10%     |1,844,600,000     |
|Reserve                  |5%      |922,300,000       |
|Developers & Builders    |5%      |922,300,000       |
|**Total**                |**100%**|**18,446,000,000**|

There is **no unallocated genesis bucket**\.

Allocation does not mean circulation\. Locked, vested, treasury\-controlled,
liquidity, market\-making, and distributed balances must be reported separately
when public circulation data becomes available\.

## Token\-2022 configuration

The EDEN production specification requires:

- `MetadataPointer`
- `TokenMetadata`
- `TransferFeeConfig`

The production profile is intentionally minimal\. The following capabilities are
not part of the EDEN Token\-2022 design:

- Freeze Authority
- Mint Close Authority
- Permanent Delegate
- Non\-Transferable
- Default Account State restrictions
- Confidential Transfer
- Transfer Hook
- Token\-2022 Pausable

Actual extension and authority state must be verified from Solana mainnet\-beta
before being represented as deployed\.

## Transfer fee policy

The planned launch transfer\-fee configuration is:

|Parameter                |Policy                 |
|-------------------------|----------------------:|
|Launch transfer fee      |2% / 200 bps           |
|Governance policy ceiling|5% / 500 bps           |
|Token-2022 maximum fee   |368,920,000 EDEN       |
|Maximum fee base units   |368,920,000,000,000,000|

The **5% value is an EDEN governance policy ceiling**\. It is distinct from the
Token\-2022 `maximum_fee` field, which is an absolute token amount per transfer\.

Transfer\-fee state, current epoch configuration, pending fee changes, withheld
fees, and withdrawal authority should be verified from chain data\.

## Primary market model

The canonical user\-facing acquisition path is:

`SOL → EDEN`

The primary on\-chain liquidity pair is designed as:

`WSOL / EDEN`

with the public market displayed as:

`SOL / EDEN`

The initial venue is planned as **Raydium CPMM**, with **Jupiter Swap API V2**
used as the primary router when a valid route is available\.

Secondary liquidity may include `EDEN / USDC`\.

A configured market is not the same as a live market\. Public trading status must
be based on verified pool existence, active liquidity, successful buy/sell
execution, and current Jupiter routing\.

## Liquidity allocation

The Liquidity & Market Making allocation is:

**2,766,900,000 EDEN — 15% of total allocation**

This allocation may be divided among:

- initial WSOL/EDEN liquidity;
- liquidity reserves;
- market\-making inventory;
- secondary EDEN/USDC liquidity\.

Every deployed or reserved amount must reconcile to the same 15% allocation\.

## Metadata

Public Token\-2022 metadata source:

\`\`metadata/metadata\.json` — pin to immutable release commit`

Website:

`https://edenlayer.ai`

Documentation:

`https://docs.edenlayer.ai`

The public token image is stored at:

`public/assets/eden.png`

For a final immutable release, `metadata/metadata.json` and
`public/assets/eden.png` should be committed together and pinned to the same
release commit\.

## Authorities

EDEN’s production authority model separates responsibilities:

|Authority                 |Intended policy|
|--------------------------|---------------|
|Mint Authority            |Governed       |
|Freeze Authority          |None           |
|Mint Close Authority      |None           |
|Transfer Fee Configuration|Governed       |
|Withheld Fee Withdrawal   |Treasury       |
|Metadata Update           |Governed       |

Public authority addresses should only be published after the deployed mint has
been verified on mainnet\-beta\.

## Circulating supply

Public circulating supply must be derived from actual on\-chain balances and
documented lock, vesting, treasury, liquidity, and custody state\.

The following values must not be treated as equivalent:

`allocated ≠ minted ≠ unlocked ≠ circulating ≠ liquid`

Until mainnet genesis and allocation reconciliation are complete, the maximum
supply and allocation table are policy values rather than a circulating\-supply
claim\.

## Verification

Once deployed, public verification should confirm:

```text
cluster                  mainnet-beta
program                  Token-2022
mint                     EDENTZYUTprUgAHdNxrBLMHQDnM5Aw7Pt5XSpLkFhfYx
decimals                 9
supply                   ≤ 18,446,000,000 EDEN
metadata                 EDEN / EDEN / canonical URI
required extensions      present
forbidden extensions     absent
freeze authority         none
mint close authority     none
transfer fee             expected policy state
mint authority           governed
```

The Solana chain is authoritative for deployed supply, authorities, extensions,
fees, token accounts, balances, and transaction history\.

## Public disclosure

EDEN tokenomics describe the protocol’s technical and economic design\. They do
not by themselves establish that a mint, pool, market, allocation, vesting
schedule, or circulation value is live\.

Mainnet deployment, market availability, liquidity, routing, circulating supply,
and authority state should be published only after independent verification\.
