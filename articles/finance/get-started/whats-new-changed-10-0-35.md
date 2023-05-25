---
# required metadata

title: What's new or changed in Dynamics 365 Finance 10.0.35 (May 2023)
description: This article describes features that are either new or changed in the Microsoft Dynamics 365 Finance version 10.0.35 preview release.
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
ms.dyn365.ops.version: 10.0.35

---

# What's new or changed in Dynamics 365 Finance 10.0.35 (May 2023)

[!include [banner](../includes/banner.md)]

[!include [banner](../includes/preview-banner.md)]

This article lists features that are new or changed for Microsoft Dynamics 365 Finance version 10.0.35. This version has a build number of 10.0.XXXX and is available on the following schedule:

- **Preview of release:** May 2023
- **General availability of release (self-update):** June 2023
- **General availability of release (auto-update):** July 2023

## Features included in this release

The following table lists the features that are included in this release. We might update this article to include features that made it into the build after this article was initially published.

| Feature area | Feature | More information | Enabled by |
|--------------|---------|------------------|------------|
| Tax Calculation | Enable exchange rate types for sales tax | The feature enables value-added tax (VAT) amounts for foreign invoice transactions to be calculated at an exchange rate that differs from the exchange rate on the document date. This functionality will be available only for legal entities where the Tax calculation service is enabled for the selected business processes. | Feature management |
| Globalization | Electronic Invoicing service – French e-invoice integration with Chorus Pro | The Electronic Invoicing service in Dynamics 365 Finance enables businesses to fully automate the electronic invoicing clearance process from end to end. This automation ranges from issuing sales invoices, free text invoices, and project invoices, to submitting electronic invoices to Chorus Pro for clearance purposes and then distributing them to other companies that are registered in Chorus Pro. This feature provides compliance with the legal requirements for electronic invoicing in France. | Feature management |

## Feature enhancements included in this release

The following table lists the feature enhancements that are included in this release. Each of these enhancements provides an incremental improvement to an existing feature. Because they are only enhancements, they aren't listed in the [release plan](/dynamics365/release-plan/2023wave1/finance-operations/dynamics365-finance).

| Feature area | Feature name | More information |
|--------------|--------------|------------------|
| General ledger | Financial tags | When the Financial tags feature is enabled, additional financial tags are available. Financial tags have been added to the **Load ledger transactions** function. Additionally, for general journal entries that are marked as **Reversing entry**, default financial tag values will be entered on the reversal entries. Default financial tags are entered from the ledger account to the split values for the breakdown of voucher functionality in journals. |
| General ledger | Ability to view the original document's financial tags for Ledger settlements | You can view the original document's financial tag values on the **Ledger settlement** page. This information will be updated for opening balances for the ledger settlement main accounts that are defined to keep details during the year-end close process. |
| Project management and Accounting | Enable GST/TDS-TCS tax support for Project Integration Journal | When the feature is enabled, Indian indirect and direct taxes are available in the Project integration journal. This feature provides an option that lets users review transactions and adjust tax attributes and accounting attributes as needed in all types of integration journals. |
| Subscription billing | Ability to use sales agreements with billing schedules | Billing schedules can create a sales agreement or be linked to a sales agreement and use the pricing from the sales agreement. |
