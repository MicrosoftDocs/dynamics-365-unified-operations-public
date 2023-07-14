---
title: What's new or changed in Dynamics 365 Finance and Operations version 8.1.3 (January 2019)
description: This article describes features that are either new or changed in Dynamics 365 Finance and Operations version 8.1.3. This version will be released in January 2019.
author: sericks007
ms.date: 10/15/2019
ms.topic: article
ms.prod: 
ms.technology: 
audience: Developer, IT Pro
ms.reviewer: sericks
ms.search.region: Global
ms.author: sericks
ms.search.validFrom: 2018-12-31
ms.dyn365.ops.version: Release 8.1.3
ms.custom: 
ms.assetid: b364a31d-34de-45c5-b698-64c5262c592e
ROBOTS: NOINDEX, NOFOLLOW
---
# What's new or changed in Dynamics 365 Finance and Operations version 8.1.3 (January 2019)

[!include [banner](../includes/banner.md)]

This article describes features that are either new or changed in Microsoft Dynamics 365 Finance and Operations version 8.1.3. This version will be released in January 2019 and has a build number of 8.1.227.

To learn about the new features and changes in the latest releases of Retail, see [What's new or changed in Dynamics 365 for Retail](../../../commerce/get-started/whats-new.md).

### Dynamics 365 October '18 release notes

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

[Check out the October '18 release notes](/dynamics365/release-plans/). We've captured all the details, end to end, top to bottom, in a single document that you can use for planning.

### Bug fixes

For information about the bug fixes included in each of the updates that are part of Finance and Operations version 8.1.3, sign in to Lifecycle Services (LCS) and view the [KB article](https://go.microsoft.com/fwlink/?linkid=2049362).

### Platform update 23

Microsoft Dynamics 365 Finance and Operations version 8.1.3 includes Platform update 23. To learn more about Platform update 23, see [What's new or changed in Dynamics 365 Finance platform update 23 (January 2019)](whats-new-platform-update-23.md).

## Extensibility enhancements

In this release of Finance and Operations, numerous extensibility enhancements have been made to support extensibility including enhancements to enumerations, metadata, and methods. For detailed information, see [Extensibility changes in Dynamics 365 Finance version 8.1.3](../../dev-itpro/extensibility/extensibility-changes-813.md).

## Collection letters

You can now set up collection letters at the customer level, so that the collection letter code for each transaction is tracked but the collection letter processing will be based on a single collection letter level that is stored for the customer. For more information, see [Process collection letters](../../../finance/accounts-receivable/tasks/process-collection-letters.md).

## Settle remainder

You can settle the amount remaining from settlement activity by applying that amount to a ledger account or another customer. You can settle the remainder when you are settling amounts entered into a journal or when you are only settling open transactions. For more information, see [Settle remainder](../../../finance/cash-bank-management/settle-remainder.md).

## Globalization

### Electronic reporting: Import from files in JSON format

You can now configure an Electronic reporting (ER) format to parse incoming files in JSON format. You can then set up ER mappings that specify how information from JSON files is used to update application data.

### Electronic reporting: Support country/region context-specific ER model mappings
You can specify a country context for ER model mapping. You can also manage multiple country-specific mappings for a single ER data model. This allows you to isolate country-specific logic of data access in a single ER model mapping. Depending on the legal entity's primary address, the appropriate country/region-specific model mapping will be used when an ER format is used to generate an electronic document. 

## Russian-specific features
This release contains the following features for Russia.

### Accounts receivable
- Tax registers allow you to track and manage taxable profits and losses in accordance with Russian tax accounting principles. The following tax registers are now available.
  -  **Accounts receivable inventory act** register 
  -  **Accounts receivable – bad debts reserve** register
  -  **Accounts receivable - bad debt reserve movement** register 
  -  **Accounts receivable movement** register 
- Accounts receivable bad debts can now be written off.
 
### Accounts payable
 - Tax registers allow you to track and manage taxable profits and losses in accordance with Russian tax accounting principles. The following tax registers are now available.
   - **Accounts payable inventory act** register
   - **Accounts payable debt movement** register 
 - Accounts payable bad debts can now be written off.

### Client-bank interface and reconciliation procedure
This release adds the interface and electronic reporting configurations examples required to use the Client-Bank functionality.
To use this feature, the following electronic reporting configurations should be imported from Lifecycle Services and selected in the following settings:
- Payment model.version.22
- Payment model mapping to destination (RU).version.22.4
- Bank statement (RU).version.22.6
- Payment order (RU).version.22.4


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]

