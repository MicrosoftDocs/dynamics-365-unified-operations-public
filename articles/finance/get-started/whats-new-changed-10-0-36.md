---
# required metadata

title: What's new or changed in Dynamics 365 Finance 10.0.36 (September 2023)
description: This article describes features that are either new or changed in the Microsoft Dynamics 365 Finance version 10.0.36 preview release.
author: twheeloc
ms.date: 07/23/2023
ms.topic: faq
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2022-09-02
ms.dyn365.ops.version: 10.0.36

---

# What's new or changed in Dynamics 365 Finance 10.0.36 (September 2023)

[!include [banner](../includes/banner.md)]

[!include [banner](../includes/preview-banner.md)]

This article lists features that are new or changed for Microsoft Dynamics 365 Finance version 10.0.36. This version has a build number of 10.0.XXXX and is available on the following schedule:

- **Preview of release:** July 2023
- **General availability of release (self-update):** August 2023
- **General availability of release (auto-update):** September 2023

## Features included in this release

The following table lists the features that are included in this release. We might update this article to include features that made it into the build after this article was initially published.

| Feature area | Feature | More information | Enabled by |
|--------------|---------|------------------|------------|
|Cash and bank management|Enable check number validation|This feature enables the **Allow check number validation** feature in Cash and bank management to validate check numbers when users generates a payment. With the parameter turned on, the check number is validated to see if it exceeds the defined interval with last check number. Users can set up the check number interval. If the check number exceeds the defined interval with last check number, user needs to confirm before proceeding to avoid entering wrong check number manually. It also validates that there is not a character in the check number.|Feature management|
|Cash and bank management|Generate customer and vendor payments from bank statements and reconciliation.|This feature enhances the bank statement and reconciliation worksheet. Users can generate and post customer and vendor payment journals from selected bank statement lines directly. The posted customer and vendor payment journals are automatically matched with the original bank statement lines. This is a preview feature available in sandbox environments in version Dynamics 365 Finance 10.0.36.|Feature management|
|Cash and bank management|Improved advanced bank reconciliation by enabling group conditions in reconciliation matching rules.|In advanced bank reconciliation, grouping conditions are available in the reconciliation matching rules setup to match bank statement lines with bank documents in a many to many way.|Feature management|
|Cash and bank management|Automatic importing bank statement from a SharePoint folder.|This feature imports bank statement files from a SharePoint folder and allows users to set up recurrence rules to import the files periodically.|Feature management|
|Cash and bank management|Bank foreign currency revaluation enhancements|Prior to this feature, the bank foreign currency revaluation process considered every financial dimension value when calculating the gain or loss. This feature allows your organization to select to use all or none of the financial dimensions when calculating the gain or loss. In addition, this feature changes the calculation logic. The calculation will first calculate the balance of the bank account, either with all financial dimensions or no financial dimensions, and then calculate the unrealized gain or loss per ledger account.  <p>**IMPORTANT:** This feature can't be disabled after it's been enabled. <p> |Feature management|
|Cash and bank management|Accounts payable and accounts receivable foreign currency revaluation performance improvement by splitting into even batches.|This feature improves the performance of the foreign currency revaluation by splitting large batches into even batches to avoid large batches from a certain vendor or customer.|Feature management|
|Cash and bank management|Use the time zone option on bank statement import page for BAI2 format bank statement id generation.|If a bank statement format uses time stamp to generate bank statement id, this feature uses the time zone option on bank statement import page instead of the user option.|Feature management|
|General ledger|	Post foreign currency realized gains/losses for ledger settlements|	This feature posts foreign currency realized gains and realized losses for ledger settlements when the reporting currency values of the debits and credits differ. This feature also enhances usability to the Ledger settlement process by reducing the effort needed to mark vouchers.|	Feature management|

## Feature enhancements included in this release

The following table lists the feature enhancements that are included in this release. Each of these enhancements provides an incremental improvement to an existing feature. Because they are only enhancements, they aren't listed in the [release plan](/dynamics365/release-plan/2023wave1/finance-operations/dynamics365-finance).

| Feature area | Feature name | More information |
|--------------|--------------|------------------|
|Financial tags|	On by default|	General ledger|
|(Italy) Fiscal journal page numbering improvements|	Mandatory|	General ledger|
|Journal reversal no longer requires consecutive number sequence	|Mandatory	|General ledger|
|Allow edits to internal data on general ledger vouchers	|Mandatory	|General ledger|
|Amount details from **General journal account** entry are displayed on the **Trial balance with transactional detail** report	|Mandatory|	General ledger|
|Awareness between ledger settlement and year-end close|	On by default|	General ledger|
|Add a date filter when viewing unsettled ledger transactions|	Mandatory|	General ledger|
