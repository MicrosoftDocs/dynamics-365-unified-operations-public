---
title: What's new or changed in Dynamics 365 Finance 10.0.46 (December 2025)
description: Learn about features that are either new or changed in the Microsoft Dynamics 365 Finance version 10.0.46 preview release.
author: twheeloc
ms.author: twheeloc
ms.topic: whats-new
ms.date: 10/24/2025
ms.update-cycle: 1095-days
ms.custom:   
  - bap-template
  - evergreen
ms.reviewer: twheeloc
ms.search.region: Global
---

# What's new or changed in Dynamics 365 Finance 10.0.46 (December 2025) 

[!include [banner](../includes/banner.md)]
[!include [banner](../includes/preview-banner.md)]

This article lists the features that are new or changed for Microsoft Dynamics 365 Finance version 10.0.46. This version has a build number of 10.0.2428 and is available on the following schedule:

- **Preview of release:** October 2025
- **General availability of release (self-update):** December 2025
- **General availability of release (auto-update):** February 2026

## Features included in this release
This section contains a table that lists the features that are included in this release when available. We might update this article to include features that were added to the build after this article was 
originally published.

| Module or feature area | Feature name | More information | Enabled by |
|---|---|---|---|
|Accounts receivable|	(Switzerland) Structured addresses in QR-Bill|	This feature enables structured addresses (address type “S”) for both biller and debtor, with each address broken into its individual components. |	Feature management|
|Accounts receivable|	Performance issue on the **Global transaction** page with huge volume of data|	This feature improves performance issue in **Global transaction** page by changing the join type dynamically to inner.|	On by default |
|Fixed assets | Create acquisition proposal through recurrence batch job throws error in batch tasks when the created journal is deleted | This update addresses a scenario where the recurrence batch job for creating acquisition proposals fails with an error in batch tasks if the journal created by a previous run is manually deleted. Validation has been added to detect missing journals and handle the error gracefully, ensuring the batch job continues to run without interruption. | On by default |
|Fixed assets | Retain fixed asset name when acquired through Accounts payable invoice | This feature ensures that the text defined in the **Text** field of a purchase order line for a fixed asset is stored in the **Information 3** field during asset creation and remains unchanged. If the asset is later acquired through additional purchase orders with new text, the new values are appended to the **Information 3** field without removing the existing ones. | On by default|
|Fixed assets | Correct inventory sold transaction behavior when **Allow asset acquisition from purchasing** is disabled |When acquiring the same fixed asset ID from multiple purchase lines, the Inventory sold transaction is now created when posting the fixed asset acquisition proposal journal. This ensures transactions are generated at the correct stage of the process and prevents premature entries.| On by default|
|Fixed assets | (Preview) Data entity for transfer worksheet |This feature introduces a data entity that supports the fixed asset transfer between legal entities worksheet process. It enables users to programmatically manage asset transfers between legal entities by importing transfer data, including source asset details, financial values, and destination asset data. | Flight |
|Subscription billing|	Reduce chattiness in SubBillDeferralRecognitionProcessing and SubBillDeferralRecognitionProcessingBatch| This change successfully reduced a significant amount of chattiness in the batch process. This is controlled by SubBillDeferralRecogProcChattinessReductionFlight	|On by default|
|Subscription billing	 | Fix generate invoice with sales order performance problems|	This introduced a posting sales order batch job for billing schedule invoicing batch processing for the sales order posting process. This enables multithreaded posting resulting in parallelism and faster execution time. This is controlled by SubBillGenerateInvoiceMultiThreadedPostingFlight|	On by default|
|Subscription billing	|(Preview) Performance improvements for deferral recognition batch|	This feature enhances the subscription billing deferral recognition batch process by processing deferral data in parallel, allowing each run to complete more efficiently.|	Feature management|


## Feature enhancements included in this release

This section contains a table that lists the enhancements that are included in this release when available. We might update this article to include features that were added to the build after this article was originally published.

