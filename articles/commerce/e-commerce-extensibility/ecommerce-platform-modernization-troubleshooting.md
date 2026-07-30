---
title: Troubleshoot the Node.js 24 upgrade
description: Learn how to diagnose and fix common yarn install and yarn build failures when you upgrade the Dynamics 365 Commerce online SDK to Node.js 24.
author: mithun-microsoft
ms.date: 07/30/2026
ms.topic: troubleshooting-general
ms.search.region: Global
ms.author: mithunbobade
ms.reviewer: mirao
ms.search.validFrom: 2026-07-30
ms.custom:
  - bap-template
---

# Troubleshoot the Node.js 24 upgrade

[!include [banner](../includes/banner.md)]

This article helps you diagnose and fix common `yarn install` and `yarn build` failures that you might encounter when you upgrade the Microsoft Dynamics 365 Commerce online SDK environment to **Node.js 24**. It complements the step-by-step guidance in [E-commerce platform modernization](ecommerce-platform-modernization.md).

## Before you start

Before you troubleshoot, confirm the following baseline requirements are in place:

- Your local Node.js version is **22.x** or **24.x**. Use `node -v` to verify. Node.js 24 is recommended.
- You're on the Dynamics 365 Commerce online SDK package for release **10.0.49** or later. See [SDK and module library updates](sdk-updates.md).
- Your `package.json` `engines.node` field is `">=22"` (or absent). Older floors such as `">=16"` no longer match a supported runtime.

If any of these prerequisites aren't in place, address them first. Many of the following issues disappear after you meet the baseline requirements.

## Installation issues

### `yarn install` reports "Already up-to-date" but new SDK versions aren't installed

**Symptom**: After you bump SDK or SSK versions in `package.json`, `yarn install` completes in a few seconds and prints "Already up-to-date", but the new versions aren't installed and `yarn build` still fails as if nothing changed.

**Root cause**: `yarn.lock` already pins the old versions and yarn doesn't re-resolve dependencies when the lockfile is satisfied. This problem typically happens after a quick edit in `package.json` without removing the lockfile or `node_modules` cache.

