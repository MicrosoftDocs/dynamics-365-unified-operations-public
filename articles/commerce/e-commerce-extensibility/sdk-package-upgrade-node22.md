---
title: Package upgrade guide for Node.js 22 compatibility
description: Learn about the package changes introduced to support Node.js 22 in the Dynamics 365 Commerce online SDK, and how to update your environment.
author: mithunbobade
ms.date: 04/03/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: mithunbobade
ms.search.validFrom: 2026-04-03
ms.custom:
  - bap-template
---
# Package upgrade guide for Node.js 22 compatibility

[!include [banner](../includes/banner.md)]

This article describes the package changes introduced in the Dynamics 365 Commerce online SDK to support Node.js 22, and provides guidance for customers who upgrade to SDK packages that include these changes.

The current packages include dependency updates that are compatible with Node.js 16, 18, and 22.

## What changed

### node-sass replaced with sass (Dart Sass)

The `node-sass` package has been replaced with `sass` (Dart Sass) in the SDK. This is the most significant change for customers upgrading to these packages.

| | Before | After |
|---|---|---|
| **Package** | `node-sass: ^9.0.0` | `sass: ^1.77.0` |
| **Type** | Native binary (LibSass) | Pure JavaScript (Dart Sass) |
| **Node.js 22 support** | No — fails to compile on Node.js 22 | Yes |

The `node-sass` package is deprecated and fails to compile on Node.js 22. Dart Sass (`sass`) is the official successor and is fully compatible with Node.js 16, 18, 20, and 22.

In addition, a Yarn resolution alias is added to redirect any transitive `node-sass` dependency (from upstream packages like `bootstrap` and `jest-css-modules-transform`) to Dart Sass:

```json
"resolutions": {
    "node-sass": "npm:sass@^1.77.0"
}
```

### node-gyp updated to ^9.4.1

The `node-gyp` resolution was updated from `^8.4.1` to `^9.4.1`. This provides Node.js 22 ABI header support while maintaining backward compatibility with Node.js 16 and later.

`node-gyp` is only invoked as a fallback when a native module has no prebuilt binary for the current platform. This change has no visible impact on day-to-day development.

## Impact on customers upgrading packages

### SCSS compilation behavior change

Migrating from `node-sass` (LibSass) to Dart Sass may expose SCSS syntax issues that LibSass silently accepted but Dart Sass treats as errors.

#### Invalid parent selector `&` at `@media` top level

LibSass accepted the following syntax, but Dart Sass rejects it with `Top-level selectors may not contain the parent selector "&"`:

```scss
// Incorrect — Dart Sass will error
@media (max-width: 768px) {
    &.col-sm:last-child .ms-content-block[data-m-layout="tile"]:last-child {
        padding-bottom: 20px;
    }
}

// Correct — remove the & prefix
@media (max-width: 768px) {
    .col-sm:last-child .ms-content-block[data-m-layout="tile"]:last-child {
        padding-bottom: 20px;
    }
}
```

> [!NOTE]
> The SDK theme packages (`starter-theme-pack`, `adventureworks-theme-kit`, `fabrikam-design-kit`) have been updated to fix this issue. If you have custom SCSS that extends these themes, review your files for the same pattern.

#### Empty pseudo-class argument

LibSass accepted `:nth-last-child()` with no argument, but Dart Sass enforces the CSS `An+B` syntax and rejects it:

```scss
// Incorrect — Dart Sass will error
&:nth-last-child() {
    border-bottom: none;
}

// Correct — use :last-child or a valid An+B expression
&:last-child {
    border-bottom: none;
}
```

#### Slash division deprecation warnings

Dart Sass generates deprecation warnings for `/` used as a division operator outside of `calc()`. These are **warnings only** and do not block compilation in Dart Sass 1.x. They will become errors in Dart Sass 2.0.

```scss
// Deprecated — generates warning
width: $total-width / 2;

// Recommended
width: math.div($total-width, 2);
// or
width: calc($total-width / 2);
```

You can safely ignore these warnings for now. Microsoft will provide guidance when Dart Sass 2.0 support is required.

