---
title: What's new or changed in Dynamics 365 Finance 10.0.46 (December 2025)
description: Learn about features that are either new or changed in the Microsoft Dynamics 365 Finance version 10.0.46 preview release.
author: twheeloc
ms.author: twheeloc
ms.topic: whats-new
ms.date: 12/17/2025
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
| Cash and bank management | Display payee name for customer/vendor payment information | This feature enables the retrieval and display of the payee name defined on the customer and vendor bank account details. The payee name will be visible in customer and vendor payment journals, payment proposals, and outbound payment files. The payee name can be different from the name of the customer/vendor defined on the master data, and should align with banking requirements, ensuring accurate identification of payment recipients. | Feature management |
| Cash and bank management | Enable batch mode for Bank CODA transfer to ledger |When the feature is enabled, users can transfer Bank CODA account statements to ledger journals in batch.| Feature management |
| Cash and bank management | Automatic bank reconciliation matching results (Preview) | This feature is released in private preview allowing its usage in nonproduction environments. The **Preview automatic bank reconciliation matching results** feature enables users to preview matching results during the bank reconciliation matching process before transactions are posted. By allowing users to select rules that require review and user checks, the feature ensures accurate matching and minimizes errors. To enable this feature, contact support. | Feature management |
| Cash and bank management | Delay invoice settlement (Preview) | This feature is released in private preview without the ability to enable it in production environments. The feature controls the **Delayed settlement** parameter in General Ledger journal names. When the feature and parameter are enabled, the settlement is delayed and is executed separately from posting the customer and vendor payment journals. To enable this feature, contact support.  | Feature management |
|Fixed assets | Create acquisition proposal through recurrence batch job throws error in batch tasks when the created journal is deleted | This update addresses a scenario where the recurrence batch job for creating acquisition proposals fails with an error in batch tasks if the journal created by a previous run is manually deleted. Validation has been added to detect missing journals and handle the error gracefully, ensuring the batch job continues to run without interruption. | On by default |
|Fixed assets | Retain fixed asset name when acquired through Accounts payable invoice | This feature ensures that the text defined in the **Text** field of a purchase order line for a fixed asset is stored in the **Information 3** field during asset creation and remains unchanged. If the asset is later acquired through additional purchase orders with new text, the new values are appended to the **Information 3** field without removing the existing ones. | On by default|
|Fixed assets | Correct inventory sold transaction behavior when **Allow asset acquisition from purchasing** is disabled |When acquiring the same fixed asset ID from multiple purchase lines, the Inventory sold transaction is now created when posting the fixed asset acquisition proposal journal. This ensures transactions are generated at the correct stage of the process and prevents premature entries.| On by default|
|Fixed assets | Data entity for transfer worksheet (preview) |This feature introduces a data entity that supports the fixed asset transfer between legal entities worksheet process. It enables users to programmatically manage asset transfers between legal entities by importing transfer data, including source asset details, financial values, and destination asset data. | Flight |
|Subscription billing|	Reduce chattiness in SubBillDeferralRecognitionProcessing and SubBillDeferralRecognitionProcessingBatch| This change successfully reduced a significant amount of chattiness in the batch process. This is controlled by SubBillDeferralRecogProcChattinessReductionFlight	|On by default|
|Subscription billing	 | Fix generate invoice with sales order performance problems|	This introduced a posting sales order batch job for billing schedule invoicing batch processing for the sales order posting process. This enables multithreaded posting resulting in parallelism and faster execution time. This is controlled by SubBillGenerateInvoiceMultiThreadedPostingFlight|	On by default|
|Subscription billing	|Performance improvements for deferral recognition batch (preview) |	This feature enhances the subscription billing deferral recognition batch process by processing deferral data in parallel, allowing each run to complete more efficiently.|	Feature management|
|Subscription billing	| Performance improvement in deferral processing | Key performance improvements are introduced in Subscription Billing deferral processing. These enhancements are designed to address critical business challenges observed in high-volume deferral scenarios and to improve overall reliability and scalability of the batch process.| On by default |
|Regulatory reporting	| [Withholding tax report for Indonesia](../localizations/indonesia/apac-idn-wht-declaration.md) |	Support generating the e-Bupot file for reporting periods starting from 2025 based on the withholding tax transactions.|	Electronic Reporting configurations |
|Regulatory reporting	| [VAT (Pajak Pertambahan Nilai) declaration for Indonesia](../localizations/indonesia/apac-idn-ppn-declaration.md) |	Support generating the SPT Masa PPN (Pajak Pertambahan Nilai) in Excel format for reporting periods starting from 2025.|	Electronic Reporting configurations |
|Regulatory reporting	| [VAT declaration for Estonia - KMD5, KMD6](../localizations/estonia/emea-est-vat-declaration.md) |	Support generating the VAT declaration for Estonia - KMD5 for reporting periods from January to June 2025, KMD6 for reporting periods starting from July 2025.|	Electronic Reporting configurations |


