---
# required metadata

title: What's new or changed in Finance and Operations version 10.0.1 (April 2019)
description: This topic describes features that are either new or changed in Dynamics 365 for Finance and Operations version 10.0.1. This version will be released in April.
author: tonyafehr
manager: AnnBe
ms.date: 04/05/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: tfehr
ms.search.scope:  Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: a362a31d-44df-45c5-b698-64c5264c592e
ms.search.region: Global
# ms.search.industry: 
ms.author: tfehr
ms.search.validFrom:  
ms.dyn365.ops.version: Release 10.0.1

---
# What's new or changed in Finance and Operations version 10.0.1 (April 2019)

[!include [banner](../includes/banner.md)]


This topic describes features that are either new or changed in Microsoft Dynamics 365 for Finance and Operations version 10.0.1. This version will be released in April and has a build number of 10.0.51. For more information about version 10.0.1, see [Additional resources](whats-new-changed-10-0-1.md#additional-resources).

To learn about the new features and changes in the latest releases of Microsoft Dynamics 365 for Retail, see [What's new or changed in Dynamics 365 for Retail version 10.0.1](https://docs.microsoft.com/dynamics365/unified-operations/retail/get-started/whats-new-10-0-1).


## Enable edit for externally maintained fields

Due to integration scenarios with external systems, such as the Prospect to cash integration, certain fields on Global address book and customer records were marked as externally maintained with the expectation that these values would be maintained in an external system. The **Enable edit for externally maintained fields** option has been added to the Global address book parameters (**Organization administration > Global address book > Global address book parameters**) with the default value of **No**.  If the user scenario requires these fields to be available for edit even though maintained externally, the value can be set to **Yes**.

## Regulatory updates
For information about the regulatory updates for Finance and Operations, see [Localization and Regulatory features – Regulatory updates](../../financials/localizations/regulatory-updates.md). Alternatively, you can sign in to Lifecycle Services (LCS) and view the planned regulatory updates using the issue search tool, where you can search by country, type of feature, and release.


## Additional resources

### Bug fixes
For information about the bug fixes included in each of the updates that are part of Finance and Operations version 10.0.1, sign in to Lifecycle Services (LCS) and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=299640&dbType=3&qc=2da6de70aab0f4c61b0f920b3242211f5043697189d50a6e1fb1ac3d27ee5f78).

### Platform update 25
Microsoft Dynamics 365 for Finance and Operations version 10.0.1 includes Platform update 25. To learn more about Platform update 25, see [What's new or changed in Finance and Operations platform update 25 (April 2019)](whats-new-platform-25.md).

### Dynamics 365 April '19 release notes
Wondering about upcoming and recently released capabilities in any of our business apps or platform?

[Check out the April '19 release notes](https://docs.microsoft.com/en-us/business-applications-release-notes/April19/index). We've captured all the details, end to end, top to bottom, in a single document that you can use for planning.

### Removed and deprecated features
The [Removed or deprecated features](../../dev-itpro/migration-upgrade/deprecated-features.md) topic describes features that have been removed or deprecated for Dynamics 365 for Finance and Operations.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature is not in active development and may be removed in a future update.

Before any feature is removed from the product, the deprecation notice will be announced in the [Removed or deprecated features](../../dev-itpro/migration-upgrade/deprecated-features.md) topic 12 months prior to the removal.

For breaking changes that only affect compilation time, but are binary compatible with sandbox and production environments, the deprecation time will be less than 12 months. Typically these are functional updates that need to made to the compiler.

