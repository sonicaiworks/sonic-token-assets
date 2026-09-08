# SONIC Public Assets

Canonical public asset package for the SONIC Token and SONIC Network interfaces.

## Structure

```text
public/
├── README.md
├── manifest.json
├── assets/
│   ├── README.md
│   ├── sonic.png
│   ├── sonic.svg
│   └── coin.png
├── images/
│   ├── README.md
│   ├── sonic.webp
│   └── sonic-red.webp
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

## Asset contract

| Path | Role | Recommended use |
|---|---|---|
| `assets/sonic.png` | Canonical red SONIC token artwork | Token metadata fallback, repository/docs |
| `assets/sonic.svg` | Canonical vector waveform mark | Brand/source asset |
| `assets/coin.png` | Silver SONIC coin artwork | Tokenomics, marketing, documentation |
| `images/sonic.webp` | Optimized silver SONIC coin | Web hero/cards/tokenomics UI |
| `images/sonic-red.webp` | Optimized red SONIC token | Web product surfaces |
| `icons/sonic.svg` | Shared vector mark | UI imports |
| `icons/logo/sonic.svg` | Primary vector logo mark | Headers, navigation, scalable UI |
| `icons/logo/sonic-black.svg` | Monochrome dark mark | Light surfaces |
| `icons/logo/sonic-white.svg` | Monochrome light mark | Dark surfaces |
| `icons/logo/sonic.png` | Square red token icon | Wallet/token UI fallback |
| `icons/logo/coin.png` | 512 px silver coin | Token cards and previews |

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
.brand-mark {
  background-image: url("/icons/logo/sonic.svg");
}
```

## Rules

- Prefer SVG for scalable interface marks.
- Prefer WebP for website imagery.
- Keep `assets/` as the canonical source/reference layer.
- Use PNG when a wallet, explorer, metadata consumer, or integration does not reliably support SVG/WebP.
- Do not overwrite the canonical source asset when creating optimized derivatives.
- Token metadata should use an immutable URL after final mainnet publication.
