---
title: What's new or changed in Dynamics 365 Finance 10.0.44 (June 2025)
description: Learn about features that are either new or changed in the Microsoft Dynamics 365 Finance version 10.0.44 preview release.
author: twheeloc
ms.author: twheeloc
ms.topic: faq
ms.date: 04/26/2025
ms.custom:   
  - bap-template
  - evergreen
ms.reviewer: twheeloc
ms.search.region: Global
---

# What's new or changed in Dynamics 365 Finance 10.0.44 (June 2025)

[!include [banner](../includes/banner.md)]
[!include [banner](../includes/preview-banner.md)]

This article lists the features that are new or changed for Microsoft Dynamics 365 Finance version 10.0.44. This version has a build number of 10.0.xxxx and is available on the following schedule:

- **Preview of release:** April 2025
- **General availability of release (self-update):** May 2025
- **General availability of release (auto-update):** June 2025

## Features included in this release

This section contains a table that lists the features that are included in this release when available. We might update this article to include features that were added to the build after this article was originally published.

| Module or feature area | Feature name | More information | Enabled by |
|---|---|---|---|
|Fixed assets| Post the inventory close adjustment to the fixed assets subledger after purchase order invoice adjustment |This feature automates the adjustment process for fixed assets acquired through purchase order invoices that include inventory items. When an invoice is adjusted, the inventory closing recalculation process automatically generates and posts corresponding entries to the fixed assets subledger, ensuring consistency, reducing manual effort, and maintaining accurate financial records.| Feature management |
|Fixed assets| Budget depreciation proposal running in the background across multiple legal entities |This feature introduces a new menu item, **Create budget depreciation proposal** that uses background batch job processing to run depreciation budgets across multiple legal entities. Users no longer need to manually execute the budget for each company, saving time, reducing manual effort, and enhancing consistency throughout the organization. | |
|Fixed assets |Add financial tags on inventory to fixed asset journal |This feature adds financial tags to the line details in the inventory to fixed asset journal, allowing users to assign financial tags prior to posting. It improves asset categorization and traceability, leading to more accurate financial management and streamlined reporting. | |
|Asset leasing |Ability to assign sales tax group and item tax group on the asset lease |This feature introduces **Sales tax group** and **Item sales tax group** fields in the lease/lease book. When a lease book is marked as **Pay to vendor**, these defined values are automatically copied to the vendor invoice journal created from the payment schedule. If a vendor or main account already specifies a sales tax group or item sales tax group, the system defaults to those; otherwise, it applies the default values defined on the lease.| Feature management |
|Asset leasing | Add cancel option to the lease termination |The **Lease termination proposal cancellation** feature adds a **Cancel** option, allowing users to revoke termination proposals. When triggered, the **Proposal status** updates to **Canceled** and resets the lease book, enhancing flexibility and ensuring accurate, controlled lease management.| Feature management |
|General ledger| Year-end close job status verification |To ensure a year-end close job is truly running and not stuck in an error state from a batch crash or restart, a batch job is add to the Ledger fiscal close service history table. This allows us to verify if the batch job is active and safely reset its status when needed.| Feature management |
|General ledger | Review missing settlement accounts |This page displays any ledger accounts that have ledger settlements but are missing from the Ledger settlement page in General ledger parameters. Learn more at [Ledger settlements](../general-ledger/ledger-settlements.md). | Default |
| Cash and bank management | **Bank transactions** page performance improvement | This feature introduces performance enhancements on the **Bank transactions** page. The introduced changes allow users to optionally set default filters to show only transactions meeting the criteria. By enabling this feature, users are able to access the bank documents form directly from the **Bank account** page. | Feature management | 
| Cash and bank management | Enable process automation for bank foreign currency revaluation | By enabling this feature, users are able to run bank foreign currency revaluation using process automation. | Feature management |  
| Cash and bank management | Accounts payable enable settle with priority | This feature enhances the Accounts payable module by introducing settlement priority. It allows users to assign a predetermined order to transactions, which can be applied during both manual and automatic settlements. | Feature management | 
| Credit and collections	| Collection process automation to include project invoices and general journals| 	Collection process automation previously didn't include project invoices and general journals, with this feature enabled, users can include them.	| Feature management| 
| Credit and collections| 	Include general journals in the interest calculation process| When creating interest notes, users can include general journals so interest is calculated on them.	| Feature Management| 
| Accounts receivable	| Prepayment customer invoice feature	| The **Prepayment customer invoice** feature allows users to create and manage invoices for customer prepayments. This feature streamlines the invoicing process and enhances customer relationships by offering flexible payment options.| 	Feature management| 
| Subscription billing	| Performance issue creating billing detail lines for daily usage billing schedule line| Improved performance by replacing the line-based logic to set based processing Subscription billing consumption entry. In addition to performance improvements, pricing control logic is updated to ensure consistency and prevent pricing discrepancies.| 	Feature management| 
| Subscription billing	| Performance improvement for consumption quantity update | 	Termination adjustments is now calculated using the exchange rate on the termination date, posts currency fluctuation differences to the Profit and loss account, and maintains a clear audit trail in the deferral schedule. | 	Feature management| 
| Accounts receivable| 	Clean up Free text invoice temp tables used in Free text invoice report. | 	Data update automatically schedules maintenance jobs to clean up temporary data for Free text and Sales invoice reports, eliminating the need for manual scheduling by users.| Default | 


