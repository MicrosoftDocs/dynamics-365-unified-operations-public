---
# required metadata

title: Preview features in Finance and Operations version 10.0.2 (May 2019)
description: This topic describes features that are either new or changed in Dynamics 365 for Finance and Operations version 10.0.2. This version will be released in May.
author: tonyafehr
manager: AnnBe
ms.date: 05/05/2019
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
# Preview features in Finance and Operations version 10.0.2 (May 2019)

[!include [banner](../includes/banner.md)]

[!include [banner](../includes/preview-banner.md)]

This topic describes features that are either new or changed in Microsoft Dynamics 365 for Finance and Operations version 10.0.2. This version will be released in May and has a build number of BUILD#. For more information about version 10.0.2, see [Additional resources](whats-new-changed-10-0-2.md#additional-resources).

To learn about the new features and changes in the latest releases of Microsoft Dynamics 365 for Retail, see [Preview features in Dynamics 365 for Retail version 10.0.2](https://docs.microsoft.com/dynamics365/unified-operations/retail/get-started/whats-new-10-0-2.


## <Enter New Feature Name here>

<enter new feature description here>
  
## Create project-based sales orders for projects with a funding source of type "Grant"

This feature provides support for the creation of project-based sales orders for time and material projects funded by a grant on the related project contract. The customer assigned as the contact for the grant will be the customer on the sales order.

## Support for project-based sales orders for projects with multiple funding sources

This feature allows creation of sales orders for time and material projects where the related project contract has multiple funding sources. Enable this feature by selecting the **Allow sales orders for projects with multilple funding sources** option on the **General** tab in the **Project management and accounting parameters** form. The parameter will be removed and the feature will always be enabled in a future release. See [Removed or deprecated features](../../dev-itpro/migration-upgrade/deprecated-features.md) for more information.

## Regulatory updates
For information about the regulatory updates for Finance and Operations, see [Localization and Regulatory features – Regulatory updates](../../financials/localizations/regulatory-updates.md). Alternatively, you can sign in to Lifecycle Services (LCS) and view the planned regulatory updates using the issue search tool, where you can search by country, type of feature, and release.


## Additional resources

### Bug fixes
For information about the bug fixes included in each of the updates that are part of Finance and Operations version 10.0, sign in to Lifecycle Services (LCS) and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=299640&dbType=3&qc=2da6de70aab0f4c61b0f920b3242211f5043697189d50a6e1fb1ac3d27ee5f78).

### Platform update 25
Microsoft Dynamics 365 for Finance and Operations version 10.0.1 includes Platform update 25. To learn more about Platform update 25, see [Preview features in Finance and Operations platform update 25 (April 2019)](whats-new-platform-25.md).

### Dynamics 365 April '19 release notes
Wondering about upcoming and recently released capabilities in any of our business apps or platform?

[Check out the April '19 release notes](https://docs.microsoft.com/en-us/business-applications-release-notes/April19/index). We've captured all the details, end to end, top to bottom, in a single document that you can use for planning.

### Removed and deprecated features
The [Removed or deprecated features](../../dev-itpro/migration-upgrade/deprecated-features.md) topic describes features that have been removed or deprecated for Dynamics 365 for Finance and Operations.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature is not in active development and may be removed in a future update.

Before any feature is removed from the product, the deprecation notice will be announced in the [Removed or deprecated features](../../dev-itpro/migration-upgrade/deprecated-features.md) topic 12 months prior to the removal.

For breaking changes that only affect compilation time, but are binary compatible with sandbox and production environments, the deprecation time will be less than 12 months. Typically these are functional updates that need to made to the compiler.
