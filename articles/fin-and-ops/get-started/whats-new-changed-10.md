---
# required metadata

title: What's new or changed in Dynamics 365 for Finance and Operations version 10.0 (April 2019)
description: This topic describes features that are either new or changed in Dynamics 365 for Finance and Operations version 10.0. This version will be released in April 2019.
author: tonyafehr
manager: AnnBe
ms.date: 02/11/2019
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
ms.search.validFrom: 2019-04-01 
ms.dyn365.ops.version: Release 10

---
# What's new or changed in Dynamics 365 for Finance and Operations version 10.0 (April 2019)

[!include [banner](../includes/banner.md)]

[!include [banner](../includes/preview-banner.md)]

This topic describes features that are either new or changed in Microsoft Dynamics 365 for Finance and Operations version 10.0. This version will be released in April 2019 and has a build number of 10.0.8.

To learn about the new features and changes in the latest releases of Microsoft Dynamics 365 for Retail, see [What's new or changed in Dynamics 365 for Retail](https://docs.microsoft.com/dynamics365/unified-operations/retail/get-started/whats-new).

### Dynamics 365 April '19 release notes

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

[Check out the April '19 release notes](https://docs.microsoft.com/en-us/business-applications-release-notes/April19/index). We've captured all the details, end to end, top to bottom, in a single document that you can use for planning.

### Bug fixes

For information about the bug fixes included in each of the updates that are part of Finance and Operations version 10.0, sign in to Lifecycle Services (LCS) and view the KB article (coming soon).

### Platform update 24

Microsoft Dynamics 365 for Finance and Operations version 10.0 includes Platform update 24. To learn more about Platform update 24, see [What's new or changed in Dynamics 365 for Finance and Operations platform update 24 (January 2019)](whats-new-platform-update-24.md).

## Extensibility enhancements

In this release of Finance and Operations, numerous extensibility enhancements have been made to support extensibility including enhancements to enumerations, metadata, and methods. For detailed information, see [Extensibility changes in Dynamics 365 for Finance and Operations version 10.0](../../dev-itpro/extensibility/extensibility-changes-10.md).

## Catch weight product processing with warehouse management
This feature allows you to use catch weight products within warehouse management processes. This feature is only available to a limited audience for this release. 

For more information, see [Catch weight product processing with warehouse management](../../supply-chain/warehousing/catch-weight-processing.md).

## Restrict payment methods for returns without a receipt
This feature allows for certain payment types to be restricted for refund if the returns are made without a receipt using Dynamics 365 for Retail.

For more information, see [Restrict payment methods for returns without a receipt](../../retail/payment-methods-restrictions.md).

## Omni-channel advanced auto charges
With the advanced auto-charges features in Dynamics 365 for Retail, orders created in any supported Retail channel (point of sale (POS), call center, and online), can take advantage of the auto charges configurations defined in Dynamics 365 for both header and line-level related charges.  

For more information, see [Omni-channel advanced auto charges](../../retail/omni-auto-charges.md).

## Retail price reports
With this new functionality, store managers can create reports detailing recent or upcoming price changes.

For more information, see [Retail price reports](../../retail/price-report.md).

## Return items across multiple customer orders and invoices
This functionality enables returns across multiple customer orders and invoices in Dynamics 365 for Retail.

For more information, see [Return items across multiple customer orders and invoices](../../retail/multireturn.md).

## Loyalty changes
Functionality has been added to enhance the loyalty features in Dynamics 365 for Retail.

For more information, see [Loyalty overview](../../retail/set-up-customer-loyalty-program.md).

## Non-GST transaction for India 
This feature allows you to create non-GST transaction with the Tax engine. To create a non-GST transaction, you need to select the **Non-GST** check box in the **Tax information** of each taxable transaction line. You also need to make sure that there is a **Number sequence code** for **Bill of supply** in the **Reference number sequence group**. These transactions will be identified as non-GST transactions in the GST return (GSTR). 

## Fiscal printer integration sample for Poland
Microsoft Dynamics 365 for Retail now contains a sample of the integration of POS with fiscal printers for Poland. The sample is a part of the Retail SDK. Implementation partners may extend the integration functionality to cover all required retail scenarios or build integration with other fiscal printer models based on the samples.

## Tax functionality updates for China

In China, official tax invoices can only be issued via two government-authorized invoicing software (Aisino and BaiWang). This feature lets you export the issued invoices into the .TXT and .XML file formats so you can import the files into the authorized invoicing software of Aisino and BaiWang providers accordingly. 

You can also maintain the tax classification and codes in Finance and Operations, which is in alignment with tax integration interface 3.0. The exported invoice file will include commodity codes (classification of goods and services) which is mandatory for China. 

The standard category hierarchy setting functionality is used to include the commodity codes in the invoice lines of the exported file.

The following updates are included in this release:

- There is a new interface with BaiWang provider software that lets you export issued invoices in .XML format and you can import files from BaiWang software in .TXT and .XML formats.
- We updated the structure of the issued invoice that is exported and you can import .TXT file for interface with Aisino provider software.

For more information, see [Configure tax integration for China](../../financials/localizations/apac-chn-tax-integration.md).

## Regulatory updates
For information about the regulatory updates for Finance and Operations, see [Localization and Regulatory features – Regulatory updates](../../financials/localizations/regulatory-updates.md). Alternatively, you can sign in to Lifecycle Services (LCS) and view the planned regulatory updates using the issue search tool, where you can search by country, type of feature, and release.
