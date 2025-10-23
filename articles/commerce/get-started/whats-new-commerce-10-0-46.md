---
title: Preview features in Dynamics 365 Commerce 10.0.46 (October 2025)
description: This article describes features that are either new or changed in Microsoft Dynamics 365 Commerce 10.0.46. 
author: johnmichalak
ms.date: 10/24/2025
ms.update-cycle: 1095-days
ms.topic: whats-new
ms.custom: 
  - bap-template
  - evergreen
ms.reviewer: johnmichalak
ms.search.region: Global
ms.author: johnmichalak
ms.search.validFrom: 2023-11-01
ms.dyn365.ops.version: 10.0.46

---

# What's new or changed in Dynamics 365 Commerce 10.0.46 (October 2025)

[!include [banner](../includes/banner.md)]

This article lists features that are either new or changed in Microsoft Dynamics 365 Commerce preview version 10.0.46. This version has a build number of 10.0.2345 and is available on the following schedule:

- **Preview of release:** October 2025
- **General availability of release (self-update):** November 2025
- **General availability of release (auto-update):** December 2025

## Features included in this release

The following table lists the features that are included in this release. We might update this article to include features that were added to the build after this article was originally published.

| Feature area | Feature | More information | Enabled by |
|---|---|---|---|
| Extensibility | Generated extension SQL script | The Generated extension SQL script feature simplifies and accelerates the process of adding extensions to the channel database. It also helps optimize performance and avoid common customization errors that impact data synchronization.<br><br>In Dynamics 365 headquarters, a new Generated extension SQL script section on the **Scheduler Subjobs** page (**Retail and Commerce** \> **Headquarters setup** \> **Commerce scheduler** \> **Scheduler subjobs**) displays SQL script that you can use as a starting point to add or modify tables in the channel database for the selected subjob. Learn more in [Generated extension SQL script](../dev-itpro/channel-db-extensions.md#generated-extension-sql-script).| |
|  Unified pricing management | Enable streamlined migration to unified pricing management | This feature provides a migration script for Dynamics 365 Commerce unified pricing management that doesn't require additional configuration. | Admins |

## Features turned on by default in this release

The following table lists the features that became turned on by default in version 10.0.43. You can still disable these features in **Feature management**, if necessary.

| Module | Feature name | More information |
|--|--|--|


## Resources

### Platform updates for finance and operations apps

Microsoft Dynamics 365 Commerce version 10.0.46 includes platform updates. Learn more in [Platform updates for version 10.0.46 of finance and operations apps](../../fin-ops-core/fin-ops/get-started/whats-new-platform-updates-10-0-46.md). 
  
### Bug fixes

For information about the bug fixes included in each of the updates that are part of version 10.0.46, sign in to Microsoft Dynamics Lifecycle Services and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=NNNNN).

### Dynamics 365 and industry clouds: 2025 release wave 2 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out the [Dynamics 365 and industry clouds: 2025 release wave 2 plan](/dynamics365/release-plan/2025wave2/). We captured all the details, end to end, top to bottom, in a single document that you can use for planning.

### Removed and deprecated Commerce features

The [Removed or deprecated features in Dynamics 365 Commerce](removed-deprecated-features-commerce.md) article describes features that are removed or deprecated for Commerce.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature isn't in active development and may be removed in a future update.

Before any feature is removed from the product, the deprecation notice is announced in the [Removed or deprecated features in Dynamics 365 Commerce](removed-deprecated-features-commerce.md) article 12 months before removal.

For breaking changes that only affect compilation time, but are binary compatible with sandbox and production environments, the deprecation time is less than 12 months. Typically, these changes are functional updates that need to be made to the compiler.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
