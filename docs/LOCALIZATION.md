# Localization

## Supported languages

The app supports English (`en`) and Brazilian Portuguese (`pt`). Portuguese is the default when no saved language preference or `lang` query parameter is present.

Each entry point owns its profile-specific dictionary:

- High: `translations` in `index.html`.
- Mid: `I18N` in `mid.html`.
- Low: `I18N` in `low.html`.

When changing a shared label, update all three dictionaries. High also forwards language changes to an embedded Depths or Grass scene.

## Adding or changing text

1. Add the same semantic key to both `en` and `pt` dictionaries in every relevant profile.
2. Mark static HTML with `data-i18n="your_key"`.
3. Use `data-i18n-aria-label` or `data-i18n-title` for accessible labels and tooltips.
4. Use `t('your_key')` for runtime content.
5. Verify both languages while the relevant mode, Settings modal, palette, and support sheet are open.

## Current naming

Use the same short name in the top navigation and main title within each profile:

| Experience | High (English / Portuguese) | Mid and Low (English / Portuguese) |
| --- | --- | --- |
| Drift | Drift / Ondas | Drift / Ondas |
| Fluid / smoke | Ink / Tinta | Smoke / Fumaça |
| Depths | Depths / Profundezas | Depths / Profundezas |
| Grass | Grass / Grama | Grass / Grama |

Theme names are also localized. Avoid literal translations that sound unnatural in recovery-oriented Brazilian Portuguese.

## Writing guidance

Keep recovery language calm, direct, and non-judgmental. Do not imply failure, urgency, or a guarantee of treatment. If production localization expands beyond Portuguese, have recovery, crisis, and support language reviewed by a qualified local reviewer.
