# Serenia

Serenia is a mobile-first, portrait-first recovery-support prototype. It offers calm, interactive visual experiences intended to help a person stay with a craving while it rises and passes. It is a static web app: there is no backend, account, analytics, or network dependency.

## Experiences

- **Tide / Maré** — overhead water, rocks, fish, and rock-aware tap or hold ripples.
- **Mist / Nuvem** — touch-driven coloured fluid or smoke with selectable palettes.
- **Depths / Profundeza** — temporarily reveal a hidden underwater world by swiping through murky water.
- **Meadow / Campo** — brush responsive grass and slowly growing shoots.

## Quality profiles

The app has three separate entry points so the high-fidelity renderer remains isolated:

| Profile | Entry point | Intended use |
| --- | --- | --- |
| High | `index.html` | Full WebGL/Canvas experience. |
| Mid | `mid.html` | Portable 2D ocean/smoke treatment; shared Depths and Grass scene. |
| Low | `low.html` | Lower-cost portable ocean/smoke treatment; shared Depths and Grass scene. |

The app recommends a profile using device capability heuristics. Users can override it from Settings; an explicit quality choice always wins. Depths and Grass use the same shared scene in every profile, with lower rendering targets in Mid and Low.

## Session duration

Settings offers 5, 10, 15, and 20 minute sessions. The default is 10 minutes.

- Selecting a duration resets the shared countdown and progress bar immediately.
- The duration is saved in browser storage under `serenia-session-minutes` and is reused after refresh and when moving between quality profiles.
- A completed session keeps the selected duration until the user changes it.
- Prompts, Drift phase timing, progress, and Grass growth scale proportionally to the selected duration.

## Run locally

Open `index.html` in a modern browser for a quick check. A local static server is preferable for device testing:

```sh
python3 -m http.server 4173 --bind 127.0.0.1
```

Visit `http://127.0.0.1:4173/`. Use `/mid.html` or `/low.html` to test the portable profiles.

Useful query parameters:

- `mode=drift|fluid|water|grass` in High.
- `mode=drift|ink|depths|grass` in Mid and Low.
- `lang=en|pt` overrides the interface language for testing or a deep link. Otherwise, first launch follows the phone/browser locale; an in-app language choice is remembered.
- `quality=high|mid|low` preserves a deliberate quality choice.

## Project structure

```text
index.html                 High profile application and shared Depths/Grass renderer
mid.html                   Mid portable profile
low.html                   Low portable profile
assets/                    Wave favicon/PWA PNGs and local ambient audio tracks
site.webmanifest           PWA metadata
docs/ARCHITECTURE.md       Renderer, profile, settings, and timer design
docs/LOCALIZATION.md       English/Portuguese copy workflow
CONTRIBUTING.md            Development and regression-check guidance
dist/                      Deployment mirror of the HTML entry points (ignored by Git)
```

## Browser support

Test on current iOS Safari, Android Chrome, and desktop Chromium/Safari before release. High requires working WebGL for its full visual quality. Mid and Low are designed as lower-cost alternatives, while preserving the primary recovery interactions.

The app includes the supplied wave artwork as a PNG favicon, Apple touch icon, and 192/512px PWA icons. It does not include a service worker, so do not rely on offline installation yet.

## Safety note

This prototype is a grounding and distraction aid, not crisis care or a substitute for clinical treatment. A production integration should keep regional crisis, emergency, sponsor, peer-support, and recovery-resource contacts current.

## License

No license has been selected. Add a `LICENSE` file before public reuse.
