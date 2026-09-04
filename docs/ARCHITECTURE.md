# Architecture

## Delivery model

Pausa Guiada is intentionally framework-free. The three HTML entry points contain their own markup, CSS, JavaScript, shaders, and local asset references:

- `index.html` is the High profile and canonical shared renderer.
- `mid.html` is the Mid portable profile.
- `low.html` is the Low portable profile.

`dist/` and `dist/static/` mirror these entry points for hosting. Keep each copy byte-for-byte synchronized with its source counterpart before publishing.

## Profiles and renderers

| Experience | High | Mid / Low |
| --- | --- | --- |
| Drift / Ondas | High-fidelity overhead ocean renderer with tap, hold, release, fish, rocks, and phases. | Portable Canvas ocean with rock-aware ripples, fish avoidance, tones, and layout shifting. |
| Ink / Tinta (High); Smoke / Fumaça (Mid/Low) | WebGL fluid solver with touch colour controls and palettes. | Portable coloured smoke renderer and palette switching. |
| Depths / Profundezas | Shared Canvas renderer. | Embeds High’s shared Depths renderer in an iframe. |
| Grass / Grama | Shared Canvas renderer. | Embeds High’s shared Grass renderer in an iframe. |

The embedded High scenes receive `embed=1`, `fps=15`, the current language, sound state, and session-duration messages from Mid/Low. This prevents the old separate portable Depths/Grass implementations from diverging.

## Shared session settings

### Duration

`pausa-session-minutes` is a device-local browser-storage preference. Allowed values are 5, 10, 15, and 20; invalid or unavailable values fall back to 10.

Each profile reads the setting during startup. Choosing a duration:

1. stores the setting;
2. resets that profile’s timer and progress bar;
3. sends the duration to an active embedded High scene; and
4. keeps the preference after refresh, mode changes, quality changes, and session completion.

High keeps `sessionMinutes`, `sessionDuration`, `remaining`, and `ended` in its session shell. Its phase timing, prompts, progress bar, and Grass growth use the duration as a proportion rather than assuming ten minutes. Mid and Low keep an equivalent portable countdown and dispatch `guided-reset` with the selected number of seconds.

### Other local preferences

- `pausa-lang` stores English or Portuguese.
- `pausa-sfx-muted` stores touch-sound state.
- `pausa-ambient-muted` stores ambient audio state.

Settings links include `quality=` so a manual profile choice remains an override of the automatic recommendation.

## Lifecycle and interaction

Only the active High renderer runs. Visual loops pause when the document is hidden. Rendering is capped and adaptive-resolution logic reduces work when necessary.

The portable profiles retain their own Drift and Smoke surfaces. A capture-phase mode handler switches Depths and Grass to the embedded shared scene; returning to Drift or Smoke removes the iframe scene and restores the portable canvas.

Pointer input is intentionally direct and low-precision:

- Drift: water-only tap makes a small ripple; hold/release makes a larger ripple.
- Smoke: tap or drag releases changing palette colours.
- Depths: swipe reveals water temporarily, then it recovers gradually.
- Grass: dragging bends stalks; growth occurs over the session.

## Maintaining the project

- Do not reintroduce standalone Mid/Low Depths or Grass renderers.
- Keep High-only visual changes isolated from portable replacements unless the user asks for parity.
- Keep support content, timer position, font treatment, and progress behavior aligned across profiles.
- Prefer fade or gradual change over abrupt visual transitions.
- Make any new user-visible copy available in both languages.
