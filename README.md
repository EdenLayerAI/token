EDEN Token

> **EDEN 1.0.0** — Solana Token-2022 infrastructure for governed supply, transparent tokenomics, fee-aware settlement, and a primary **SOL → EDEN** market model.

<p align="center">
  <img src="./public/assets/eden.png" alt="EDEN Token" width="180" />
</p>

<p align="center">
  <strong>Solana · Token-2022 · SOL/EDEN · Raydium · Jupiter</strong>
</p>

────────

Overview

|Property                      |Value                                         |
|------------------------------|----------------------------------------------|
|**Name**                      |EDEN                                          |
|**Symbol**                    |EDEN                                          |
|**Version**                   |1.0.0                                         |
|**Network**                   |Solana                                        |
|**Cluster**                   |mainnet-beta                                  |
|**Standard**                  |Token-2022                                    |
|**Decimals**                  |9                                             |
|**Canonical Address**         |`EDENTZYUTprUgAHdNxrBLMHQDnM5Aw7Pt5XSpLkFhfYx`|
|**Fee Account**               |`fee4nF8g16g44NRF6ADqR5Cf9Yj942Ke2s2fbnHcU9p` |
|**Authority**                 |`FRYSb7iu48Jt7RAqzzMzu9nLiPKkFKtUabZQLsmoZiyR`|
|**Maximum Outstanding Supply**|18,446,000,000 EDEN                           |
|**Primary Acquisition**       |SOL → EDEN                                    |
|**Primary On-Chain Pair**     |WSOL / EDEN                                   |
|**Display Market**            |SOL / EDEN                                    |

> [!IMPORTANT]
> The address above is the canonical EDEN production address. Repository configuration must not represent it as a live mainnet mint until Solana mainnet-beta verification confirms that the account exists and matches the EDEN Token-2022 specification.

────────

Canonical Token Identity

EDEN Token
Mint / Token Address    EDENTZYUTprUgAHdNxrBLMHQDnM5Aw7Pt5XSpLkFhfYx
Fee Account             fee4nF8g16g44NRF6ADqR5Cf9Yj942Ke2s2fbnHcU9p
Authority               FRYSb7iu48Jt7RAqzzMzu9nLiPKkFKtUabZQLsmoZiyR
Token Program           TokenzQdBNbLqP5VEhdkAS6EPFLC1PHnBqCXEpPxuEb

> [!NOTE]
> `Authority` is intentionally labeled generically until its exact on-chain
> Token-2022 role is verified. Likewise, the fee account address is published
> as the configured EDEN fee account without assuming an ATA, treasury, or
> withheld-fee ownership role that has not yet been verified.

────────

Tokenomics

Maximum Outstanding Supply

18,446,000,000 EDEN

At 9 decimals:

18,446,000,000,000,000,000 base units

EDEN uses a maximum outstanding-supply policy. Outstanding supply must never exceed the policy ceiling.

Mint authority is intended to remain governed rather than permanently revoked. Routine post-genesis issuance is disabled by policy. Burn replacement, when permitted by governance, must still keep outstanding supply at or below the maximum.

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

> [!NOTE]
> Allocation does not equal circulation. Locked, vested, treasury-controlled, liquidity, market-making, reserve, and distributed balances must be reported independently.

Full public tokenomics: tokenomics/public/README.md

────────

Token-2022 Profile

Required Extensions

• MetadataPointer
• TokenMetadata
• TransferFeeConfig

Intentionally Absent

• Freeze Authority
• Mint Close Authority
• Permanent Delegate
• Non-Transferable
• Default Account State restrictions
• Confidential Transfer
• Transfer Hook
• Token-2022 Pausable

Actual deployed extension and authority state must be verified from Solana mainnet-beta before being represented as live.

────────

Transfer Fee Policy

|Parameter                |Policy                 |
|-------------------------|----------------------:|
|Launch transfer fee      |2% / 200 bps           |
|Governance policy ceiling|5% / 500 bps           |
|Token-2022 maximum fee   |368,920,000 EDEN       |
|Maximum fee base units   |368,920,000,000,000,000|

The 5% / 500 bps value is an EDEN governance policy ceiling.

It is distinct from Token-2022’s maximum_fee, which is an absolute token amount in the transfer-fee configuration.

────────

Market Model

Primary Acquisition

SOL → EDEN

Primary Liquidity Pair

WSOL / EDEN

Public interfaces display:

SOL / EDEN

The production design uses:

• Raydium CPMM for primary liquidity;
• Jupiter Swap API V2 for route discovery and transaction construction;
• EDEN-owned validation, simulation, policy, review, reconciliation, and receipts.

Secondary liquidity may include:

EDEN / USDC

> [!CAUTION]
> A configured market is not the same as a live market. Public trading status must be based on verified pool existence, active liquidity, successful buy/sell execution, and current Jupiter routing.

────────

Mint Governor

EDEN includes an Anchor-based mint-governor program for bounded, auditable issuance control.

Program ID
CVSkbcwhBszqgcJ3368nezg2e1tCuibDX96uwNwMQq48

The governor enforces:

• maximum outstanding supply;
• policy revision checks;
• stale supply protection;
• replay-resistant mint receipts;
• purpose-hash receipts;
• governed mint authority;
• burn-replacement accounting.

The same program identity may be deployed independently to Devnet and Mainnet.

────────

Repository Structure

