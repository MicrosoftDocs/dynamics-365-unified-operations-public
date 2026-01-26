---
title: What's new or changed in Dynamics 365 Finance 10.0.47 (March 2026)
description: Learn about features that are either new or changed in the Microsoft Dynamics 365 Finance version 10.0.47 preview release.
author: twheeloc
ms.author: twheeloc
ms.topic: whats-new
ms.date: 01/26/2026
ms.update-cycle: 1095-days
ms.custom:   
  - bap-template
  - evergreen
ms.reviewer: twheeloc
ms.search.region: Global
---

# What's new or changed in Dynamics 365 Finance 10.0.47 (March 2026) 

[!include [banner](../includes/banner.md)]
[!include [banner](../includes/preview-banner.md)]

This article lists the features that are new or changed for Microsoft Dynamics 365 Finance version 10.0.47. This version has a build number of 10.0.2527 and is available on the following schedule:

- **Preview of release:** January 2026
- **General availability of release (self-update):** March 2026
- **General availability of release (auto-update):** April 2026

## Features included in this release
This section contains a table that lists the features that are included in this release when available. We might update this article to include features that were added to the build after this article was 
originally published.

| Module or feature area | Feature name | More information | Enabled by |
|---|---|---|---|
|Accounts receivable	|(Switzerland) Structured Addresses in QR-Bill|	This feature enables structured addresses (address type “S”) for both biller and debtor, with each address broken into its individual components. |	Feature management|
| Budgeting | Allow cancelation of individual lines on General budget reservations | The feature enables users to cancel individual lines within a General budget reservation. By introducing line-level cancelation, users have the flexibility to manage budget reservations compliantly. If the line has been **Cancelled**, it's also considered **Finalized**. | Feature management 
|Subscription billing| Performance improvements for subscription billing unbilled revenue batch (Preview) |	This feature enhances the subscription billing unbilled revenue mass processing in batch. The batch now processes subscription billing data in parallel, allowing each to run complete more efficiently.	|Feature management|
|Subscription billing|	Transaction date for unbilled revenue recalculation	|The new **Transaction date** field introduces clearer separation between the posting intent and the recalculation date during unbilled revenue processing. This enhances control and mitigates incorrect updates when recalculation is performed outside the billing schedule range.|	Feature management||

## Feature enhancements included in this release

This section contains a table that lists the enhancements that are included in this release when available. We might update this article to include features that were added to the build after this article was originally published.

| Module or feature area | Feature name | More information | Enabled by |
|---|---|---|---|
| General ledger | Ledger period close enhancement (Preview) |This feature introduces multi-stage task statuses, and comprehensive audit trial capability. The task statues risk and issue flags, approval assignment, and enhanced reporting capabilities in the **Period end close** workspace. The audit trial capability in the **Financial period close** workspace, enabling users to track task history, status changes, and related actions through a dedicated side panel.| Feature management |
| General ledger | Update balances button added to dimension set balance calculation in Trial balance |In the Trial balance, the **Update balances** button is now available when the **Performance enhancement for general ledger dimension set balance calculation** feature is enabled in Feature management. You can manually start a batch job to update the dimension set balances instead of waiting for the automatic process to update the balances. For more information, see [General ledger account balances](../general-ledger/general-ledger-account-balances.md). | Feature management |
|General ledger|	Account reconciliation agent|	The Account reconciliation agent functionality has been improved to allow filtering by legal entity on sandbox environments.|	Feature management|
|General ledger|	Account reconciliation workspace	|The Account reconciliation workspace now allows filtering by legal entity on sandbox environments.|	Default|
|Subscription billing|	Billing schedule |	The fix ensures that billing detail lines aren't prematurely deleted from SubBillInvoiceParmLines when multiple batch jobs are created in close succession. This prevents batch tasks from losing their processing context and ensures that billing detail lines are picked up and processed correctly, resulting in successful sales order generation.|	Feature management|
|Tax|	Tax calculation performance improvement	|Standard tax engine performance for free text invoices has been improved through query optimization and the implementation of caching mechanisms. These enhancements are managed by the TaxCalculatePerfFlight flight, which is enabled by default.|	Flight|
|Tax|	Withholding tax performance improvement	|Enhanced the performance of the withholding tax engine in the vendor payment proposal automation scenario through query optimization and the implementation of caching strategies. This improvement is controlled by the TaxWHTPerfFlight flight, which is enabled by default.|	Flight|
|Tax|	Multi-language support in Advanced tax calculation engine		|The Advanced Tax Calculation Engine now supports multiple languages. Labels within both the Tax Feature Setup and Tax Configuration interfaces are translated accordingly. The changes are controlled by the TaxEngineConfigTranslationFlight flight, which is enabled by default. To utilize the translation functionality, the following prerequisites must be met: Tax Data Model: Version 50 or higher; Tax Calculation Data Model: Version 50.78 or higher; Tax Calculation Configuration: Version 50.78.269 or higher.|Tax configuration; Flight|


## Features turned on by default in this release

The following table lists the features that became turned on by default in version 10.0.47. You can still turn these features off in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) if necessary.

