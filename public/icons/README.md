<div align="center">

# SONIC Icons

### Vector and raster logo variants for application UI

</div>

---

```text
icons/
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

## Logo variants

| File | Purpose |
|---|---|
| `sonic.svg` | Shared canonical vector mark |
| `logo/sonic.svg` | Primary scalable logo |
| `logo/sonic-black.svg` | Dark mark for light surfaces |
| `logo/sonic-white.svg` | Light mark for dark surfaces |
| `logo/sonic.png` | Full red token icon |
| `logo/sonic-512.png` | 512px raster fallback |
| `logo/sonic-256.png` | 256px raster fallback |
| `logo/sonic-128.png` | 128px raster fallback |
| `logo/coin.png` | Silver coin preview/icon |

Prefer SVG for product UI unless a target platform explicitly requires raster output.
