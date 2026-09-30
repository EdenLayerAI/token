# EDEN Token — Tokenomics

> **EDEN 1.0.0** is a Solana Token-2022 asset designed around governed supply, transparent allocation, fee-aware settlement, and a primary **SOL → EDEN** market model.

────────

Overview

|Property                 |Value                                         |
|-------------------------|----------------------------------------------|
|**Name**                 |EDEN                                          |
|**Symbol**               |EDEN                                          |
|**Version**              |1.0.0                                         |
|**Network**              |Solana                                        |
|**Cluster**              |mainnet-beta                                  |
|**Standard**             |Token-2022                                    |
|**Decimals**             |9                                             |
|**Canonical Address**    |`EDENVVPjLTS62hirwreuM53LjFwq52bHp5hNQBm9FE5J`|
|**Primary Acquisition**  |SOL → EDEN                                    |
|**Primary On-Chain Pair**|WSOL / EDEN                                   |
|**Display Market**       |SOL / EDEN                                    |

> **Deployment status**
> 
> The address above is the canonical EDEN production address. Public documentation must not represent it as a live mainnet mint until Solana mainnet-beta verification confirms that the account exists and matches the EDEN Token-2022 specification.

────────

Supply

Maximum Outstanding Supply

18,446,000,000 EDEN

At 9 decimals:

18,446,000,000,000,000,000 base units

EDEN uses a maximum outstanding-supply policy. Outstanding supply must never exceed the policy ceiling.

Mint authority is intended to remain governed rather than permanently revoked. Routine post-genesis issuance is disabled by policy. If tokens are permanently burned, replacement issuance may only occur through the governed mint process and must still satisfy the maximum outstanding-supply constraint.

This is a policy-controlled maximum outstanding supply. It is not a claim that the mint has already been initialized, that the full supply has already been minted, or that the full allocation is circulating.

────────

Genesis Allocation

|Category                 |Share   |Allocation             |
|-------------------------|-------:|----------------------:|
|Community                |30%     |5,533,800,000 EDEN     |
|Ecosystem                |20%     |3,689,200,000 EDEN     |
|Team                     |15%     |2,766,900,000 EDEN     |
|Liquidity & Market Making|15%     |2,766,900,000 EDEN     |
|Treasury                 |10%     |1,844,600,000 EDEN     |
|Reserve                  |5%      |922,300,000 EDEN       |
|Developers & Builders    |5%      |922,300,000 EDEN       |
|**Total**                |**100%**|**18,446,000,000 EDEN**|

Unallocated genesis supply: 0 EDEN

Allocation must not be interpreted as circulation. Locked, vested, treasury-controlled, liquidity, market-making, reserved, and distributed balances must be reported independently when public circulation data becomes available.

────────

Token-2022 Profile

Required Extensions

EDEN’s production specification requires:

• MetadataPointer
• TokenMetadata
• TransferFeeConfig

Intentionally Absent

The production profile is designed without:

• Freeze Authority
• Mint Close Authority
• Permanent Delegate
• Non-Transferable
• Default Account State restrictions
• Confidential Transfer
• Transfer Hook
• Token-2022 Pausable

Actual extension and authority state must be verified directly from Solana mainnet-beta before being represented as deployed.

────────

Transfer Fee Policy

|Parameter                |Policy                 |
|-------------------------|----------------------:|
|Launch transfer fee      |2% / 200 bps           |
|Governance policy ceiling|5% / 500 bps           |
|Token-2022 maximum fee   |368,920,000 EDEN       |
|Maximum fee base units   |368,920,000,000,000,000|

The 5% / 500 bps value is an EDEN governance policy ceiling.

It is distinct from Token-2022’s maximum_fee, which is an absolute token amount applied to a transfer-fee configuration rather than a percentage ceiling.

Public fee reporting should distinguish:

• active transfer-fee basis points;
• pending fee configuration;
• maximum fee amount;
• withheld balances;
• harvested fees;
• withdrawn fees;
• treasury receipts;
• applicable authority addresses.

────────

Market Model

Primary Acquisition

SOL → EDEN

Primary Liquidity Pair

WSOL / EDEN

Public interfaces should display the market as:

SOL / EDEN

The planned primary venue is Raydium CPMM, with Jupiter Swap API V2 used as the primary router when a valid route is available.

Secondary Liquidity

Secondary market support may include:

EDEN / USDC

A configured market is not equivalent to a live market. Public trading status must be based on verified:

• pool existence;
• active liquidity;
• successful SOL → EDEN execution;
• successful EDEN → SOL execution;
• current Jupiter routing;
• acceptable slippage and price impact;
• settlement reconciliation.

────────

Liquidity Allocation

The Liquidity & Market Making allocation is:

2,766,900,000 EDEN — 15% of total allocation

This allocation may be distributed across:

• initial WSOL / EDEN liquidity;
• liquidity reserves;
• market-making inventory;
• secondary EDEN / USDC liquidity.

Every deployed, reserved, or market-making balance must reconcile back to the same 15% allocation.

────────

Authorities

EDEN separates authority responsibilities by function.

|Authority                 |Intended Policy|
|--------------------------|---------------|
|Mint Authority            |Governed       |
|Freeze Authority          |None           |
|Mint Close Authority      |None           |
|Transfer Fee Configuration|Governed       |
|Withheld Fee Withdrawal   |Treasury       |
|Metadata Update           |Governed       |

Public authority addresses should only be published after the deployed mint has been independently verified on mainnet-beta.

────────

Circulating Supply

Public circulating supply must be derived from actual on-chain balances together with documented lock, vesting, treasury, liquidity, market-making, reserve, and custody state.

These values are not interchangeable:

allocated ≠ minted ≠ unlocked ≠ circulating ≠ liquid

Until mainnet genesis and allocation reconciliation are complete, the maximum supply and allocation table represent protocol policy values, not a circulating-supply claim.

────────

Metadata

Canonical Metadata Source

https://raw.githubusercontent.com/EdenLayerAI/token/2e7c61bccd087229aa631a24296275fd87176d66/metadata/metadata.json

Public Links

• Website: https://edenlayer.ai
• Documentation: https://docs.edenlayer.ai
• Token image: public/assets/eden.png

For a final immutable release, metadata/metadata.json and public/assets/eden.png should be committed together and pinned to the same immutable Git commit.

────────

Verification

Once deployed, EDEN public verification should confirm:

Cluster                 mainnet-beta
Program                 Token-2022
Mint                    EDENVVPjLTS62hirwreuM53LjFwq52bHp5hNQBm9FE5J
Decimals                9
Outstanding Supply      ≤ 18,446,000,000 EDEN
Metadata                EDEN / EDEN / canonical URI
Required Extensions     Present
Forbidden Extensions    Absent
Freeze Authority        None
Mint Close Authority    None
Transfer Fee            Expected policy state
Mint Authority          Governed

The Solana blockchain is authoritative for deployed:

• supply;
• extensions;
• authorities;
• fee configuration;
• token accounts;
• balances;
• transaction history;
• settlement state.

────────

Public Disclosure

EDEN tokenomics describe the protocol’s technical and economic design.

They do not, by themselves, establish that a mint, pool, market, allocation, vesting schedule, liquidity position, authority transition, or circulating-supply value is live.

Mainnet deployment, market availability, liquidity, routing, circulating supply, and authority state should only be represented as active after independent verification.

────────

Version

EDEN Token 1.0.0
