# Contributing

## Development principles

- Keep the app mobile-first and portrait-first.
- Preserve the dependency-free static delivery model unless there is a deliberate product decision to change it.
- Prefer calm, predictable motion over surprise, gamification, or rapid autonomous movement.
- Keep the High profile isolated from Mid/Low portable implementations.
- Do not add tracking, remote assets, or network calls without an explicit privacy and product decision.
- Preserve a single shared timer setting across modes and quality profiles.

## Before submitting a change

Test each profile separately:

1. **High**: Drift, Smoke, Depths, Grass, all bottom controls, themes, palette sheets, support modal, settings, audio controls, language switch, and timer reset.
2. **Mid and Low**: Drift and Smoke input, tone/shift controls, theme switching, support modal, settings, language switch, and the shared embedded Depths/Grass scenes.
3. **Timer**: Select 5, 10, 15, and 20 minutes. Each selection must reset the clock and progress bar, survive refresh, survive a mode or quality change, and remain selected after completion.
4. **Touch**: Confirm Drift ripples are water- and rock-aware, Smoke responds to drag, Depths reveals temporarily, and Grass bends without random stalk replacement.
5. **Accessibility and layout**: Test a narrow phone viewport, a two-line title case, English and Portuguese, and ensure timer/title/instruction positions remain stable.
6. **Performance**: Confirm visual loops pause in a backgrounded tab and that the intended profile remains smooth on the target device.

## Documentation and deployment copies

- Update `README.md`, `docs/ARCHITECTURE.md`, and `docs/LOCALIZATION.md` whenever architecture, settings, language, or user flow changes.
- Synchronize `index.html`, `mid.html`, and `low.html` into both `dist/` and `dist/static/` before deployment.
- Parse every inline script and run `git diff --check` before publishing.
- Keep old renderers out of backups or hidden code paths; Git history is the recovery mechanism.

## Pull requests

- Describe the interaction and recovery-experience impact in plain language.
- Include a mobile screenshot or short recording for visual changes.
- Call out changes to timing, session duration, motion, translations, support language, accessibility, or performance.
- Keep unrelated cleanup separate from behavior changes where practical.
