# SONIC Token Runtime

Production-oriented Token-2022 runtime for SONIC Network.

> **Deployment state:** no verified SONIC mint address exists in the current `sonicaiworks/token` repository. `SONIC_TOKEN_MINT` therefore remains blank until `scripts/create-token-2022-mint.ts` is executed and the resulting address is independently verified. Never substitute another project’s SONIC mint.

Canonical policy

|Parameter                     |Value                                                    |
|------------------------------|---------------------------------------------------------|
|Network                       |Solana                                                   |
|Standard                      |Token-2022                                               |
|Decimals                      |9                                                        |
|Initial maximum supply        |18,446,000,000 SONIC                                     |
|Atomic maximum supply         |18,446,000,000,000,000,000                               |
|Token-2022 transfer fee       |200 bps / 2%                                             |
|SONIC fee-rate policy cap     |500 bps / 5%                                             |
|Absolute Token-2022 maximumFee|Deployment input; not invented                           |
|Quarterly burn policy         |200 bps / 2%; disabled until calculation base is approved|
|Locked supply designation     |3,000,000,000 SONIC via Streamflow policy                |

The atomic maximum deliberately fits within a Solana u64, leaving 744,073,709,551,615 atomic units of headroom.

Architecture

```text
programs/sonic/token/src/      Anchor policy registry
scripts/                       Mint/genesis/verify/pricing CLIs
env/                           Typed runtime environment
constants/                     Program IDs, token policy, URLs
context/                       Request/token context
components/services/           Provider adapters
lib/                           RPC, token, cache, rate limit, safe actions
utils/                         Errors, amount helpers
common/                        API response/price contracts
types/                         Actions, status, chart types
data/                          Metadata, tokenomics, deployment manifest
app/api/v1/                    SONIC Token REST API
api/swagger/                   OpenAPI 3.1
postman/                       Postman collection
tests/                         Policy/unit tests
target/                        Generated Anchor artifacts (gitignored)
```

Install

```bash
corepack enable
pnpm install
cp .env.example .env.local
pnpm validate
pnpm test
pnpm typecheck
pnpm dev
```

Mint lifecycle

```text
POLICY_VALIDATED
      ↓
TOKEN-2022 MINT CREATED
      ↓
METADATA INITIALIZED
      ↓
MINT ADDRESS RECORDED
      ↓
ON-CHAIN VERIFICATION
      ↓
GENESIS SUPPLY MINTED
      ↓
TREASURY RECONCILED
      ↓
OPTIONAL MINT AUTHORITY REVOCATION
      ↓
PRODUCTION REGISTRY PUBLISHED
```

1. Configure the absolute transfer-fee maximum

Token-2022 requires an absolute maximumFee token amount in addition to the 200 bps rate. Set it explicitly:

```bash
SONIC_TRANSFER_FEE_MAXIMUM_FEE_ATOMIC=<approved-u64-amount>
```

2. Create mint

```bash
pnpm mint:create
```

This creates a Token-2022 mint with TransferFeeConfig and MetadataPointer, initializes native Token-2022 metadata, and writes the result to the gitignored data/deployment.local.json.

3. Publish mint address into environment

```bash
SONIC_TOKEN_MINT=<actual-created-address>
```

4. Verify

```bash
pnpm verify:onchain
```

5. Genesis mint

Set SONIC_TREASURY_ADDRESS, then:

```bash
pnpm mint:genesis
```

The script refuses to run when mint supply is already non-zero. Set SONIC_REVOKE_MINT_AUTHORITY_AFTER_GENESIS=true only after the final issuance policy is approved.

API

• GET /api/v1/health
• GET /api/v1/token
• GET /api/v1/token/mint
• GET /api/v1/token/metadata
• GET /api/v1/token/supply
• GET /api/v1/token/verify
• GET /api/v1/token/fees?amountAtomic=
• GET /api/v1/token/price?mint=
• GET /api/v1/token/holders?mint=
• GET /api/v1/token/market?mint=
• GET /api/v1/market/swap-quote?inputMint=&outputMint=&amount=
• GET /api/v1/integrations/health
• GET /api/v1/actions
• POST /api/v1/music/generate (internal key + configured Suno Platform only)
• GET /api/swagger

Live data routing

```text
Pyth (only configured feed IDs)
  ↓
Jupiter Price V3
  ↓
Birdeye
  ↓
CoinGecko / GeckoTerminal
  ↓
Helius DAS
  ↓
Solscan
  ↓
Raydium
  ↓
Orca
```

Pyth is not assigned a fake SONIC feed ID. Until a verified SONIC Pyth feed exists, SONIC market pricing falls through to market/indexer sources.

Program IDs

The repo pins verified public IDs for System Program, SPL Token, Token-2022, Associated Token, Metaplex Token Metadata, Bubblegum V2, Account Compression, SPL Noop, and current Pyth receiver/price-feed programs in constants/programs.ts.

The custom Anchor program ID in this scaffold is a development placeholder. Run anchor build && anchor keys sync before deploying it.

External providers

Adapters are included for Helius RPC/DAS, Pyth Hermes, Jupiter, Birdeye, CoinGecko, Solscan, Raydium, Meteora DLMM, Orca, Magic Eden and Suno Platform. API-key-backed services are disabled until their secrets are configured.

Security

Minting is intentionally CLI-only, not an HTTP endpoint. The API provides read/verify/quote surfaces, and the Suno write proxy requires x-sonic-api-key. For production, replace in-memory rate limiting/cache with shared infrastructure if the API runs across multiple server instances.

Documentation

• docs/token/ — full SONIC token/tokenomics/security documentation
• docs/runtime/API.md — API v1 route contract
• docs/runtime/PROVIDERS.md — live provider architecture
• api/swagger/openapi.yaml — OpenAPI 3.1
• postman/SONIC-Token-API.postman_collection.json — Postman collection
• VALIDATION_REPORT.md — executed validation status and environment limitations