## Feature enhancements included in this release

This section contains a table that lists the enhancements that are included in this release when available. We might update this article to include features that were added to the build after this article was originally published.

| Module or feature area | Feature name | More information | Enabled by |
|---|---|---|---|
| Cash and bank management | Bank account lifecycle management | As of Dynamics 365 Finance version 10.0.46, this feature isn't in Preview. Bank account lifecycle management feature enables approval workflow for bank account opening, modification and closing, adds additional signer information in the bank account data model, and provides bank account change history for auditing purpose. | Feature management |
| Cash and bank management | Modern bank reconciliation | When the feature is enabled, sales tax direction is considered when the general ledger voucher is generated during bank reconciliation process. | Feature management |
 |Credit and collections |Customer interest note creation – top picking optimization |This feature uses top picking to improve the performance when creating customer interest notes. This helps avoid long-running transactions and ensures faster and more efficient processing when handling large transaction volumes. | Feature management |
| General ledger | Account reconciliation agent (Production ready preview) | The Account reconciliation agent functionality has been improved to provide suggested actions for **In ledger not in subledger** and **In subledger not in ledger** exception types.| Feature management |
| General ledger |User ID added to the **Ledger settlement inquiry** page for full visibility. |The user ID that did the ledger settlement is now displayed in the **Ledger settlement inquiry** page. | Default |
| General ledger |Performance improvements in Ledger settlements when the **Enable advanced awareness option** feature isn't enabled. | The **Ledger settlements** page has been updated to improve the performance when doing ledger settlements. Customizations may need to be updated to work with the new page. | Default |
 |Subscription billing	 | Billing schedule	 |The discount group setup in the trade agreement for item prices should automatically apply to the billing schedule when it is created for the corresponding customer record.  |	Feature management |
 |Subscription billing	 |Subscription billing deferral COGS adjustment-enhancement (preview) | A dedicated dashboard monitors and provides visibility into errors that had occurred during the adjustment process. This dashboard offers actionable insights and a user-friendly interface, allowing users to conveniently reprocess failed adjustments through a rerun batch job—reducing manual effort and enhancing the overall reliability of the deferral.  |	Feature management |
 |Subscription billing |Subscription billing deferral COGS adjustment-enhancement (preview) |	A notification message is displayed when the asynchronous process finishes so that the user is notified. |	Feature management |
 |Regulatory reporting | \[Sweden\] Standard Import and Export (SIE) modernization in Electronic Reporting |	This feature replaces the legacy `SIE export format (SE)` format with the new `Standard Import and Export SIE TXT (SE)` format under the `Ledger accounting reports` model in Electronic Reporting. This new format enables the export of key financial data, including balances and transactions, in accordance with SIE Types 1 through 4. It supports larger datasets and introduces a redesigned export process that ensures faster generation, reduced system load, and a simplified workflow. By adopting this feature, Swedish entities can efficiently meet statutory reporting obligations while benefiting from a more scalable, performant, and maintainable export solution. [Export financial information (SIE) in Sweden](../localizations/sweden/emea-swe-sie-standard-report.md) |	Feature management |
 |Regulatory reporting | \(Preview\) \[Italy\] Fiscal Journal modernization in Electronic Reporting |	This feature replaces the legacy SSRS-based report with a modern, PDF-based solution built on Electronic Reporting. It offers improved performance, enhances the ability to process large volumes of data across extended reporting periods, including up to a full fiscal year, while ensuring compliance with Italian fiscal requirements. |	Feature management |
 |Regulatory reporting | Enhancement of Calculate statistics for [Payment terms in commercial transactions report for Poland](../localizations/poland/emea-pol-payment-terms-report.md) |	As of version 10.0.46 of Finance, the **Payment transaction type** parameter is available in the **Calculate statistics** dialog of **Statistics on invoices** process. This parameter allows selection of types of payment transactions to include in the statistics. |	Default |
 |Regulatory reporting | Define application of exchange rates in Intrastat reporting |	This feature introduces flexibility in how amounts are calculated for Intrastat, enabling alignment with tax calculation logic. [Intrastat overview - Foreign trade parameters](../localizations/europe/emea-intrastat.md#foreign-trade-parameters) |	Default |

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


