---
title: What's new or changed in Finance and Operations version 10.0.3 (June 2019)
description: This article describes features that are either new or changed in Dynamics 365 Finance and Operations version 10.0.3. This version will be released in June.
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
ms.dyn365.ops.version: Release 10.0.3
ms.custom: 
ms.assetid: a362a31d-44df-45c5-b698-64c5264c592e
ROBOTS: NOINDEX, NOFOLLOW
---
# What's new or changed in Finance and Operations version 10.0.3 (June 2019)

[!include [banner](../includes/banner.md)]


This article describes features that are either new or changed in Microsoft Dynamics 365 Finance and Operations version 10.0.3. This version will be released in June and has a build number of 10.0.107. For more information about version 10.0.3, see [Additional resources](whats-new-changed-10-0-3.md#additional-resources).

To learn about the new features and changes in the latest releases of Retail, see [What's new or changed in Dynamics 365 for Retail version 10.0.3](../../../commerce/get-started/whats-new-10-0-3.md).

## Feature management

The **Feature management** experience provides a workspace where you can view a list of features that have been delivered in each release. By default, new features are turned off. You can use the workspace to turn them on and view the documentation for them.

For more information, see [Feature management](./feature-management/feature-management-overview.md).

## Enable Bank foreign currency revaluation without a parameter
Bank foreign currency revaluation was released in version 10.0.2 and it included a parameter in Cash and Bank parameters to enable it. You can now enable bank foreign currency revaluation for all legal entities where it is available using feature management. 

For more information, see [Bank foreign currency revaluation](../../../finance/cash-bank-management/bank-revaluation.md#bank-foreign-currency-revaluation).

## Expense reports re-imagined
Expense report entry has been redesigned to simplify and decrease the time to complete your expense report. You can enable this functionality in feature management to add a new setup form to configure expense fields visibility to determine what data is required, optional, or not enabled for entering expense reports. A new expense workspace is enabled with this feature, replacing the previous expense workspace and is the landing page for the improved entry experience. 

For more information, see [Expense reports re-imagined](/dynamics365/project-operations/prod-exp/ExpenseWorkspaceNew).

## Extensibility enhancements

In this release of Finance and Operations, numerous enhancements have been made to support extensibility. For example, extensibility enhancements have been made to enumerations, metadata, and methods. For detailed information, see [Extensibility changes in Dynamics 365 Finance and Operations version 10.0.3](../../dev-itpro/extensibility/extensibility-changes-10-3.md).

## Tax engine

> [!NOTE]
> The tax engine (GTE) is currently only available for India.

### Calculate tax in accounting currency for Import/Export Order

In this release of Finance and Operations, a new parameter is added to the **Tax setup parameters** page, which allows user to choose based on which currency the tax should be calculated for Import/Export Order. By default, the **Transaction currency** allows you to choose which currency the tax should be calculated for an import/export order. By default, the **Transaction currency** is the same as the original system behavior. If you choose **Accounting currency**, the system will calculate the tax based on the assessable value in accounting currency.

## Regulatory updates
For information about the regulatory updates for Finance and Operations, see [Localization and Regulatory features – Regulatory updates](../../../finance/localizations/regulatory-updates.md). Alternatively, you can sign in to Lifecycle Services (LCS) and view the planned regulatory updates using the issue search tool, where you can search by country/region, type of feature, and release.

## Additional resources

### Bug fixes
For information about the bug fixes included in each of the updates that are part of Finance and Operations version 10.0.3, sign in to Lifecycle Services (LCS) and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=320385&dbType=3&qc=d5539716f56ccea45e2187c269570772af20e1f10a78371811220da6315a3c34).

### Platform update 27
Microsoft Dynamics 365 Finance and Operations version 10.0.3 includes Platform update 27. To learn more about Platform update 27, see [What's new or changed in Dynamics 365 Finance and Operations platform update 27 (June 2019)](whats-new-platform-update-27.md).

### Dynamics 365 April '19 release notes
Wondering about upcoming and recently released capabilities in any of our business apps or platform?

[Check out the April '19 release notes](/business-applications-release-notes/April19/index). We've captured all the details, end to end, top to bottom, in a single document that you can use for planning.

### Removed and deprecated features
The [Removed or deprecated features for finance and operations](../../dev-itpro/migration-upgrade/deprecated-features.md) article describes features that have been removed or deprecated for Dynamics 365 Finance and Operations.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature is not in active development and may be removed in a future update.

Before any feature is removed from the product, the deprecation notice will be announced in the [Removed or deprecated features for finance and operations](../../dev-itpro/migration-upgrade/deprecated-features.md) article 12 months prior to the removal.

For breaking changes that only affect compilation time, but are binary compatible with sandbox and production environments, the deprecation time will be less than 12 months. Typically, these are functional updates that need to be made to the compiler.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]

