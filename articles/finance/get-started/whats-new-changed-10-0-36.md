---
# required metadata

title: What's new or changed in Dynamics 365 Finance 10.0.36 (September 2023)
description: This article describes features that are either new or changed in the Microsoft Dynamics 365 Finance version 10.0.36 preview release.
author: twheeloc
ms.date: 05/23/2023
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
|Cash and bank management|Enable check number validation|This feature enables a new parameter "Allow check number validation" in cash and bank management to validate check number when user generates payment. With the parameter turned on, firstly, it will validate if check number exceeds the defined interval with last check number. Users can set up the check number interval. If the check number exceeds the defined interval with last check number, user needs to confirm before proceeding to avoid entering wrong check number manually. Secondly, it will validate if there is any character in the check number.|Feature management|
|Cash and bank management|Generate customer and vendor payments from bank statement and reconciliation|This feature provides feature enhancement on bank statement and reconciliation worksheet. User can generate and post customer and vendor payment journals from selected bank statement lines directly. The posted customer and vendor payment journals will be automatically matched with the original bank statement lines. This is a preview feature available in sandbox only in 10.0.36|Feature management|
|Cash and bank management|Advanced bank reconciliation improvement: enable group conditions in reconciliation matching rules|When this feature is enabled, in advanced bank reconciliation, grouping conditions will be available in the reconciliation matching rules setup for user to match bank statement lines with bank documents in a many to many way.|Feature management|
|Cash and bank management|Automatic importing bank statement from SharePoint folder|This feature enables importing bank statement files from SharePoint folder and allows user to set up recurrence rules to import the files periodically.|Feature management|
|Cash and bank management|Enhancements to bank foreign currency revaluation|Prior to this feature, the bank foreign currency revaluation process considered every financial dimension value when calculating the gain or loss. This feature will allow your organization to select to use all or none of the financial dimensions when calculating the gain or loss. In addition, this feature will change the calculation logic. The calculation will first calculate the balance of the bank account, either with all financial dimensions or no financial dimensions, and then calculate the unrealized gain or loss per ledger account. IMPORTANT: After enabling this feature, it can’t be disabled.|Feature management|
|Cash and bank management|Accounts payable/ accounts receivable foreign currency revaluation performance improvement by splitting into even batches|This feature further enhances the performance improvement on top of feature "Foreign Currency Revaluation performance Improvements" by splitting into even batches to avoid some batches containing a large amount of data from a certain vendor or customer.|Feature management|
|Cash and bank management|Use the time zone option on bank statement import form for BAI2 format bank statement id generation|If a bank statement format uses time stamp to generate bank statement id, this feature will use the time zone option on bank statement import form instead of user option.|Feature management|

## Feature enhancements included in this release

The following table lists the feature enhancements that are included in this release. Each of these enhancements provides an incremental improvement to an existing feature. Because they are only enhancements, they aren't listed in the [release plan](/dynamics365/release-plan/2023wave1/finance-operations/dynamics365-finance).

| Feature area | Feature name | More information |
|--------------|--------------|------------------|
