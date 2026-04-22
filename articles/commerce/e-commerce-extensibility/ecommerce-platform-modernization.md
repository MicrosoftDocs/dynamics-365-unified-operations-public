---
title: E-commerce platform modernization
description: Learn about platform modernization efforts for the Dynamics 365 Commerce online SDK, including Node.js runtime upgrades, TypeScript upgrades, and the deprecation timeline for Node.js 16.
author: mithun-microsoft
ms.date: 04/15/2026
ms.topic: overview
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: mithunbobade
ms.search.validFrom: 2026-04-15
ms.custom:
  - bap-template
---
# E-commerce platform modernization

[!include [banner](../includes/banner.md)]

This article describes ongoing platform modernization efforts for the Microsoft Dynamics 365 Commerce eCommerce online SDK. These improvements help ensure the SDK remains secure, performant, and aligned with the latest industry standards.

## Node.js runtime upgrade

The Dynamics 365 Commerce online SDK now supports **Node.js 22**. Node.js 22 delivers significant security improvements, an updated V8 engine, and long-term support (LTS) coverage through April 2027.

### Supported Node.js versions

| Node.js version | Support status |
|-----------------|----------------|
| Node.js 16.x | Supported — deprecation planned (see below) |
| Node.js 18.x | Supported — not recommended (reached end of life April 30, 2025) |
| Node.js 20.x | Supported — not recommended (reaches end of life April 30, 2026) |
| Node.js 22.x | Supported (recommended) |

> [!IMPORTANT]
> **Node.js 16 support will be dropped in Dynamics 365 Commerce release 10.0.49 (scheduled for July 27, 2026).** After this release, Node.js 16 will no longer be a supported runtime for eCommerce SDK development. We strongly recommend upgrading your development environments to **Node.js 22** before this date.

> [!NOTE]
> Node.js 18 reached end of life on April 30, 2025, and Node.js 20 reaches end of life on April 30, 2026. If you are on either of these versions, we recommend upgrading to **Node.js 22**.

For the full Commerce release schedule, see [Dynamics 365 Finance, Supply Chain Management, and Commerce public preview releases](/dynamics365/fin-ops-core/dev-itpro/get-started/public-preview-releases).

### Why upgrade?

Node.js 16 reached end of life on September 11, 2023, Node.js 18 on April 30, 2025, and Node.js 20 reaches end of life on April 30, 2026. None of these versions receive active security patches. Upgrading to Node.js 22 provides:

- Active security updates.
- Improved performance through the updated V8 engine.
- Compatibility with the latest SDK dependencies.

### What you need to do

To prepare for Node.js 16 deprecation, complete the following steps before the 10.0.49 release:

1. **Upgrade Node.js** — install Node.js 22 on your development environment.

   For installation steps, see [Set up a development environment](setup-dev-environment.md).

   > [!TIP]
   > If you manage multiple Node.js versions across projects, use [Node Version Manager (nvm)](https://github.com/nvm-sh/nvm) to switch between Node.js versions without affecting your other projects.

1. **Reinstall dependencies** — after upgrading Node.js, run `yarn install` from the root of your SDK repository to pick up the compatible dependency set for your new runtime.

   ```console
   yarn install
   ```

1. **Validate your environment** — start the local development server and verify that your modules, themes, and data actions build and run as expected.

   ```console
   yarn start
   ```

## TypeScript upgrade

Starting with online SDK package version **9.55** (SDK bootloader version 1.55), the Dynamics 365 Commerce online SDK upgraded its TypeScript compiler from **TypeScript 3.x** to **TypeScript 4.2.4**. This upgrade brings improved type checking, better editor tooling support, and access to modern TypeScript language features.

### Supported TypeScript version

| TypeScript version | Support status |
|--------------------|----------------|
| TypeScript 3.x | No longer supported |
| TypeScript 4.2.4 | Supported (current) |

> [!NOTE]
> The TypeScript version is pinned in the SDK's `package.json` resolutions to **4.2.4**. After upgrading to SDK package version 9.55 or later, the correct TypeScript version is automatically resolved when you run `yarn install`.

### What you need to do

If you're upgrading from an SDK version earlier than 9.55, complete the following steps:

1. **Update your SDK package** — upgrade to SDK package version 9.55 or later. For instructions, see [SDK and module library updates](sdk-updates.md).

1. **Reinstall dependencies** — run `yarn install` from the root of your SDK repository to pick up the updated TypeScript compiler.

   ```console
   yarn install
   ```

1. **Build and fix type errors** — run `yarn build` and resolve any new TypeScript compilation errors. TypeScript 4.x introduces stricter type checking compared to TypeScript 3.x.

   ```console
   yarn build
   ```

For a full list of changes between TypeScript 3.x and 4.x, see the [TypeScript release notes](https://www.typescriptlang.org/docs/handbook/release-notes/overview.html).

## Additional resources

- [Set up a development environment](setup-dev-environment.md)
- [SDK and module library updates](sdk-updates.md)
- [System requirements for a Dynamics 365 Commerce online extensibility development environment](system-requirements.md)
- [Dynamics 365 Commerce public preview release schedule](/dynamics365/fin-ops-core/dev-itpro/get-started/public-preview-releases)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