| Module | Feature name | Feature state |
|--|--|--|
|Accounts receivable| Customer account renames data maintenance.| Mandatory|
|Accounts receivable |Free text invoice performance boost while loading.| Mandatory|
|Accounts receivable |Customer invoice logging framework for sales order and free text invoice history tracking. |Released|
|Accounts receivable| Add support for financial tags to the free text invoice entity within data management.| On by default|
|Accounts receivable| Enable data migration from timestate table to current table. (Preview) | Released|
| Budgeting |Enable non-retrievable purchase orders form for purchase year-end order process. |On by default  |
| Budgeting |Budget register entries form performance enhancement. | On by default   |
| Cash and bank management |Align time zone conversion in modern bank reconciliation. | On by default   |
| Cash and bank management | Automatic vendor account matching. | On by default   |
| Cash and bank management | Bank transactions page performance improvement. | On by default    | 
| Cash and bank management | Search for customer/vendor account ID when manual payment journal is created during bank reconciliation process.|  On by default |
|Credits and collections| Include Project and General journal invoices in Collections process automation.| On by default|
|Credits and collections |Customer aging performance enhancement with customer pools.| Mandatory|
|Credits and collections| Collections process automation track step enhancement.| On by default|
|Credits and collections | Aging snapshot performance improvement using pre-calculated sales total. (Preview)| Released|
|Credits and collections|Enable general journals parameter for interest calculation process.| On by default|
|Subscription billing |Use journal info from schedule line post-recognition. |Released|
|Subscription billing |Project subscription billing deferral COGS adjustment.(Preview) |Released|
|Subscription billing| Subscription billing deferral COGS adjustment. (Preview)| Released|
| Tax | Canadian harmonized sales tax rules.|  Mandatory  |
| Tax | Consistency check for Tax trans general journal account entry association for Bank exchange rate.|  Mandatory  |
| Tax | Enable "Include corrections" option on Sales tax settlement periods.|  On by default  |
| Tax | Enable reverse charge mechanism for VAT/GST scheme.|  Mandatory  |
| Tax | Reverse charge availability for additional countries.|  Mandatory  |
| Tax | (India) GST/TDS-TCS tax support for Project Integration Journal.|  Mandatory  |
| Tax | Sales tax settlement and reporting by date of VAT register.|  Mandatory  |
| Tax | Sales tax specification by **Purchase expenditure for product** posting type.|  On by default  |


## Features removed from feature management

The following table lists features that were removed from Feature management in version 10.0.47. These features are no longer listed in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) and are now a permanent part of Finance.

| Module | Feature name | More information |
|---|---|---|
|Accounts receivable| Use percentage in parameter to calculate batch tasks for the customer aging snapshot |Remove or obsolete feature|
|Accounts receivable |Custom search on customer page |Remove or obsolete feature|
| Budgeting |Default the account structure in the budget register entry | The related functionality is enabled out of the box | 
| Budgeting |Reverse preliminary budget with today's date |The related functionality is enabled out of the box | 
| Cash and bank management |Enable batch mode for "Mark as reconciled" in advance bank reconciliation| The related functionality is enabled out of the box | 
| Cash and bank management |Foreign Currency Revaluation performance Improvements |The related functionality is enabled out of the box |
|Credits and collections| This feature enables multi-threading when creating collection letters in batch |Remove or obsolete feature|
|Credits and collections| Collections process automation| Remove or obsolete feature|
|Credits and collections| Use the transaction date as the basis when calculating interest using ranges| Remove or obsolete feature|
|Credits and collections| (Italy) Separate accounts for credit notes| Remove or obsolete feature|
|Credits and collections| Default dimensions for write-off account from original invoice's revenue account| Remove or obsolete feature|
|Credits and collections| Customer interest notes creation process performance improvement |Remove or obsolete feature|
|Credits and collections| Prevent update picking quantity and release to warehouse if a sales order is on credit hold |Remove or obsolete feature|
|Credits and collections| Credit management| Remove or obsolete feature|
|Credits and collections| Intercompany sales order exclusion from credit management |Remove or obsolete feature|
|Credits and collections| Customer balance statistics deletion job | Remove or obsolete featur|e
| Tax |Keep GST tax document for confirmation journal |The related functionality is enabled out of the box |
| Tax |(Brazil) Dual base calculation for ICMS-DIFAL in sales transactions |The related functionality is enabled out of the box |
| Tax |(India) Enable the default assessable value of BOE calculated proportionally |The related functionality is enabled out of the box |
| Tax |Tax in transfer order |The related functionality is enabled out of the box |
| Tax |Support multiple VAT registration numbers |The related functionality is enabled out of the box |


## More information

### Platform updates for finance and operations apps

Dynamics 365 Finance version 10.0.47 includes platform updates. To learn more, see 
[Platform updates for version 10.0.47 of finance and operations apps](../../fin-ops-core/fin-ops/get-started/whats-new-platform-updates-10-0-47.md).

### Bug fixes

For information about the bug fixes that are included in this update, sign in to Microsoft Dynamics 365 Lifecycle Services, and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=xxxxx).

### Regulatory updates

For information about regulatory updates for finance and operations apps, see [Regulatory updates](../localizations/regulatory-updates.md). Another way to learn about regulatory updates is to sign in to Lifecycle
Services and view the planned regulatory updates using the issue search tool. Issue search lets you search by country/region, type of feature, and release.


### Dynamics 365 and industry clouds: 2025 release wave 2 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out [Dynamics 365 and industry clouds: 2025 release wave 2 plan](/dynamics365/release-plan/2025wave2/). We've captured all the details, end to end, top to bottom, that you can use for planning.





