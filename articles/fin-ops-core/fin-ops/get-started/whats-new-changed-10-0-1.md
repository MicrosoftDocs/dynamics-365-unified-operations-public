---
title: What's new or changed in Finance and Operations version 10.0.1 (April 2019)
description: This article describes features that are either new or changed in Dynamics 365 Finance and Operations version 10.0.1. This version will be released in April.
author: sericks007
ms.date: 10/02/2019
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
# What's new or changed in Finance and Operations version 10.0.1 (April 2019)

[!include [banner](../includes/banner.md)]


This article describes features that are either new or changed in Microsoft Dynamics 365 Finance and Operations version 10.0.1. This version will be released in April and has a build number of 10.0.51. For more information about version 10.0.1, see [Additional resources](whats-new-changed-10-0-1.md#additional-resources).

To learn about the new features and changes in the latest releases of Retail, see [What's new or changed in Dynamics 365 for Retail version 10.0.1](../../../commerce/get-started/whats-new-10-0-1.md).


## Enable edit for externally maintained fields

Due to integration scenarios with external systems, such as the Prospect to cash integration, certain fields on Global address book and customer records were marked as externally maintained with the expectation that these values would be maintained in an external system. The **Enable edit for externally maintained fields** option has been added to the Global address book parameters (**Organization administration > Global address book > Global address book parameters**) with the default value of **No**.  If the user scenario requires these fields to be available for edit even though maintained externally, the value can be set to **Yes**.

## Russian features

### Journal of alcohol sales
This functionality includes printing the journal of Alcohol retail sales in statutory format.

### Electronic format of accounting reporting
Electronic reporting configuration is now available. It allows you to generate accounting reporting in electronic format, and contains data calculated based on the configured Financial report. For more information, see [Accounting reporting in electronic format (Russia)](../../../finance/localizations/rus-accounting-reporting.md)

You can find information about how to do the following tasks in [Financial reporting (Russia)](../../../finance/localizations/rus-financial-reports.md):
- Set up financial reports.
- Configure Electronic reporting to use the results of financial report calculations.
- Configure electronic messages to generate the financial report and store the results.

For more information about configuring printing for financial reports in Excel, see [Configure financial reports in Excel (Russia)](../../../finance/localizations/rus-excel-financial-report.md)

### Assessed tax registers and electronic format of declaration version 5.05 (2019)
This functionality allows you to keep technical and tax information for realty assets, calculate assessed tax registers, and generate assessed tax declaration in electronic format, applicable from the reporting for year 2019. For more information, see [Assessed tax declaration (Russia)](../../../finance/localizations/rus-assessed-tax-declaration.md)

### Transport tax registers and electronic format of declaration
This functionality allows you to keep technical and tax information for vehicles, calculate transport tax registers, and generate transport tax declaration in electronic format.

### Land tax registers and electronic format of declaration version 5.06 (2018)
This functionality allows you to keep technical and tax information for ground areas, calculate land tax registers, and generate land tax declaration in electronic format, applicable from the annual reporting for year 2018.

### VAT declaration in electronic format version 5.06 (2019)
This functionality allows you to generate a VAT statement in XML format that is applicable from the reporting for year 2019.
For more information, see [VAT declaration (Russia)](../../../finance/localizations/rus-VAT-declaration.md).

### Sales, purchase books, and factures journals in electronic format (2019)
This functionality allows you to generate sales, purchase books, and factures journals in electronic format applicable from the year 2019. For details about how to work with sales and purchase books, see [Sales books, purchase books, and invoice-factures journals](../../../finance/localizations/rus-sales-books-purchase-books.md).

## Regulatory updates
For information about the regulatory updates for Finance and Operations, see [Regulatory updates](../../../finance/localizations/regulatory-updates.md). Alternatively, you can sign in to Lifecycle Services (LCS) and view the planned regulatory updates using the issue search tool, where you can search by country/region, type of feature, and release.

## Extensibility enhancements

In this release of Finance and Operations, numerous enhancements have been made to support extensibility. For example, extensibility enhancements have been made to enumerations, metadata, and methods. For detailed information, see [Extensibility changes in Dynamics 365 Finance version 10.0.1](../../dev-itpro/extensibility/extensibility-changes-10-1.md).

## Additional resources

### Bug fixes
For information about the bug fixes included in each of the updates that are part of Finance and Operations version 10.0.1, sign in to Lifecycle Services (LCS) and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=299640&dbType=3&qc=2da6de70aab0f4c61b0f920b3242211f5043697189d50a6e1fb1ac3d27ee5f78).

### Platform update 25
Microsoft Dynamics 365 Finance and Operations version 10.0.1 includes Platform update 25. To learn more about Platform update 25, see [What's new or changed in Dynamics 365 Finance and Operations platform update 25 (April 2019)](whats-new-platform-25.md).

### Dynamics 365 April '19 release notes
Wondering about upcoming and recently released capabilities in any of our business apps or platform?

[Check out the April '19 release notes](/business-applications-release-notes/April19/index). We've captured all the details, end to end, top to bottom, in a single document that you can use for planning.

### Removed and deprecated features
The [Removed or deprecated features for finance and operations](../../dev-itpro/migration-upgrade/deprecated-features.md) article describes features that have been removed or deprecated for Dynamics 365 Finance.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature is not in active development and may be removed in a future update.

Before any feature is removed from the product, the deprecation notice will be announced in the [Removed or deprecated features for finance and operations](../../dev-itpro/migration-upgrade/deprecated-features.md) article 12 months prior to the removal.

For breaking changes that only affect compilation time, but are binary compatible with sandbox and production environments, the deprecation time will be less than 12 months. Typically these are functional updates that need to made to the compiler.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]

