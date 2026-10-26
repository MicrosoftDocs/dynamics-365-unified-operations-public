---
title: Platform updates for version 10.0.50 of finance and operations apps (October 2026)
description: This article lists the features and enhancements that are included in the platform updates for version 10.0.50 of finance and operations apps.
author: johnmichalak
ms.author: johnmichalak
ms.reviewer: johnmichalak
ms.date: 10/26/2026
ms.update-cycle: 1095-days
ms.topic: whats-new
ms.custom:
  - bap-template
  - evergreen
ms.search.region: Global
---

# Platform updates for version 10.0.50 of finance and operations apps (October 2026)

[!INCLUDE [banner](../includes/banner.md)]

This article lists the features in the platform updates for version 10.0.50 of finance and operations apps. This version uses build number 10.0.2919 and is available on the following schedule:

- **Preview of release:** October 2026
- **General availability of release (self-update):** December 2026
- **General availability of release (auto-update):** January 2027

## Features included in this release

This section lists the features included in this release when available. The article might be updated to add features that are added to the build after it's published.

| Module or feature area | Feature name | More information | Enabled by |
| --- | --- | --- | --- |
| Nothing at this time |  |  |  |

## Feature enhancements included in this release

This section contains a table that lists enhancements included in this release when available. The article might be updated to include features added to the build after it's published.

| Module or feature area | Feature name | More information | Enabled by |
| --- | --- | --- | --- |
| Developer tools | X++ | The **client** and **server** keyword warnings are now compilation errors. | &nbsp; |
| Developer tools | X++ | Added best practice rule `BPErrorAggregateFieldInUpdateRecordsetSetting` for update_recordset to detect unsupported aggregate expressions | &nbsp; |
| Developer tools | X++ | Added compiler validation `IndexCannotContainVirtualField` to ensure an index can't contain a field with `SaveContents` set to `No` | &nbsp; |
| Developer tools | X++ | Added compiler validation `FormControlNotFound` for `Target Control` property. | &nbsp; |

### Bug fixes

To see bug fixes in this update, sign in to Microsoft Dynamics Lifecycle Services and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=1198101).

### Removed and deprecated platform features

The [Removed or deprecated platform features](../../fin-ops/get-started/removed-deprecated-features-platform-updates.md) article describes features that are removed or planned for removal in platform updates for finance and operations apps.

- A *removed* feature isn't available in the product.
- A *deprecated* feature isn't in active development and might be removed in a future update.

Deprecation notices appear in the [Removed or deprecated platform features](../../fin-ops/get-started/removed-deprecated-features-platform-updates.md) article 12 months before any feature is removed.

For breaking changes that affect only compilation time but are binary-compatible with sandbox and production environments, the deprecation time is less than 12 months. These changes are functional updates that you must make to the compiler.
