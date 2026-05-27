---
title: E-commerce platform modernization
description: Learn about platform modernization efforts for the Dynamics 365 Commerce online SDK, including Node.js runtime upgrades and TypeScript upgrades.
author: mithun-microsoft
ms.date: 05/27/2026
ms.topic: overview
ms.search.region: Global
ms.author: mithunbobade
ms.reviewer: mirao
ms.search.validFrom: 2026-05-27
ms.custom:
  - bap-template
---

# E-commerce platform modernization

[!include [banner](../includes/banner.md)]

This article describes ongoing platform modernization efforts for the Microsoft Dynamics 365 Commerce eCommerce online SDK. These improvements help ensure the SDK remains secure, performant, and aligned with the latest industry standards.

## Node.js runtime upgrade

The Dynamics 365 Commerce online SDK is moving to **Node.js 22** as the only supported runtime starting with the SDK package for Dynamics 365 Commerce release 10.0.49 (scheduled for July 27, 2026). Node.js 22 delivers significant security improvements, an updated V8 engine, and long-term support (LTS) coverage through April 2027.

### Supported Node.js versions

| Node.js version | Support status |
| --------------- | -------------- |
| Node.js 16.x | Supported on SDK packages earlier than the Dynamics 365 Commerce 10.0.49 release |
| Node.js 22.x | Supported; required on the SDK package for Dynamics 365 Commerce release 10.0.49 and later |

> [!IMPORTANT]
> The Node.js 22 requirement applies only when you upgrade to the SDK package for Dynamics 365 Commerce release 10.0.49 (scheduled for July 27, 2026) or later. If you remain on an earlier SDK package, you can continue to use Node.js 16. To upgrade your SDK to the 10.0.49 release or later, you must move your development environment to **Node.js 22**.

For the full Commerce release schedule, see [Dynamics 365 Finance, Supply Chain Management, and Commerce public preview releases](/dynamics365/fin-ops-core/dev-itpro/get-started/public-preview-releases).

### Why upgrade?

Node.js 16, 18, and 20 have all reached end of life and no longer receive active security patches from the Node.js project. The SDK package for Dynamics 365 Commerce release 10.0.49 and later supports Node.js 22 only. Upgrading to Node.js 22 provides:

- Active security updates
- Improved performance through the updated V8 engine
- Compatibility with the latest SDK dependencies
- Ability to consume the SDK package for release 10.0.49 and later

### What you need to do

If you plan to upgrade your SDK to the package for Dynamics 365 Commerce release 10.0.49 or later, complete the following steps to move your development environment to Node.js 22:

1. **Upgrade Node.js**: Install Node.js 22 in your development environment.

   For installation steps, see [Set up a development environment](setup-dev-environment.md).

   > [!TIP]
   > If you manage multiple Node.js versions across projects, use [Node Version Manager (nvm)](https://github.com/nvm-sh/nvm) to switch between Node.js versions without affecting your other projects.

1. **Reinstall dependencies**: After you upgrade Node.js, run `yarn install` from the root of your SDK repository to apply the compatible dependency set for your new runtime.

   ```console
   yarn install
   ```

1. **Validate your environment**: Start the local development server and verify that your modules, themes, and data actions build and run as expected.

   ```console
   yarn start
   ```

## TypeScript upgrade

Starting with online SDK package version 9.55 (SDK bootloader version 1.55), the Dynamics 365 Commerce online SDK upgraded its TypeScript compiler from **TypeScript 3.x** to **TypeScript 4.2.4**. This upgrade brings improved type checking, better editor tooling support, and access to modern TypeScript language features.

### Supported TypeScript version

| TypeScript version | Support status |
| ------------------ | -------------- |
| TypeScript 3.x | No longer supported |
| TypeScript 4.2.4 | Supported (current) |

> [!NOTE]
> The SDK's `package.json` resolutions pin the TypeScript version to **4.2.4**. After you upgrade to SDK package version 9.55 or later, running `yarn install` automatically resolves the correct TypeScript version.

### What you need to do

If you're upgrading from an SDK version earlier than 9.55, complete the following steps:

1. **Update your SDK package**: Upgrade to SDK package version 9.55 or later. For the instructions, see [SDK and module library updates](sdk-updates.md).

1. **Reinstall dependencies**: Run `yarn install` from the root of your SDK repository to pick up the updated TypeScript compiler.

   ```console
   yarn install
   ```

1. **Build and fix type errors**: Run `yarn build` and resolve any new TypeScript compilation errors. TypeScript 4.x introduces stricter type checking compared to TypeScript 3.x.

   ```console
   yarn build
   ```

For a full list of changes between TypeScript versions 3.x and 4.x, see the [TypeScript release notes](https://www.typescriptlang.org/docs/handbook/release-notes/overview.html).

## More resources

- [Set up a development environment](setup-dev-environment.md)
- [SDK and module library updates](sdk-updates.md)
- [System requirements for a Dynamics 365 Commerce online extensibility development environment](system-requirements.md)
- [Dynamics 365 Commerce public preview release schedule](/dynamics365/fin-ops-core/dev-itpro/get-started/public-preview-releases)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
