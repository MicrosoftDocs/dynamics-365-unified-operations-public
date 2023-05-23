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
- **General availability of release (auto-update):** Junly 2023

## Features included in this release

The following table lists the features that are included in this release. We might update this article to include features that made it into the build after this article was initially published.

| Feature area | Feature | More information | Enabled by |
|--------------|---------|------------------|------------|
| Tax Calculation | Enable exchange rate types for sales tax | The feature enables calculation of VAT amount for foreign invoice transactions on exchange rate different from the document date. This functionality will be available only for the legal entities with the enabled Tax calculation service for the selected business processes. | Feature management |
|Globalization |Electronic Invoicing service – French e-invoice integration with Chorus Pro|The Electronic Invoicing service in Dynamics 365 Finance allows businesses to fully automate the electronic invoicing clearance process end to end. This automation ranges from issuing sales, free text, and project invoices to submitting electronic invoices to Chorus Pro for clearance purposes and then distributing them to other companies registered in Chorus Pro. This feature provides compliance with the legal requirements for electronic invoicing in France.| Feature management|


## Feature enhancements included in this release

The following table lists the feature enhancements that are included in this release. Each of these enhancements provides an incremental improvement to an existing feature. Because they are only enhancements, they aren't listed in the [release plan](/dynamics365-release-plan/2023wave1/finance-operations/dynamics365-finance).

| Feature area | Feature name | More information |
|--------------|--------------|------------------|
|General ledger|Financial tags|When the Financial tags feature is enabled, additional financial tags are available. Financial tags have been added to the Load ledger transactions function. Additionally, general journal entries that are marked as **Reversing entry**, financial tag values will default on the reversal entries. Financial tags default from the Ledger account to the split values for the breakdown of voucher functionality in journals.|
|General ledger|Ability to view the original document’s financial tags for Ledger settlements|You can view the original document’s financial tag values on the **Ledger settlement** page. This information will be updated for opening balances for the ledger settlement main accounts that are defined to keep details during the year-end close process.|
|Project management and Accounting |Enable GST/TDS-TCS tax support for Project Integration Journal|When the feature is enabled, India Indirect and direct taxes are available on Project integration Journal . This feature provides users with an option to review transactions and adjust tax attributes and accounting attributes as needed in all the types of integration journals.|
|Subscription billing |Ability to use sales agreements with billing schedules |Billing schedules can create a Sales agreement or be linked to a sales agreement and leverage the pricing from the sales agreement.|




