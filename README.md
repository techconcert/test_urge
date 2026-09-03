# Guided Relief

Guided Relief is a single-file, mobile-first prototype for a short recovery-support practice. It offers several calm, visual grounding experiences designed to occupy attention while an urge rises and passes.

The prototype is intentionally self-contained: there is no build system, dependency install, account, analytics, or backend.

## Experiences

- **Flow** — crisp WebGL impasto water flowing around rocks.
- **Drift** — a slow aerial water journey with gentle discoveries.
- **Ink** — touch-driven WebGL fluid simulation.
- **Depths** — a Canvas pond where touch clears temporary windows through murky water.
- **Grass** — touch-responsive grass stalks.
- **Anchor** — an ocean journey with tap, hold, release, and finger-ripple interaction.

All views share one ten-minute countdown. The interface is available in English and Portuguese.

## Run locally

Open `index.html` directly in a modern browser for a quick look. For the most reliable WebGL behaviour, serve the folder with any static server:

```sh
python3 -m http.server 4173 --bind 127.0.0.1
```

Then visit `http://127.0.0.1:4173`.

## Project structure

```text
index.html                 Application, styles, GLSL, and JavaScript
docs/ARCHITECTURE.md       Rendering modules and session behaviour
docs/LOCALIZATION.md       English/Portuguese translation workflow
CONTRIBUTING.md            Development and review guidance
```

## Browser support

The visual modes use WebGL/WebGL 2 or Canvas 2D. Test on current iOS Safari, Android Chrome, and desktop Chromium/Safari before production release. The Ink mode needs WebGL 2 with floating-point color-buffer support; other modes degrade independently if their required graphics API is unavailable.

## Safety note

This prototype is a grounding and distraction aid, not crisis care or a substitute for clinical treatment. Keep regional crisis, emergency, sponsor, peer-support, and recovery-resource contacts current in any production integration.

## License

No license has been selected yet. Add a `LICENSE` file before publishing publicly so reuse terms are clear.
