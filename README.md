# Fibonacci Circles — Generative Art

> A seed-based generative system for Fibonacci-scaled ellipse ring compositions.  
> A reproducible catalogue of computational series studies.

---

## What is this?

**Fibonacci Circles** is a generative design system built on the Fibonacci series. Ellipses are sized by the series numbers, stacked concentrically at incrementing rotations, so that each ring is a little further turned than the one before it. Three seeded colours thread through the sequence; a saturated ground holds it all in place. Thirty scattered lines cross the composition at random, cutting the symmetry with raw gesture.

Every artwork in this catalogue is defined by a single numeric seed. The same seed always produces the identical composition — making each piece **traceable, reproducible, and licensable** across textile, print, and apparel applications.

Named for the integer sequence that governs the ring sizes, **Fibonacci Circles** reframes mathematical growth as a textile.

---

## Live

🌐 **[View the catalogue →](https://reyrove.github.io/Fibonacci-Circles/)**

---

## The System

The generator combines three layers:

| Layer | Description |
|-------|-------------|
| **Ground** | A saturated background: random hue, saturation 50–255, brightness 20–80. |
| **Fibonacci rings** | Ellipses sized by the Fibonacci series up to 1000, stacked at incrementing rotations. |
| **Crossed lines** | 30 random lines drawn over the stack, sampled from the three-colour palette. |

All three layers are driven by the same seed, ensuring deterministic output.

### Parameters

- **Fibonacci series** — 0, 1, 1, 2, 3, 5, 8, 13, 21, ... up to 1000
- **Ring size** — `fib[i] × canvas / 2000` plus a small seeded jitter of `±canvas/100`
- **Ring rotation** — `startAngle + i × 0.2` radians
- **Ring stroke weight** — 1 to 4, scaled by `canvas / 500`
- **Line count** — 30
- **Line stroke weight** — 0.5 to 2, scaled by `canvas / 500`
- **Colour mode** — HSB (360, 255, 255)
- **Palette** — 3 seeded colours, cycled through the rings

---

## Structure

```
Fibonacci-Circles/
├── index.html              ← Full catalogue (single-file)
├── images/
│   ├── fav.svg
│   ├── fibonacci-tote.png
│   ├── fibonacci-cushion.png
│   └── ...
├── Fibonacci-Circles.jpg   ← Apparel mockup
└── README.md
```

The entire project is contained in a single `index.html` — no build step, no framework. The only external dependency is **p5.js** (loaded from CDN), which drives the exact sketch pipeline.

---

## Features

- **Seed-based generation** — every composition is deterministic and reproducible
- **Same seed, many surfaces** — the plate, cover, framed print, and all four surface swatches render from the same seed
- **Tiled rectangular surfaces** — scarves, textiles, and wallpaper tile the square composition to fill their aspect ratio, preserving the visual identity
- **Archive of 8 seeds** — each thumbnail is a *different* composition; click one to load it into the plate, and every surface follows
- **Live animation** — the plate runs continuously; the cover and framed plate auto-stop after 2 seconds
- **PNG export** — download the current frame of the plate directly from the browser
- **Keyboard shortcuts** — `R` for new seed, `S` to save
- **Legal modal** — licensing, terms, and credits built in
- **Responsive** — works on desktop, tablet, and mobile
- **Mobile-first navbar** — horizontally scrollable with fade hint

---

## Usage

### Generate a new composition

Click **New Seed** or press `R`.

### Download the current frame

Click **Download** or press `S`.

### Load a seed from the archive

Click any plate in the **Archive** section. The plate, cover, framed print, and every surface swatch update to that seed.

---

## Color System

Every composition is drawn from three seeded colours, chosen per seed in HSB space:

- **Three ellipse colours** — each a fully random hue, saturation, and brightness, drawn independently per seed
- **Background** — a saturated ground: random hue, saturation between 50 and 255, brightness between 20 and 80
- **Ring colour** — cycles through the three ellipse colours by index (`i % 3`), so every third ring repeats
- **Line colour** — sampled from the same three-colour palette at random

Because the seed picks both the palette and the geometry, no two compositions share the same rhythm of colour and shape.

---

## Surfaces — one seed, many ratios

Every surface in the catalogue is drawn from the same seed. The rectangular surfaces tile the square composition to fill their aspect ratio:

| Surface | Ratio | Tiling |
|---------|-------|--------|
| **Print** | 1 : 1 | 1 × 1 — identical to the plate |
| **Scarf** | 3 : 1 | 3 × 1 — composition repeated 3× horizontally |
| **Textile** | 4 : 3 | 2 × 2 — composition repeated 2× in both directions |
| **Wall** | 2 : 3 | 1 × 2 — composition repeated 2× vertically |

Every tile uses the same seed with a fresh RNG reset, so all tiles are visually identical. This is exactly what a repeat pattern looks like — one motif, tiled.

---

## Technical Notes

- **p5.js** drives the composition. `ellipse()`, `line()`, and `stroke()` are used natively in HSB colour mode.
- **Seeded randomness** uses a Lehmer LCG. Same seed → same palette, same rotations, same jitter on every ring, same 30 lines.
- **Live plate** — 30fps. The plate's `draw()` runs continuously until the page is hidden.
- **Cover and framed plate** — 20fps, auto-stop after 2 seconds.
- **Frozen stills** — the four surface swatches and eight archive thumbnails run 2 frames then freeze.
- **Off-screen pause** — an `IntersectionObserver` calls `noLoop()` on live instances that scroll out of view.
- **`prefers-reduced-motion` respected.**

---

## About

**Fibonacci Circles** is a project by [Reyhaneh Daneshdoost](https://reyrove.github.io/) — an Iranian-born artist working at the intersection of classical textile logic and generative systems.

The work begins with a simple observation: the woven surface — repetitive, mathematically structured, infinitely variable — has always been a form of computation, long before computers.

**Fibonacci Circles** is an attempt to render that logic visible.

> *Each ring is the sum of the last two — and every ring is larger than both.*

---

## Licensing

All compositions are seed-documented and available for licensing across textile, surface, and apparel applications.

For commercial use, custom editions, or exclusive rights:

📧 **reyhanehdaneshdoost@gmail.com**

See the **Licensing** section in the live catalogue for details.

---

## Links

- 🌐 [Website](https://reyrove.github.io/)
- 📷 [Instagram](https://www.instagram.com/rey._.rove/)
- 💼 [LinkedIn](https://www.linkedin.com/in/reyhaneh-daneshdoost-730481160/)
- 🐦 [X](https://x.com/reyrove)

---

## Credits

**Design & Generative System**  
Reyhaneh Daneshdoost

**Typefaces**  
Cormorant Garamond · DM Mono

**Edition**  
Fibonacci Circles — Autumn 2026

---

<p align="center">
  <em>Generative Fibonacci Ring</em><br />
  <sub>© Reyrove Studio · All compositions reproducible by seed</sub>
</p>