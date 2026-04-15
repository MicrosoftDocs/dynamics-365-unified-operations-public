---
title: eCommerce Platform Modernization
description: Learn about the platform modernization efforts for the Dynamics 365 Commerce online SDK, including Node.js runtime upgrades and the deprecation timeline for Node.js 16.
author: mithunbobade
ms.date: 04/15/2026
ms.topic: overview
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: mithunbobade
ms.search.validFrom: 2026-04-15
ms.custom:
  - bap-template
---
# eCommerce Platform Modernization

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

For the full Commerce release schedule, see [Dynamics 365 Finance, Supply Chain Management, and Commerce public preview releases](https://learn.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/get-started/public-preview-releases).

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

## Additional resources

- [Set up a development environment](setup-dev-environment.md)
- [SDK and module library updates](sdk-updates.md)
- [System requirements for a Dynamics 365 Commerce online extensibility development environment](system-requirements.md)
- [Dynamics 365 Commerce public preview release schedule](https://learn.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/get-started/public-preview-releases)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
