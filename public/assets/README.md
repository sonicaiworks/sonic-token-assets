# SONIC Token Assets

Source/reference assets for SONIC Token.

| File | Description | Format |
|---|---|---|
| `sonic.png` | Canonical red SONIC token artwork | PNG / RGBA |
| `sonic.svg` | Vector SONIC waveform mark | SVG |
| `coin.png` | Silver SONIC coin artwork | PNG |

These are source/reference assets. Web-specific derivatives belong in `../images/`; reusable UI marks belong in `../icons/`.

## Recommended mapping

```text
Token metadata icon       → sonic.png
Scalable logo/brand mark  → sonic.svg
Tokenomics coin visual    → coin.png
```

For final on-chain metadata, publish the selected token icon and JSON metadata through an immutable storage strategy before setting the production metadata URI.