### sass-loader compatibility

`sass-loader@13.x` is fully compatible with Dart Sass. No changes are required to your webpack configuration.

### canvas package (test environments only)

The `canvas` package is a test dependency used by jest/jsdom. It is not used in server-rendered pages or build output.

- **Node.js 16, 18:** `canvas@2.x` is included and works without any additional steps.
- **Node.js 22:** `canvas@2.x` does not have prebuilt binaries for Node.js 22 ABI 127. If you run `yarn test` on Node.js 22 and encounter canvas-related errors, add the following to your root `package.json` resolutions:

```json
"resolutions": {
    "canvas": "^3.2.1"
}
```

`canvas@3.x` uses the Node-API (NAPI v7) ABI-stable interface and works across Node.js 18, 20, and 22. Node.js 22 satisfies the `canvas@3.x` engine requirement (`^18.12.0 || >= 20.9.0`) natively — no `--ignore-engines` flag is needed.

## SDK package changes

The following changes are specific to the core SDK packages (`@msdyn365-commerce/bootloader`, `@msdyn365-commerce/build-scripts-internal`, `@msdyn365-commerce/theming-internal`, and related packages).

### Node.js version gate — Node.js 22 is now allowed

The bootloader previously hard-blocked Node.js 21 and later at startup. This restriction has been removed. The updated version gate behavior is:

| Node.js version | Behavior |
|---|---|
| < 16.x | Hard exit with error |
| >= 16.x (including 22.x) | Allowed |

If you are running Node.js 22, you will no longer see the following error at dev server startup:

```
Error: Current Node.js version of your development environment is X.X.X.
Please install Node.js version >=16.x which is the supported version for development!!
```

### Security fix — picomatch updated to 4.0.4

The `picomatch` package (a transitive dependency introduced via `sass` → `@parcel/watcher`) has been pinned to `4.0.4` to address CVE-2026-33671, a High severity ReDoS (Regular Expression Denial of Service) vulnerability in `picomatch@4.0.3`.

This fix is applied via a root `package.json` resolution and requires no action from customers. After upgrading, run `yarn install` to pick up the updated lockfile.

### @parcel/watcher entries in yarn.lock

After upgrading, you may notice a cluster of new entries in your `yarn.lock`:

```
@parcel/watcher-win32-x64@2.x.x
@parcel/watcher-darwin-arm64@2.x.x
@parcel/watcher-linux-x64-glibc@2.x.x
...
```

These are **transitive dependencies of `sass`** (Dart Sass uses `@parcel/watcher` for file watching in watch mode). One optional platform-specific binary is listed per OS/architecture combination, but only the binary matching your current OS is actually installed at runtime. This is a standard cross-platform distribution pattern and has no impact on build output or performance.

### ICU currency formatting differences between Node.js 16 and Node.js 22

Node.js 22 ships with a newer version of the ICU (International Components for Unicode) library. If you have Jest snapshot tests that capture `Intl.NumberFormat` currency output (for example, SAR in Arabic locale or COP in certain locale fallbacks), those snapshots may differ between Node.js 16 and Node.js 22.

Known differences:

| Locale | Node.js 16 output | Node.js 22 output |
|--------|------------------|------------------|
| SAR (`ar-SA`) | `"٣٤٫٠٠ ر.س.\u200F"` | `"\u200F٣٤٫٠٠ ر.س.\u200F"` (leading RTL mark added) |
| COP (`hi` locale fallback) | `"COP 34.00"` | `"COP 34"` (trailing `.00` dropped for whole numbers) |

**Fix:** Replace `toMatchSnapshot()` for these cases with version-tolerant assertions:

```typescript
// SAR — works on both Node.js 16 and 22
const result = formatter.formatCurrency('34', 'sar');
expect(result).toContain('٣٤');
expect(result).toContain('ر.س');

// COP — works on both Node.js 16 and 22
const result = formatter.formatCurrency('34', 'cop');
expect(result).toContain('COP');
expect(result).toMatch(/34/);
```

### Relative url() paths in compiled CSS may change depth

