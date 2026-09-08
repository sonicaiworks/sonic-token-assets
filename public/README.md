<div align="center">

# SONIC · Public Assets

### Token artwork · Coin visuals · Web images · SVG icons

[SONIC Network](https://sonicnetwork.ai) ·
[Tokenomics](https://token.sonicnetwork.app) ·
[Docs](https://docs.sonicnetwork.app)

</div>

---

## Overview

`public/` is the canonical runtime-facing asset layer for SONIC Token and SONIC Network interfaces.

The package separates **source assets**, **optimized web imagery**, and **reusable icons** so applications can select the correct format without duplicating or modifying canonical originals.

```text
public/
├── README.md
├── manifest.json
│
├── assets/
│   ├── README.md
│   ├── sonic.png
│   ├── sonic.svg
│   └── coin.png
│
├── images/
│   ├── README.md
│   ├── sonic.webp
│   └── sonic-red.webp
│
└── icons/
    ├── README.md
    ├── sonic.svg
    └── logo/
        ├── coin.png
        ├── sonic.svg
        ├── sonic-black.svg
        ├── sonic-white.svg
        ├── sonic.png
        ├── sonic-512.png
        ├── sonic-256.png
        └── sonic-128.png
```

## Canonical asset map

| Path | Role | Preferred use |
|---|---|---|
| `assets/sonic.png` | Canonical red SONIC token artwork | Token metadata, wallets, explorers, repository/docs |
| `assets/sonic.svg` | Canonical vector waveform mark | Source brand/vector asset |
| `assets/coin.png` | Silver SONIC coin artwork | Tokenomics, marketing, documentation |
| `images/sonic.webp` | Optimized silver coin | Hero sections, token cards, tokenomics UI |
| `images/sonic-red.webp` | Optimized red token | Alternate product/brand surfaces |
| `icons/sonic.svg` | Shared vector mark | Generic UI imports |
| `icons/logo/sonic.svg` | Primary scalable logo | Headers, navigation, components |
| `icons/logo/sonic-black.svg` | Dark monochrome logo | Light backgrounds |
| `icons/logo/sonic-white.svg` | Light monochrome logo | Dark backgrounds |
| `icons/logo/sonic.png` | Square red token icon | Wallet/token UI raster fallback |
| `icons/logo/coin.png` | 512px silver coin | Token cards and previews |

---

## Usage

### HTML

```html
<img src="/icons/logo/sonic.svg" alt="SONIC" />
```

### Next.js

```tsx
import Image from "next/image";

<Image
  src="/images/sonic.webp"
  alt="SONIC Token"
  width={1500}
  height={1500}
  priority
/>
```

### CSS

```css
.sonic-logo {
  background: url("/icons/logo/sonic.svg") center / contain no-repeat;
}
```

---

## Asset rules

- Use **SVG** for scalable interface marks.
- Use **WebP** for web imagery where supported.
- Use **PNG** for wallet, explorer, metadata, social, and integration fallbacks.
- Keep `assets/` as the source/reference layer.
- Keep optimized derivatives in `images/`.
- Keep reusable UI marks in `icons/`.
- Do not overwrite source artwork when generating new sizes or formats.
- Do not use mutable branch URLs for final immutable token metadata.
- Use the committed manifest to verify file identity and integrity.

---

## Integrity

`manifest.json` records canonical paths, dimensions, byte sizes, and SHA-256 hashes for public assets.