**Fix**: As described in [Yarn: The `yarn.lock` file](https://classic.yarnpkg.com/lang/en/docs/yarn-lock/), yarn skips re-resolution while the lockfile already satisfies `package.json`. Following that behavior, delete `yarn.lock` and `node_modules`, and then reinstall:

```console
yarn rimraf node_modules yarn.lock
yarn install
```

If the `rimraf` command isn't available in your repo, delete the two paths manually instead, and then run `yarn install`:

```powershell
Remove-Item -Recurse -Force node_modules, yarn.lock
```

Verify that the new SDK and SSK versions are listed in both `dependencies` and `resolutions` in `package.json` before you reinstall.

## Build issues: Node.js runtime and webpack

### Build fails with `error:0308010C:digital envelope routines::unsupported`

**Symptom**: The build fails immediately on Node.js 18 or later. The error doesn't appear on Node.js 16.

```console
Error: error:0308010C:digital envelope routines::unsupported
```

**Root cause**: Webpack 5.42.0 (and earlier) calls `crypto.createHash("md4")`, which OpenSSL 3 doesn't support. Node.js 17 and later versions bundle OpenSSL 3, so this error appears as soon as you upgrade above Node.js 16.

**Fix**: As discussed in the upstream webpack issue [Error: error:0308010C:digital envelope routines::unsupported (#14532)](https://github.com/webpack/webpack/issues/14532), move to a webpack version that hashes with `xxhash64` instead of `md4`. Pin the webpack by adding the following entry to the `resolutions` block in `package.json`:

```json
"resolutions": {
  "webpack": "5.99.9"
}
```

Then, reinstall:

```console
yarn install
```

Any webpack version 5.61.0 or later resolves the underlying `md4` issue. The Dynamics 365 Commerce online SDK uses `5.99.9`.

## Build issues: `node-sass` to `sass` (dart-sass) migration

The Dynamics 365 Commerce online SDK migrated from `node-sass` to the JavaScript-based `sass` (dart-sass) implementation. `node-sass` is a deprecated, end-of-life native binding (its final release was 9.0.0 and the project was archived in 2024) and doesn't build against the Node.js 22 or 24 V8/ABI surface. After the swap, custom storefront SCSS might also need small syntax updates that dart-sass enforces but `node-sass` silently accepted.

### `node-sass: Command failed` or `gyp ERR! build error`

**Symptom**: The error appears during `yarn install` or the first build, often referencing `binding.node` or Python.

```console
gyp ERR! build error
node-sass: Command failed.
```

**Root cause**: `node-sass` is a native binding compiled against a specific Node.js version. It fails to build against Node.js 22 or 24. As described in the [node-gyp repository](https://github.com/nodejs/node-gyp), when no prebuilt binary matches your runtime, node-gyp compiles the module from source and requires Python and C++ build tools, which is the `gyp ERR!` output you see.

**Fix**: As the Sass team explains in [LibSass is deprecated](https://sass-lang.com/blog/libsass-is-deprecated/), replace the end-of-life `node-sass` binding with dart-sass. Remove `node-sass` from `package.json` and replace it with `sass`:

```json
"dependencies": {
  "sass": "^1.70.0"
},
"resolutions": {
  "node-sass": "npm:sass@^1.70.0"
}
```

The `npm:sass@^1.70.0` redirect in `resolutions` rewrites any transitive `node-sass` references to `sass`. `sass-loader` 13.x autodetects the installed implementation. You don't need any webpack configuration change.

After the swap, rebuild. If the build now fails with a dart-sass SCSS error in your custom styles, see the following dart-sass SCSS sections.

### dart-sass SCSS error 1: Empty variadic mixin argument

**Symptom**:

```console
Error: () isn't a valid CSS value.
  src/themes/.../mixins/transition.scss 7:25
```

**Root cause**: A mixin declared with a variadic argument (`$var...`) is called with no arguments. `node-sass` silently dropped the empty value; dart-sass rejects it.

**Fix**: As described in [Taking arbitrary arguments](https://sass-lang.com/documentation/at-rules/mixin/) in the Sass documentation, a variadic argument list can be empty. So, guard the body of the mixin with `@if length($var) > 0`:

```scss
@mixin transition($transition...) {
    @if length($transition) > 0 {
        -webkit-transition: $transition;
        transition: $transition;
    }
}
```

Search your custom SCSS for variadic mixins (`...`) and add the guard wherever the mixin can be called with no arguments.

### dart-sass SCSS warning 2: Division using `/` outside `calc()` (error in dart-sass 2.x)

**Symptom**:

```console
DEPRECATION WARNING [slash-div]: Using / for division outside of calc() is deprecated.
  border-width: ($tooltip-arrow-width / 2)
```

**Root cause**: dart-sass 2.x removes `/` as the division operator. In dart-sass 1.x, it's a warning, but in 2.x, it's an error.

**Fix**: As described in [Breaking change: `/` as division](https://sass-lang.com/documentation/breaking-changes/slash-div/), Sass replaces the `/` division operator with `math.div()`. Following that guidance, replace `/` division with `math.div()`, or wrap the expression in `calc()`:

```scss
@use 'sass:math';
border-width: math.div($tooltip-arrow-width, 2);
// Or
border-width: calc($tooltip-arrow-width / 2);
```

Use `math.div()` when the operands are plain SCSS numbers. Use `calc()` when CSS variables or browser-side computation is involved.

### dart-sass SCSS error 3: Parent selector `&` at the top level

**Symptom**:

```console
Error: Top-level selectors may not contain the parent selector "&".
  &.col-sm:last-child { ... }
```

**Root cause**: The `&` parent selector is only valid inside a nested rule. `node-sass` accepts it at the top level, but dart-sass doesn't.

**Fix**: As described in [The parent selector](https://sass-lang.com/documentation/style-rules/parent-selector/) in the Sass documentation, `&` is only valid inside a nested rule. Either remove the `&`, or nest the rule under its intended parent:

```scss
// Before
&.col-sm:last-child { ... }

// After - nest inside the parent rule
.parent {
    &.col-sm:last-child { ... }
}
```

### dart-sass SCSS error 4: Empty pseudo-class argument

**Symptom**:

```console
Error: Expected "n".
  src/themes/.../modules/order-details.scss 42:19
```

For example, the error points at a rule such as `&:nth-last-child() {border-bottom: none;}`.

**Root cause**: A functional pseudo-class such as `:nth-child()` or `:nth-last-child()` is called with no argument. dart-sass enforces the CSS `An+B` grammar and requires a value, so an empty argument list is a hard parse error. `node-sass` silently accepted the empty argument.

**Fix**: As the [`:nth-child()`](https://developer.mozilla.org/en-US/docs/Web/CSS/:nth-child) reference on MDN describes, the functional pseudo-class requires a valid `An+B` argument. Supply a valid argument, or use the equivalent non-functional pseudo-class:

```scss
// Before - empty argument
&:nth-last-child() { border-bottom: none; }

// After - use the equivalent pseudo-class
&:last-child { border-bottom: none; }
```

Search your custom SCSS for functional pseudo-classes called with empty parentheses (`:nth-child()`, `:nth-last-child()`, `:nth-of-type()`) and give each one a valid `An+B` argument. Or, replace it with `:first-child` or `:last-child` where that captures the intent.

### dart-sass SCSS warning 5: `@import` deprecation

**Symptom**:

```console
DEPRECATION WARNING: @import is deprecated and will be removed in Dart Sass 3.0.0.
```

**Root cause**: dart-sass is moving from `@import` to `@use` and `@forward`.

**Fix**: As the Sass team explains in [Breaking change: `@import` rules](https://sass-lang.com/documentation/breaking-changes/import/), `@import` is being replaced by the module system (`@use` and `@forward`). This warning isn't urgent; dart-sass 1.x continues to accept `@import` and the build still succeeds. Plan to migrate to `@use` and `@forward` before dart-sass 3.0.0, following the [@use rule](https://sass-lang.com/documentation/at-rules/use/) guide.

## Build issues: Other native modules

Beyond `node-sass`, the most common native module that breaks on Node.js 22 and 24 is `canvas`, which many storefronts pull in transitively through their unit test stack (`jest` and `jsdom`).

### `canvas` fails to install or load, or falls back to a source compile that needs Python

**Symptom**: During `yarn install`, `canvas` attempts a source compile that fails because it can't find Python or C++ build tools. The error appears on Node.js 22 or 24, but not on Node.js 16.

```console
Error: Cannot find module '../build/Release/canvas.node'
```

**Root cause**: `canvas@2.x` doesn't ship a prebuilt binary for the Node.js 22 or 24 ABI, so it falls back to compiling from source, which requires Python and native build tools. `canvas@2.x` also doesn't use the Node-API (N-API) ABI-stable interface. So, a binary built for one Node.js major version doesn't load on another.

**Fix**: As the [node-canvas changelog](https://github.com/Automattic/node-canvas/blob/master/CHANGELOG.md) documents, version 3.0.0 switched to a prebuilt, ABI-stable Node-API binary that works across Node.js 18, 20, 22, and 24 with no recompilation. Upgrade `canvas` to 3.x by adding the entry to the `resolutions` block in `package.json`:

```json
"resolutions": {
  "canvas": "^3.2.1"
}
```

Then, reinstall:

```console
yarn install
```

`canvas` is typically a test-only dependency (jest/jsdom) and isn't used in server-rendered pages or build output. So, this change is safe for the build. For the full project, see the [node-canvas repository](https://github.com/Automattic/node-canvas).

> [!NOTE]
> `canvas@3.x` requires Node.js `^18.12.0 || >=20.9.0` and doesn't support Node.js 16. It's compatible with the Node.js 22 or 24 baseline that this troubleshooting guide uses. You only need to set the `canvas` version to `^2.9.0` in an environment that still runs Node.js 16 (for example, a build agent that isn't upgraded yet).

## Build issues: TypeScript type definition cascades

### Errors in `node_modules/@types/node/*.d.ts` or `node_modules/undici-types/*.d.ts`

**Symptom**: The following errors appear during `yarn build`.

```console
node_modules/@types/node/https.d.ts (129, 52): ',' expected.
node_modules/undici-types/dispatcher.d.ts (215, 5): Property or signature expected.
node_modules/undici-types/client.d.ts (23, 12): ';' expected.
```

**Root cause**: Recent `@types/node` versions (newer than the `18.11.9` pin) bundle `undici-types` as a transitive dependency. `undici-types` uses the TypeScript `override` keyword in class methods, which requires **TypeScript 4.3** or later versions. The Dynamics 365 Commerce online SDK pins TypeScript to **4.2.4**, so the newer type definitions don't parse.

**Fix**: As the [TypeScript 4.3 release notes](https://www.typescriptlang.org/docs/handbook/release-notes/typescript-4-3.html) describe, the `override` keyword that these newer type definitions rely on was introduced in TypeScript 4.3. Because the SDK stays on TypeScript 4.2.4, pin `@types/node` to a version that doesn't pull `undici-types`. Add the entry to either `devDependencies` or `resolutions` in `package.json`:

```json
"devDependencies": {
  "@types/node": "18.11.9"
}
```

Or, if a transitive dependency pulls a newer `@types/node`, you can force the override:

```json
"resolutions": {
  "@types/node": "18.11.9"
}
```

The Dynamics 365 Commerce online SDK uses the `devDependencies` form by default. Use the `resolutions` form when a transitive dependency (for example, a newer testcafe version) brings in a newer `@types/node` that you need to override.

`@types/node@18.11.9` doesn't pull in `undici-types`. It remains compatible with the Node.js 22 and 24 runtimes because `@types/node` is a compile-time-only package. Node.js 22 and 24 are backward compatible with the Node.js 18 standard library API surface.

> [!NOTE]
> If your code uses a Node.js 22-specific or 24-specific API that isn't declared in `@types/node@18.11.9`, TypeScript flags it as unknown but the code still runs at runtime. Add a narrow `// @ts-ignore` or a custom type declaration if you need that API.

### Errors in `node_modules/@types/lodash/*.d.ts`

**Symptom**:

```console
node_modules/@types/lodash/common/common.d.ts (266, 65): '?' expected.
node_modules/@types/lodash/common/object.d.ts (1026, 46): '?' expected.
```

**Root cause**: Newer versions of `@types/lodash` (4.17.x and later) use TypeScript syntax that requires TypeScript 4.3 or later. The Dynamics 365 Commerce online SDK pins TypeScript to **4.2.4**.

**Fix**: The `@types/*` packages are maintained in the community [DefinitelyTyped repository](https://github.com/DefinitelyTyped/DefinitelyTyped), where you can review the version history. Pin `@types/lodash` to a version that's compatible with TypeScript 4.2.4 by adding the following entry to the `resolutions` block in `package.json`:

```json
"resolutions": {
  "@types/lodash": "4.14.191"
}
```

### General pattern: A transitive `@types/*` package uses syntax that TypeScript 4.2.4 can't parse

If you see TypeScript parser errors (`',' expected`, `';' expected`, `'?' expected`, `Property or signature expected`) in any file under `node_modules/@types/`, the root cause is the same - A transitive type definition that requires a newer TypeScript compiler than the SDK is pinned to.

**Fix**:

1. Identify the offending `@types/*` package from the error path.
1. Find the latest version that's compatible with TypeScript 4.2.4. Versions published before mid-2023 are usually compatible.
1. Add a pin to the `resolutions` block in `package.json`.
1. Reinstall: `yarn install`.

## Test failures introduced by Node.js 24

Most test failures after the Node.js 24 upgrade are pre-existing race conditions that older Node.js versions happen to hide. Node.js 24 ships V8 13.x, which schedules microtasks differently than earlier versions. Patterns that depend on a specific microtask ordering can fail under Node.js 24 even if you don't change any test or application code. For the list of engine changes in this release, see the [Node.js 24 release announcement](https://nodejs.org/en/blog/release/v24.0.0).

### Test fails with `Unhandled promise rejection: Cannot read properties of undefined`

**Symptom**: A test that passes on Node.js 16, 18, 20, or 22 fails on Node.js 24 with an unhandled promise rejection. The stack trace points to a `.map(async ...)` callback that inspects a logger's recorded requests. For example:

```console
   Unhandled promise rejection:
   TypeError: Cannot read properties of undefined (reading 'statusCode')
   at test/page-tests.ts:X
```

**Root cause**: The test uses the pattern `Logger?.requests.map(async r => ...)` without waiting for the resulting array of promises. On older Node.js versions, the microtask scheduler populated the response data before the unawaited callbacks ran. Node.js 24 schedules microtasks differently, so the orphan callbacks now run while some responses are still pending. The unawaited `.map` produces an array of promises that the test never awaits. So, any rejection becomes an unhandled promise rejection instead of a regular test failure.

**Fix**: As the MDN [`Promise.all()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise/all) reference describes, awaiting an array of promises surfaces rejection instead of letting it escape. Await the `.map` result with `Promise.all`, and explicitly wait for the response before asserting on it. Replace this pattern:

```typescript
SomeLogger?.requests.map(async r => {
    if (r.request.url.includes('expected-url')) {
        await testController.expect(r.response.statusCode).eql(200, 'message');
    }
});
```

with the following pattern:

```typescript
// Wait for at least one matching response to be logged, so we don't race the logger.
await testController.expect(SomeLogger.contains(r =>
    r.request.url.includes('expected-url') && r.response != null
)).ok('No completed matching requests recorded');

// Assert every matching request returned 200.
await Promise.all((SomeLogger?.requests || [])
    .filter(r => r.request.url.includes('expected-url'))
    .map(async r => {
        await testController.expect(r.response).ok(
            `Request missing response: ${r.request.url}`);
        await testController.expect(r.response.statusCode).eql(200, 'message');
    }));
```

This new pattern waits for at least one response to be recorded using `RequestLogger.contains()`. Then, it asserts that every matching request received the expected status. Any pending response or non-200 status produces a visible failure instead of an unhandled rejection.

The same fix applies to any `Logger?.requests.map(async ...)` or `array.map(async ...)` pattern that the surrounding code doesn't await.

## Migration checklist

Use the following checklist when you upgrade a storefront to Node.js 24:

- **`package.json` changes**:

  - Remove `node-sass` from `dependencies`.
  - Add `"sass": "^1.70.0"` to `dependencies`.
  - Add `"node-sass": "npm:sass@^1.70.0"` to `resolutions`. It redirects transitive `node-sass` references.
  - Add `"webpack": "5.99.9"` to `resolutions`. You need this change when you run on Node.js 18 or later.
  - If TypeScript compilation fails on `@types/node` or `undici-types`, add `"@types/node": "18.11.9"` to `devDependencies`. Or, add it to `resolutions` if a transitive dependency forces a newer version.
  - If TypeScript compilation fails on `@types/lodash`, add `"@types/lodash": "4.14.191"` to `resolutions`.
  - If your unit tests pull in `canvas` (through `jest` or `jsdom`), add `"canvas": "^3.2.1"` to `resolutions`.
  - Set `engines.node` to `">=22"`. Or, remove the field.

- **Custom SCSS changes**:

  - Search for variadic mixins (`$var...`) and add `@if length($var) > 0` guards where the mixin can be called with no arguments.
  - Search for `/` division in SCSS and replace with `math.div()` or `calc()`.
  - Search for top-level `&` parent selectors and nest them under their intended parent rule.
  - Search for functional pseudo-classes called with empty parentheses (such as `:nth-child()` or `:nth-last-child()`) and give each of them a valid argument. Or, use `:first-child` or `:last-child`.
  - (Optional) Begin planning the `@import` to `@use` and `@forward` migration before dart-sass 3.0.0.

- **Verification**:

  - Run `yarn rimraf node_modules yarn.lock`, and then `yarn install`. The install succeeds without `node-sass` or peer-dependency errors.
  - Run `yarn build`. The build succeeds with exit code 0.
  - Run your test suite. If any tests fail with `Unhandled promise rejection`, fix the unawaited `.map(async ...)` patterns as explained in [Test failures introduced by Node.js 24](#test-failures-introduced-by-nodejs-24).

## More resources

- [E-commerce platform modernization](ecommerce-platform-modernization.md)
- [Set up a development environment](setup-dev-environment.md)
- [SDK and module library updates](sdk-updates.md)
- [Dynamics 365 Commerce online SDK FAQ](sdk-faq.md)
- [System requirements for a Dynamics 365 Commerce online extensibility development environment](system-requirements.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
