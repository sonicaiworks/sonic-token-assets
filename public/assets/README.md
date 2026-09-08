<div align="center">

# SONIC Token Assets

### Canonical source and reference artwork

</div>

---

## Files

| File | Description | Format | Canonical role |
|---|---|---|---|
| `sonic.png` | Red SONIC token artwork | PNG | Token icon / metadata source |
| `sonic.svg` | SONIC waveform mark | SVG | Vector source |
| `coin.png` | Silver SONIC coin artwork | PNG | Tokenomics / marketing source |

## Recommended mapping

```text
Token metadata / wallet icon  → sonic.png
Scalable SONIC mark           → sonic.svg
Tokenomics / hero coin        → coin.png
```

## Source policy

`assets/` is the canonical source/reference layer.

Optimized website derivatives belong in `../images/`. Reusable interface marks belong in `../icons/`.

Do not overwrite source assets with resized, compressed, recolored, or platform-specific derivatives.

## Mainnet metadata

For final Token-2022 metadata publication, publish the selected token artwork and metadata JSON using a durable immutable storage strategy before setting the production metadata URI.