| Module or feature area | Feature name | More information | Enabled by |
|---|---|---|---|
| General ledger | Account reconciliation agent (Production ready preview) | The Account reconciliation agent functionality has been improved to provide suggested actions for **In ledger not in subledger** and **In subledger not in ledger** exception types.| Feature management |
| General ledger |User ID added to the **Ledger settlement inquiry** page for full visibility. The **User ID** is now in the **Ledger settlement inquiry** page. |The user ID that did the ledger settlement is now displayed in the **Ledger settlement inquiry** page. | Default |
| General ledger |Performance improvements in Ledger settlements when the **Enable advanced awareness option** feature isn't enabled. | The **Ledger settlements** page has been updated to improve the performance when doing ledger settlements. Customizations may need to be updated to work with the new page. | Default |
 |Subscription billing	 |Subscription billing	 |The discount group setup in the trade agreement for item prices should automatically apply to the billing schedule when it is created for the corresponding customer record.  |	Feature management |
 |Subscription Billing	 |(Preview) Subscription billing deferral COGS adjustment-Enhancement | A dedicated dashboard monitors and provides visibility into errors that had occurred during the adjustment process. This dashboard offers actionable insights and a user-friendly interface, allowing users to conveniently reprocess failed adjustments through a rerun batch job—reducing manual effort and enhancing the overall reliability of the deferral.  |	Feature Management |
 |Subscription billing |	 (Preview) Subscription billing deferral COGS adjustment-Enhancement |	A notification message is displayed when the asynchronous process finishes so that the user is notified. |	Feature management |
 |Subscription billing |	Subscription billing |	At the termination of billing schedule, a credit note is created against the invoices (sales orders) with the same exchange rate used at the time of invoicing. |	Feature management |
 |Accounts receivable |	Accounts receivable |	When a free text invoice is created and posted, the posted invoice journal total is incorrect where the calculation doesn't consider all total lines amount. The Ledger entries are correct but the Custtrans and CustInvoiceJour amounts are incorrect. |	Feature management |
 |Accounts receivable |	Accounts receivable	Invoice and Invoice line details information on the **Associations** FastTab on **My cases** page.  |Feature management |
 |Credit and collections |	Accounts receivable |	The user should be able to view and select the option for the **Due date** and the **Terms of payment** when posting a customer interest note. |	Feature management |
 |Credit and collections |	Accounts receivable |	Email template on the collection process automation uses the variables on the **Subject** line. |	Feature management |
 |Credit and collections |Customer interest note creation – top picking optimization |This feature uses top picking to improve the performance when creating customer interest notes. This helps avoid long-running transactions and ensures faster and more efficient processing when handling large transaction volumes. | Feature management |


## Features turned on by default in this release

The following table lists the features that are turned on by default in version 10.0.46. Most features that have been turned on can be turned off in
[Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md). 

| Feature name | Feature state | Module |
|--------------|---------------|--------|
|Custom search on **Customer** page	|Mandatory	|Accounts receivable|
|Copy financial dimensions from sales order header to penny difference voucher transaction|	On by default|	Accounts receivable|
|Add support for financial tags to the free text invoice entity within data management	|Released	|Accounts receivable|
|Separate accounts for credit notes|	Mandatory|	Credits and collection|


## More information

### Platform updates for finance and operations apps

Dynamics 365 Finance version 10.0.46 includes platform updates. To learn more, see 
[Platform updates for version 10.0.46 of finance and operations apps](../../fin-ops-core/fin-ops/get-started/whats-new-platform-updates-10-0-46.md).

### Bug fixes

For information about the bug fixes that are included in this update, sign in to Microsoft Dynamics 365 Lifecycle Services, and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=1070810).

### Regulatory updates

For information about regulatory updates for finance and operations apps, see [Regulatory updates](../localizations/regulatory-updates.md). Another way to learn about regulatory updates is to sign in to Lifecycle
Services and view the planned regulatory updates using the issue search tool. Issue search lets you search by country/region, type of feature, and release.

### Dynamics 365 and industry clouds: 2025 release wave 2 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out [Dynamics 365 and industry clouds: 2025 release wave 2 plan](/dynamics365/release-plan/2025wave2/). We've captured all the details, end to end, top to bottom, that you can use for planning.


