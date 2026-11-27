# Ink Usage Calculator · Flexo & Gravure

A free, zero-dependency web tool that estimates **water-based ink consumption and cost** for flexographic and gravure printing — with a built-in dynamic waste factor, CMYK per-colour breakdown and indicative USD pricing.

It is a standalone, self-contained single HTML file. No build step, no frameworks, no external assets — open it and it works, offline included.

> Maintained by **[Star Color](https://www.starcolor-ink.com/)** · Water-based ink manufacturer.

---

## Features

- **Flexo & Gravure modes** — inputs switch between anilox roll LPI and gravure plate depth.
- **Substrate correction** — Paper, plastic film (BOPP/PET/PE) and aluminium foil.
- **Dynamic waste factor** — 18% under 2,000 m², 12% at 2,000–10,000 m², 8% above 10,000 m²; press speed above 200 / 300 m/min adds an extra allowance.
- **CMYK breakdown** — Black ≈ 30%, Cyan 20%, Magenta 25%, Yellow 25% of total volume.
- **Indicative cost** — water-based ink pricing of $4–5/kg by substrate.
- **Reference tables** — flexo anilox LPI and gravure plate depth cheat sheets.
- **Responsive & accessible** — works on mobile, keyboard-friendly form controls.

## Quick start

Just open `index.html` in any modern browser.

```bash
# optional: serve locally
python -m http.server 8080
# then visit http://localhost:8080
```

## Deploy on GitHub Pages

1. Push this repository to GitHub.
2. Go to **Settings → Pages**.
3. Under **Build and deployment**, select **Deploy from a branch** → `main` → `/ (root)`.
4. Save. Your calculator is live at `https://<username>.github.io/<repo>/`.

Because everything is in a single `index.html`, no configuration or build pipeline is required.

## How the estimate is calculated

The tool follows the classic relationship:

```
Ink (kg) = Area × Coverage × WetLaydown × 4 colours × SubstrateFactor × SpeedFactor / 1000
Total     = Ink × (1 + WasteFactor)
```

| Input | Effect |
|---|---|
| Anilox LPI (flexo) | 200 → 7.5 BCM · 360 → 4.4 · 400 → 3.7 · 600 → 2.5 · 800 → 1.8 · 1000 → 1.35 · 1200 → 1.05 |
| Plate depth (gravure) | 20 → 4.0 BCM · 25 → 5.0 · 30 → 6.0 · 35 → 7.0 |
| Wet laydown | `BCM × 2.8` g/m² (single colour) |
| Substrate | Paper 1.2 · Film 0.95 · Aluminium foil 0.90 |
| Speed | >200 m/min → ×1.05 · >300 m/min → ×1.10 |
| Waste | <2,000 m² → 18% · 2,000–10,000 m² → 12% · >10,000 m² → 8% |

> The formula mirrors the live calculator on [starcolor-ink.com](https://www.starcolor-ink.com/info/estimate-ink-usage.html) so results match exactly.

## Project structure

```
ink-usage-calculator/
├── index.html   # the entire tool (HTML + CSS + JS)
└── README.md
```

## Disclaimer

Results are **planning estimates** for standard 4-colour CMYK process work (typically within ±10–15% of real consumption). Spot colours, heavy white on film and highly absorbent kraft can shift consumption. For an exact quotation, send your artwork and substrate to our lab.

## Contact

- Website: [www.starcolor-ink.com](https://www.starcolor-ink.com/)
- Free 5 kg samples: [Request a sample](https://www.starcolor-ink.com/contact/?type=sample#leave-messasge)
- Technical team: [Contact us](https://www.starcolor-ink.com/contact/?type=technical#leave-messasge)

© Huizhou Star Color Technology Co., Ltd. All rights reserved.
