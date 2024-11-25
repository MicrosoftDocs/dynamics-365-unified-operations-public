---
title: What's new or changed in Dynamics 365 Finance and Operations version 8.1.2 (December 2018)
description: Learn about new or changed features in Dynamics 365 Finance and Operations version 8.1.2. This version was released in December 2018.
author: sericks007
ms.author: sericks
ms.topic: whats-new
ms.date: 07/12/2024
ms.custom: 
  - bap-template
  - evergreen
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2018-11-02
ms.dyn365.ops.version: Release 8.1.2 
ms.assetid: b364a31d-52de-45c5-b698-64c5262c592a
ROBOTS: NOINDEX, NOFOLLOW
---

# What's new or changed in Dynamics 365 Finance and Operations version 8.1.2 (December 2018)

[!include [banner](../../../finance/includes/banner.md)]

This article describes features that are either new or changed in Microsoft Dynamics 365 Finance and Operations version 8.1.2. This version was released in December 2018 and has a build number of 8.1.195.

To learn about the new features and changes in the latest releases of Retail, see [What's new or changed in Dynamics 365 for Retail](../../../commerce/get-started/whats-new.md).

### Dynamics 365 October '18 release notes

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

[Check out the October '18 release notes](/dynamics365/release-plans/). We've captured all the details, end to end, top to bottom, in a single document that you can use for planning.

## Bug fixes

For information about the bug fixes included in each of the updates that are part of Platform update 22, sign in to Lifecycle Services (LCS) and view the [KB article](https://go.microsoft.com/fwlink/?linkid=2037783).

## Platform update 22

Microsoft Dynamics 365 Finance and Operations version 8.1.2 includes Platform update 22. To learn more about Platform update 22, see [What's new or changed in Dynamics 365 Finance platform update 22 (December 2018)](whats-new-platform-update-22.md).

## Extensibility enhancements

In this release of Finance and Operations, numerous extensibility enhancements have been made to support extensibility including enhancements to enumerations, metadata, and methods. For detailed information, see [Extensibility changes in Dynamics 365 Finance version 8.1.2](../extensibility/extensibility-changes-812.md).

## Derived dimension values

This release includes functionality that lets you prevent changes to derived dimension values and override existing dimension values with derived dimension values. For more information, see [Financial dimensions](../../../finance/general-ledger/financial-dimensions.md).

## Resume master planning
This release includes enhanced planning engine functionality that helps to ensure that master planning batch jobs automatically resume if the main thread stops unexpectedly. This can happen if, for some reason, the batch server connection is lost during the master planning run. Before this feature was implemented, a complete rerun of master planning was needed. Now the master planning batch jobs automatically resume and continue at the place where they were interrupted. From the Master planning history log, the planner can see that the main thread was stopped unexpectedly and that the process was resumed.

Resume will only happen once. This means that if the main thread unexpectedly stops again, during the resume, it will mark it as failed in the log and not try to resume. Also, resume is only applied to regeneration and jobs that have reached at least the coverage state of the master planning calculation. If a helper thread stops unexpectedly, planning will continue with the remaining helpers.

## Intrastat format changes for Belgium
This release includes changes to the XML Intrastat format for Belgium that applies to reporting for 2019. To apply the new format, you need to import the following version (or a later version) of the ER configuration from the LCS shared asset library: Intrastat (BE).version.2.6.xml. For more information about how to import configurations, see [ER Import a configuration from Lifecycle Services](../analytics/tasks/er-import-configuration-lifecycle-services.md). 

## India-specific features
In this release, if [GTE](../../../finance/general-ledger/tax-engine.md) is enabled for a legal entity, some global fields and buttons will be hidden from the user interface. This simplifies the user interface for users by hiding fields and buttons on taxable documents like Purchase orders and Sales order that don't apply when GTE is used. The following fields or buttons will be hidden if GTE is enabled.

 - Sales tax group
 - Item sales tax group
 - Sales tax button
 
The current standard GST configuration does not include VAT, so if your business needs to handle VAT, you must extend the configuration to use VAT. For more information, see [Extending tax engine configurations](../../../finance/dev-itpro/extend-tax-engine-configurations.md).

## Russian-specific features
This release includes the following features specific for Russia:

### Third-party miscellaneous charges for Russia
- Inclusion into cost of purchased goods (allocation to invoices lines from other vendors). 
- Redrawing to other parties. 
- Re-allocation to other expense accounts.

### Bailment for Russia

**Accounting at Bailee side**
 - Accounting of inventory receipt for bailment as required by law and generation of primary form MX-1. 
 - Accounting of inventory return from bailment and generation of primary form MX-3. 
 - Bailment costs calculation from Bailee side.
 
 **Accounting at Owner side**
 - Accounting of inventory transfer to bailment and inventory return from bailment on Goods Owner side under bailment service contract.

### Goods in transit for Russia

**Sales to customer with postponed passing of property**
 - Post sales invoice with postponed property transfer. This means that customer debts are not posted, all outgoing taxes are posted, and items are transferred to transit warehouse. 
 - Register passing of property with posting debts and items sale from transit warehouse.

**Goods in transit from vendor**
 - Register goods in transit from vendor by special posting profile with Item type "purchased items en route". 
 - Creating Act of inventory holdings en route (INV-6).

### Optional posting of transfer orders to general ledger
Option to post or not post transactions to General ledger when posting a transfer order.

### Profit tax registers for assets
The following tax registers are available:
 - **Goods cost calculation**
 - **FA object information** 
 - **IA object information** 
 - **FA depreciation** 
 - **IA depreciation** 
 - **FA/IA sale**
 - **Depreciation bonus recovery**

### Sales, purchase books, additional sheets, invoice-factures journal in electronic format
In this release, you can review electronic formats of sales, purchase books, additional sheet,s and factures journals that are configured with Electronic reporting. 

To apply the new formats, you need to import the following or higher versions of the ER configurations from the LCS shared asset library:  
 - VAT declaration model (RU).version.46
 - VAT declaration model mapping (RU).version.46.70
 - Purchase book format.version.46.13
 - Sales book format.version.46.13
 - Purchase book additional sheet format.version.46.9
 - Sales book additional sheet format.version.46.13
 - Factures journal format.version.46.4
 
For more information, see [ER Import a configuration from Lifecycle Services](../analytics/tasks/er-import-configuration-lifecycle-services.md). 

These configuration versions are released as public preview and will be updated based on feedback received. Use them to learn how electronic formats of sales, purchase books, additional sheets, and factures journals are configured with Electronic reporting. Do not use these configurations as base configurations for derived customized configurations in a live environment.

For more information, see [Sales books, purchase books, and invoice-factures journals](../../../finance/localizations/russia/rus-sales-books-purchase-books.md).



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]