## Feature enhancements included in this release

This section contains a table that lists the enhancements that are included in this release when available. We might update this article to include features that were added to the build after this article was originally published.

| Module or feature area | Feature name | More information | Enabled by |
|---|---|---|---|
| Cash and bank management | Modern bank reconciliation | To prevent the import of duplicate bank statements, we check for a combination of AccountNo, StatementID, FromDate, and ToDate. If these elements match an existing bank statement, it is considered a duplicate and isn't imported. This ensures that each bank statement file is unique and avoids redundancy. | Default |
| Cash and bank management | Customer and vendor netting | The **Netting history** feature provides a comprehensive overview of all netted transactions between customer and vendor pairs, ensuring transparency and ease of tracking. | Feature management |
| Credit and collections	| CustCollectionsBIMeasurementV3	| CustCollectionsBIMeasurementV3 is a new entity and the CustCollectionsBIMeasurement entity is deprecated.| 	Default| 
| Credit and collections	| Exclude intercompany sales orders from credit management| Moved the **Exclude from credit management for intercompany sales orders** feature to a parameter.	| Parameter| 
| Accounts receivable| 	Prepayment customer invoice feature	| Microsoft Dynamics 365 finance and operations introduced a significant enhancement with the **Customer prepayment invoice** feature. This feature is  aimed at improving control and transparency over customer prepayment processes. |Feature management | 



## Features turned on by default in this release

The following table lists the features that are turned on by default in version 10.0.44. Most features that were turned on automatically can be turned off in [Feature management](../../fin-ops-core/fin-ops/
get-started/feature-management/feature-management-overview.md). In the future, some features that were turned on automatically might be removed from Feature management and become mandatory. This change ensures 
that customers are using current functionality, so that as enhancements are added, they can build on the current functionality. Features are never automatically enabled in less than one year, unless they're 
determined to be essential.

| Feature name | Feature state | Module |
|--------------|---------------|--------|

## Features removed from Feature management

The following table lists the features that were removed from Feature management in version 10.0.44.

| Feature name | Feature state | Module |
|--------------|---------------|--------|
|Exclude intercompany sales orders from credit management|	The **Exclude from credit management for intercompany sales orders** feature moved to a parameter.	|Credit and collections |

## More information

### Platform updates for finance and operations apps

Dynamics 365 Finance version 10.0.44 includes platform updates. To learn more, see [Platform updates for version 10.0.44 of finance and operations apps](../../fin-ops-core/fin-ops/get-started/whats-new-platform
-updates-10-0-44.md).

### Bug fixes

For information about the bug fixes that are included in this update, sign in to Microsoft Dynamics 365 Lifecycle Services, and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=xxxx).

### Regulatory updates

For information about regulatory updates for finance and operations apps, see [Regulatory updates](../localizations/regulatory-updates.md). Another way to learn about regulatory updates is to sign in to Lifecycle
Services and view the planned regulatory updates using the issue search tool. Issue search lets you search by country/region, type of feature, and release.

### Dynamics 365 and industry clouds: 2025 release wave 1 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out [Dynamics 365 and industry clouds: 2024 release wave 1 plan](/dynamics365/release-plan/2025wave1/finance-supply-chain/dynamics365-finance). We've captured all the details, end to end, top to bottom, that you can use for planning.


