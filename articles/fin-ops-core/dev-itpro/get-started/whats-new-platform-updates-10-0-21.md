---
title: Platform updates for version 10.0.21 of finance and operations apps (October 2021)
description: Learn about the features that are included in the platform updates for version 10.0.21 of finance and operations apps.
author: sericks007
ms.author: sericks
ms.topic: whats-new
ms.date: 07/12/2024
ms.custom: 
  - bap-template
  - evergreen
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2021-05-31
ms.dyn365.ops.version: 10.0.21
---

# Platform updates for version 10.0.21 of finance and operations apps (October 2021)

[!include [banner](../includes/banner.md)]

This article lists the features that are included in the platform updates for version 10.0.21 of finance and operations apps. This version has a build number of 7.0.6129 and is available on the following schedule:

- **Preview of release:** August 2021
- **General availability of release (self-update):** September 2021
- **General availability of release (auto-update):** October 2021

## Features included in this release

The following features are included in this release. Some of the listed features are still in preview, while others may already be generally available. See the [release plan](/dynamics365-release-plan/2021wave2/finance-operations/finance-operations-crossapp-capabilities/planned-features) for official release dates for each feature.

Some features must be enabled by using [Feature management](../../fin-ops/get-started/feature-management/feature-management-overview.md) before you can use them.

| Feature area   | Feature                                                  | More information                                                                    |
|----------------|----------------------------------------------------------|-------------------------------------------------------------------------------------|
| Client features | [Improved legal entity support for saved views](/dynamics365-release-plan/2021wave2/finance-operations/finance-operations-crossapp-capabilities/improved-legal-entity-support-saved-views)  | [Saved views](../../fin-ops/get-started/saved-views.md) |
| Client features | [Updates to client feature states](/dynamics365-release-plan/2021wave2/finance-operations/finance-operations-crossapp-capabilities/updates-client-feature-states-version-10021) | Not applicable |
| System administration | [Enhanced support for full feature lifecycle in Feature management](/dynamics365-release-plan/2021wave2/finance-operations/finance-operations-crossapp-capabilities/enhanced-support-full-feature-lifecycle-feature-management)| [Feature management overview](../../fin-ops/get-started/feature-management/feature-management-overview.md) |
| Availability monitoring | [Synthetic monitoring of Service Fabric environments](/dynamics365-release-plan/2021wave2/finance-operations/finance-operations-crossapp-capabilities/synthetic-monitoring-service-fabric-environments) | Not applicable | 
| Developer tools | Visual Studio 2019 is now officially supported. | [Development tools in Visual Studio](../dev-tools/development-tools-overview.md) |

## Features turned on by default in this release

The following table lists the features that are turned on by default in 10.0.21. Most features that have been turned on atomically can be turned off in [Feature management](../../fin-ops/get-started/feature-management/feature-management-overview.md).

| Feature name | Enable date | Feature added | Feature state | Module |
| :--- | :--- | :--- | :--- | :--- |
| Enable usage of EPPlus library in Electronic reporting framework | 9/1/2021 | 1/6/2020 | On by default | Organization administration |
| Convert Electronic Reporting outbound documents from Microsoft Office formats to PDF | 9/1/2021 | 1/6/2020 | On by default | Organization administration |
| Office-like UI experience for Business document management | 9/1/2021 | 11/11/2019 | On by default | Organization administration |
| Business document management | 9/1/2021 | 6/3/2019 | On by default | Organization administration |
| Saved views | 9/1/2021 | 6/9/2019 | On by default | System administration |
| New grid control | 9/1/2021 | 10/7/2019 | On by default | System administration |
| Grouping in grids | 9/1/2021 | 12/19/2019 | On by default | System administration |
| Email distributor batch job email expiration | 9/1/2021 | 2/19/2020 | On by default | System administration |
| Designate fields as required using personalization | 9/1/2021 | 4/1/2020 | On by default | System administration |
| Show related document attachments | 9/1/2021 | 4/24/2020 | Mandatory | System administration |
| Report PDF viewer | 9/1/2021 | 4/24/2020 | On by default | System administration |
| Enable Export on Report PDF viewer | 9/1/2021 | 6/14/2020 | On by default | System administration |
| Enable Network Printing on Report PDF viewer | 9/1/2021 | 6/14/2020 | On by default | System administration |
| Key vault client caching | 9/1/2021 | 8/17/2020 | On by default | System administration |
| Allow validation of control state in task recordings | 9/1/2021 | 8/17/2020 | Mandatory | System administration |
| Enable drill through links on Report PDF viewer control. | 9/1/2021 | 8/17/2020 | On by default | System administration |
| Freezing columns in grids | 9/1/2021 | 2/20/2021 | On by default | System administration |
| New color picker control | 9/1/2021 | 9/1/2021 | On by default | System administration |
| Prevents multiple executing Workflow message processing batch jobs. | 9/1/2021 | 9/1/2021 | On by default | Workflow |
| Resets the batch affinity | 9/1/2021 | 9/1/2021 | On by default | Workflow |
| Workflow notification actions | 9/1/2021 | 8/22/2020 | On by default | Workflow |

## Additional resources

### Bug fixes

For information about the bug fixes that are included in this update, sign in to Microsoft Dynamics Lifecycle Services (LCS), and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=605166).

### Dynamics 365: 2021 release wave 2 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out the [Dynamics 365: 2021 release wave 2 plan](/dynamics365-release-plan/2021wave2/). We've captured all the details, end to end, top to bottom, in a single document that you can use for planning.

### Removed and deprecated platform features

The [Removed or deprecated platform features](../../fin-ops/get-started/removed-deprecated-features-platform-updates.md) article describes features that have been removed, or that are planned for removal in platform updates of finance and operations apps.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature isn't in active development and might be removed in a future update.

A deprecation notice will be added in the [Removed or deprecated platform features](../../fin-ops/get-started/removed-deprecated-features-platform-updates.md) article 12 months before the removal of any feature from the product.

For breaking changes that affect only compilation time, but that are binary-compatible with sandbox and production environments, the deprecation time will be less than 12 months. Typically, these changes are functional updates that must be made to the compiler.