.
├── .github/                  GitHub CI, security, release workflows
├── clusters/                 cluster profiles
├── config/                   composed token/market configuration
├── constants/                canonical IDs, mints, supply, URLs
├── context/                  runtime cluster bindings
├── deployments/              verified deployment state and receipts
├── env/                      environment templates only
├── manifests/                machine-readable protocol manifests
├── metadata/                 public Token-2022 metadata
├── programs/
│   └── mint-governor/        Anchor mint-governor program
├── public/
│   ├── README.md
│   └── assets/
│       └── eden.png
├── rpc/                      RPC policy
├── scripts/                  deployment and verification tooling
├── src/                      TypeScript implementation
├── tests/                    unit/integration tests
├── tokenomics/
│   └── public/               public tokenomics disclosure
├── Anchor.toml
├── Cargo.toml
├── DEVELOPMENT.md
├── SECURITY.md
├── TOKENOMICS.md
└── package.json

────────

Requirements

Node.js     >= 26
pnpm        12.6.0
TypeScript  ^7.0.2
Anchor      1.2.0
Solana CLI  4.1.2
SPL Token   Token-2022 capable

Install:

corepack enable
corepack prepare pnpm@12.6.0 --activate
pnpm install

Validate:

pnpm validate

────────

Development

Toolchain Check

pnpm doctor

For Solana/Anchor mainnet tooling:

pnpm doctor:mainnet

Unit Tests

pnpm test:unit

Rust Program

pnpm program:fmt
pnpm program:check
pnpm program:test

Anchor Build

pnpm platform:doctor
pnpm anchor:build

If macOS platform-tools fail with a rust-lld / __libcpp_verbose_abort incompatibility, see PLATFORM_TOOLS.md.

────────

Devnet

Canonical Devnet test mint:

testJiVWuSLXEwcLzJseBVfwUvigm28stUfCjegMKm8

Test Devnet connectivity and mint state:

pnpm test:devnet
pnpm rpc:test:devnet

Mint-governor status:

pnpm program:status:devnet

Dry-run deployment:

pnpm anchor:deploy:devnet

Execute only after review:

pnpm anchor:deploy:devnet -- --execute

────────

Mainnet-Beta

Canonical production mint address:

EDENTZYUTprUgAHdNxrBLMHQDnM5Aw7Pt5XSpLkFhfYx

Read-Only Discovery

pnpm token:discover
pnpm program:status:mainnet

Mainnet Preflight

pnpm doctor:mainnet
pnpm security:keypair
pnpm signers:check
pnpm token:create:guard

Mint Creation

token:create is dry-run by default:

pnpm token:create

Execution requires explicit review and the matching canonical mint keypair:

pnpm token:create -- --execute

> [!WARNING]
> Never run mainnet mint creation if the canonical mint already exists. Always run `pnpm token:discover` first.

────────

Signer Security

Private signing material must remain outside the repository.

Recommended locations:

$HOME/.eden/keypairs/EDENTZYUTprUgAHdNxrBLMHQDnM5Aw7Pt5XSpLkFhfYx.json
$HOME/.eden/keypairs/eden-mint-authority.json
$HOME/.eden/keypairs/eden-fee-payer.json
$HOME/.eden/keypairs/eden-mint-governor.json
$HOME/.eden/keypairs/eden-devnet-deployer.json
$HOME/.eden/keypairs/eden-mainnet-deployer.json

Recommended POSIX permissions:

chmod 700 "$HOME/.eden/keypairs"
chmod 600 "$HOME/.eden/keypairs/"*.json

Never commit, upload, log, screenshot, paste, or bundle:

• private keypair JSON;
• seed phrases;
• mnemonic phrases;
• raw signing keys;
• RPC API keys;
• treasury secrets;
• governance signer secrets.

Security documentation: SECURITY.md

────────

Metadata

Canonical metadata source:

metadata/metadata.json (commit-pin at release)

Public token image:

public/assets/eden.png

For a final immutable release, commit:

metadata/metadata.json
public/assets/eden.png

together and pin both to the same immutable Git commit.

────────

Verification

Once deployed, public verification should confirm:

Cluster                 mainnet-beta
Program                 Token-2022
Mint                    EDENTZYUTprUgAHdNxrBLMHQDnM5Aw7Pt5XSpLkFhfYx
Decimals                9
Outstanding Supply      ≤ 18,446,000,000 EDEN
Metadata                EDEN / EDEN / canonical URI
Required Extensions     Present
Forbidden Extensions    Absent
Freeze Authority        None
Mint Close Authority    None
Transfer Fee            Expected policy state
Mint Authority          Governed

Run production verification with:

pnpm token:verify:production

The Solana blockchain is authoritative for deployed supply, extensions, authorities, fee configuration, balances, token accounts, and transaction history.

────────

Public Documentation

• tokenomics/public/README.md — public tokenomics
• TOKENOMICS.md — implementation tokenomics
• DEVELOPMENT.md — engineering workflow
• SECURITY.md — signer and production security
• PLATFORM_TOOLS.md — Anchor/Solana build tooling
• MARKET_READINESS.md — market verification
• COMPLIANCE.md — technical compliance boundaries
• .github/README.md — GitHub automation and repository controls

────────

Public Links

• Website: https://edenlayer.ai
• Documentation: https://docs.edenlayer.ai
• X: https://x.com/edenlayer_ai

────────

License

Licensed under the Apache License 2.0.

See LICENSE.

────────

Disclosure

EDEN repository configuration and tokenomics describe the protocol’s technical and economic design.

They do not, by themselves, establish that a mint, liquidity pool, market, allocation, authority transition, vesting schedule, or circulating-supply value is live.

Mainnet deployment, market availability, liquidity, routing, supply, and authority state should only be represented as active after independent on-chain verification.

────────

<p align="center">
  <strong>EDEN Token 1.0.0</strong><br />
  Solana · Token-2022 · Governed Supply · SOL → EDEN
</p>
