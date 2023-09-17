---
title: What's new or changed in Finance and Operations version 10.0.2 (May 2019)
description: This article describes features that are either new or changed in Dynamics 365 Finance and Operations version 10.0.2. This version will be released in May.
author: sericks007
ms.date: 10/15/2019
ms.topic: article
ms.prod: 
ms.technology: 
audience: Developer, IT Pro
ms.reviewer: sericks
ms.search.region: Global
ms.author: sericks
ms.search.validFrom: 
ms.dyn365.ops.version: Release 10.0.1
ms.custom: 
ms.assetid: a362a31d-44df-45c5-b698-64c5264c592e
ROBOTS: NOINDEX, NOFOLLOW
---

# What's new or changed in Finance and Operations version 10.0.2 (May 2019)

[!include [banner](../includes/banner.md)]


This article describes features that are either new or changed in Microsoft Dynamics 365 Finance and Operations version 10.0.2. This version will be released in May and has a build number of 10.0.80. For more information about version 10.0.2, see [Additional resources](whats-new-changed-10-0-2.md#additional-resources).


To learn about the new features and changes in the latest releases of Retail, see [What's new or changed in Dynamics 365 for Retail version 10.0.2](../../../commerce/get-started/whats-new-10-0-2.md).

  
## Recovering vendor invoices that are in use

You can use the **Recover vendor invoices** page to recover or release vendor invoices that have been in use for more than four hours, so that they can be edited. You can open this page from the **Periodic task** navigation link or a tile on the **Vendor invoice entry** workspace. After an invoice is recovered, it will be available for editing on the **Vendor invoice** page.

For more information, see [Vendor invoices overview](../../../finance/accounts-payable/vendor-invoices-overview.md).
  
## Bank foreign currency revaluation

As part of a period end, some accounting practices require that bank account balances in foreign currencies be revalued by using different exchange rate types (current, historical, average, and so on). The bank foreign currency revaluation feature can be used to revalue one or more bank accounts. The is also a global feature, which means that from a single page, you can revalue banks across all the legal entities that you have access to.
  
## Create project-based sales orders for projects with a funding source of type Grant

This feature provides support for the creation of project-based sales orders for time and material projects funded by a grant on the related project contract. The customer assigned as the contact for the grant will be the customer on the sales order.

## Support for project-based sales orders for projects with multiple funding sources

This feature lets you create sales orders for time and material projects where the related project contract has multiple funding sources. Enable this feature by selecting the **Allow sales orders for projects with multiple funding sources** option on the **General** tab on the **Project management and accounting parameters** page. This parameter will be removed and the feature will always be enabled in a future release. For more information, refer to [Removed or deprecated features for finance and operations](../../dev-itpro/migration-upgrade/deprecated-features.md).

## Acceptance test library

This developer features enables you to efficiently write unit and component tests using a rich domain-specific language that contains hundreds of entities such as sales orders, customers, and items. For more information, see  [Acceptance test library resources](../../dev-itpro/perf-test/acceptance-test-library.md).  

## Regulatory updates
For information about the regulatory updates for Finance and Operations, see [Localization and Regulatory features – Regulatory updates](../../../finance/localizations/regulatory-updates.md). Alternatively, you can sign in to Lifecycle Services (LCS) and view the planned regulatory updates using the issue search tool, where you can search by country/region, type of feature, and release.

## Extensibility enhancements

In this release of Finance and Operations, numerous enhancements have been made to support extensibility. For example, extensibility enhancements have been made to enumerations, metadata, and methods. For detailed information, see [Extensibility changes in Dynamics 365 Finance and Operations version 10.0.2](../../dev-itpro/extensibility/extensibility-changes-10-2.md).

## Additional resources

### Bug fixes
For information about the bug fixes included in each of the updates that are part of Finance and Operations version 10.0.2, sign in to Lifecycle Services (LCS) and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=313841&dbType=3&qc=a4ba239cdec6f528657f529750b68845b75580e5fdb0ad6060c4bc33f8da67f8).

### Platform update 26

Microsoft Dynamics 365 Finance and Operations version 10.0.2 includes Platform update 26. To learn more about Platform update 26, see [What's new or changed in Dynamics 365 Finance and Operations platform update 26 (May 2019)](whats-new-platform-update-26.md).


### Dynamics 365 April '19 release notes
Wondering about upcoming and recently released capabilities in any of our business apps or platform?

[Check out the April '19 release notes](/business-applications-release-notes/April19/index). We've captured all the details, end to end, top to bottom, in a single document that you can use for planning.

### Removed and deprecated features
The [Removed or deprecated features for finance and operations](../../dev-itpro/migration-upgrade/deprecated-features.md) article describes features that have been removed or deprecated for Dynamics 365 Finance.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature is not in active development and may be removed in a future update.

Before any feature is removed from the product, the deprecation notice will be announced in the [Removed or deprecated features for finance and operations](../../dev-itpro/migration-upgrade/deprecated-features.md) article 12 months prior to the removal.

For breaking changes that only affect compilation time, but are binary compatible with sandbox and production environments, the deprecation time will be less than 12 months. Typically these are functional updates that need to be made to the compiler.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]