Dart Sass resolves relative `url()` paths differently from LibSass (node-sass). LibSass calculated the relative path based on the **source file** location. Dart Sass calculates it based on the **output file** location.

This means compiled CSS that contains `url()` references to assets (fonts, images) may have a different number of `../` segments than before. The referenced file is the same — only the relative path depth changes.

**Example:**

```css
/* Before (node-sass / LibSass) */
src: url(../../../msdyn365-assets/webfonts/fa-regular-400.woff2) format('woff2');

/* After (Dart Sass) */
src: url(../../../../../msdyn365-assets/webfonts/fa-regular-400.woff2) format('woff2');
```

**Impact:** If you have custom SCSS files that use relative `url()` paths to reference local assets (fonts, images, SVGs), verify that those assets still resolve correctly after upgrading. Using absolute paths or CSS custom properties for asset references avoids this issue entirely.

### sourceComments option removed from Sass render calls

The `sourceComments` option (which injected `/* line X, file Y */` comments into debug CSS output) has been removed from all internal Sass render calls. This option does not exist in Dart Sass's `LegacyOptions` API.

Source map debugging continues to work via `sourceMap: true` and `sourceMapContents: true`, which are unchanged. This has no impact on production CSS output.

---

## Troubleshooting

### Error: `Node Sass does not yet support your current environment`

**Symptom:**
```
Node Sass does not yet support your current environment: Unsupported runtime (127)
```

**Cause:** A package in your dependency tree is pulling in the native `node-sass` binary, which does not have a prebuilt binary for Node.js 22 (ABI 127).

**Fix:** Add the following to the `resolutions` section of your root `package.json`:

```json
"resolutions": {
    "node-sass": "npm:sass@^1.77.0"
}
```

Then run `yarn install`.

---

### Error: `Top-level selectors may not contain the parent selector "&"`

**Symptom:**
```
Error: Top-level selectors may not contain the parent selector "&".
```

**Cause:** Your SCSS (or a theme you extend) uses `&` as a top-level selector inside a `@media` block. Dart Sass enforces strict CSS selector rules.

**Fix:** Remove the `&` prefix from the selector inside the `@media` block. See [Invalid parent selector `&` at `@media` top level](#invalid-parent-selector--at-media-top-level).

---

### Error: `Expected "n"` in SCSS

**Symptom:**
```
Error: Expected "n".
```

**Cause:** An empty `:nth-last-child()` or `:nth-child()` with no argument. Dart Sass enforces the CSS `An+B` syntax.

**Fix:** Replace with `:last-child` or a valid `An+B` expression. See [Empty pseudo-class argument](#empty-pseudo-class-argument).

---

### Error: `canvas@X.X.X: The engine "node" is incompatible`

**Symptom:**
```
error canvas@3.x.x: The engine "node" is incompatible with this module. Expected version "^18.12.0 || >= 20.9.0". Got "16.x.x"
```

**Cause:** `canvas@3.x` enforces an engine requirement that excludes Node.js 16. This happens if `canvas@3.x` is resolved in your project while running Node.js 16, and your `yarn install` does not use `--ignore-engines`.

**Fix:** The SDK ships with `canvas@2.x` for Node.js 16 compatibility. If you see this error, verify your `package.json` resolutions are not overriding canvas to `^3.x`. If you want to use `canvas@3.x` (for Node.js 22 test support), add `ignore-engines true` to your `.yarnrc` file.

---

### yarn install fails with engine incompatibility errors

**Symptom:** `yarn install` fails repeatedly with engine incompatibility errors.

**Cause:** Usually caused by an incompatible engine requirement (such as `canvas@3.x` on Node.js 16) or an unresolved `node-sass` native binary.

**Fix:**
1. Check the error output for the specific package and error message.
2. Add the appropriate resolution to your root `package.json` (see above).
3. Run `yarn install` again.

## Additional resources

- [SDK and module library updates](sdk-updates.md)
- [Set up a development environment](setup-dev-environment.md)
- [Sass migration guide](https://sass-lang.com/documentation/breaking-changes/)
- [node-canvas releases](https://github.com/Automattic/node-canvas/releases)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
