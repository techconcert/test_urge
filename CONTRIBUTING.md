# Contributing

## Development principles

- Keep the app mobile-first and portrait-first.
- Preserve the single-file delivery model unless there is a deliberate product decision to introduce a build step.
- Favour slow, predictable motion over novelty, surprise, or reward-like interactions.
- Keep every experience independently removable: a view should not depend on another visual module.
- Do not add tracking, remote assets, or network calls without an explicit privacy and product decision.

## Local checks

1. Serve the project from a local static server.
2. Test at a narrow mobile viewport (for example, 390 × 844) and desktop width.
3. Switch through every experience and confirm the shared timer does not reset.
4. Test Anchor tap, hold, release, and drag interactions.
5. Test Depths and Grass with touch or pointer input.
6. Switch between English and Portuguese, including the support sheet.
7. Review the browser console for WebGL and JavaScript errors.

## Changes to copy or translation

Do not hard-code new user-visible strings. Add an English and Portuguese entry to the `translations` object in `index.html`, then reference it with `t('key')` or a `data-i18n` attribute. See [Localization](docs/LOCALIZATION.md).

## Pull requests

- Describe the experience and interaction change in plain language.
- Include a mobile screenshot or short recording for visual changes.
- Call out any change to timing, motion, support language, or accessibility.
- Keep unrelated formatting changes out of the same pull request.
