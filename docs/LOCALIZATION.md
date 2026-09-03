# Localization

## Supported languages

The prototype currently supports:

- English (`en`)
- Portuguese (`pt`)

The source of truth is the `translations` object near the start of the inline JavaScript in `index.html`.

## Adding or changing text

1. Add the same key to both `en` and `pt` objects.
2. For static HTML, add `data-i18n="your_key"` to the element.
3. For an accessible name or tooltip, use `data-i18n-aria-label` or `data-i18n-title`.
4. For runtime copy, use `t('your_key')`.
5. Verify switching languages while the relevant screen or dialog is open.

Example:

```html
<button data-i18n="support">I need support</button>
```

```js
guidance.textContent = t('guidance_quiet');
```

## Writing guidance

Keep both translations calm, direct, and non-judgmental. Do not translate recovery terms mechanically if the result is unnatural in Portuguese. If production localization expands beyond Portuguese, have crisis and support wording reviewed by a qualified local reviewer.

## Language control

The compact `PT` / `EN` button toggles the active language. `applyLanguage()` updates static marked elements, live view copy, the phase label, document language, accessible labels, and the support sheet.
