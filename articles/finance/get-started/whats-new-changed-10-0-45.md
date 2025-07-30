---
title: What's new or changed in Dynamics 365 Finance 10.0.45 (September 2025)
description: Learn about features that are either new or changed in the Microsoft Dynamics 365 Finance version 10.0.45 preview release.
author: twheeloc
ms.author: twheeloc
ms.topic: whats-new
ms.date: 07/28/2025
ms.update-cycle: 1095-days
ms.custom:   
  - bap-template
  - evergreen
ms.reviewer: twheeloc
ms.search.region: Global
---

# What's new or changed in Dynamics 365 Finance 10.0.45 (September 2025)

[!include [banner](../includes/banner.md)]
[!include [banner](../includes/preview-banner.md)]

This article lists the features that are new or changed for Microsoft Dynamics 365 Finance version 10.0.45. This version has a build number of 10.0.2345 and is available on the following schedule:

- **Preview of release:** July 2025
- **General availability of release (self-update):** September 2025
- **General availability of release (auto-update):** October 2025

## Features included in this release
This section contains a table that lists the features that are included in this release when available. We might update this article to include features that were added to the build after this article was originally published.

| Module or feature area | Feature name | More information | Enabled by |
|---|---|---|---|
|Account receivable| Customer invoice logging framework for sales order and free text invoice history tracking 	(Preview)	|This feature introduces a structured logging framework to track the lifecycle of customer invoice documents, including sales orders and free text invoices. The logged data supports a detailed posting history in the **Customer invoice** workspace, improving traceability and diagnostics. The tab pages on the **Customer invoicing** workspace remain unchanged before and after enabling this feature. Users can now view detailed error messages for sales orders that failed during the posting process. The **Sales order posting history** and **Free text invoice posting history** tabs continue to display data for the past 14 days by default. |Feature management|
|Asset leasing|  Workflow for lease impairment | This feature enables a new workflow for the lease impairment process by adding a **Submit** button to the right-of-use asset impairment dialogue. A new **Lease impairment** page is introduced that allows users to continue the impairment process after the record has been approved in the workflow. |Feature management|
|Asset leasing|  Asset leasing journal description | This feature prevents posting the asset leasing journal without a mandatory description.| Mandatory|
|Asset leasing  | Lease termination triggers fixed asset posting  | This feature automates the posting of lease termination transactions to the fixed assets subledger. |Mandatory|
| Cash and bank management | Automatic vendor account matching | When the feature is enabled, the **Generate vendor payment** bank reconciliation rule allows for auto search of vendor account based on the match of International Bank Account Number (IBAN) and bank account number fields in vendor master data with the information on bank statement lines. If matching is successful, the relevant vendor account is used to post the vendor payment journal. | Feature management |
| Cash and bank management | Optimized auto settlement | This feature optimizes auto settlement process performance for customer and vendor transactions by addressing inefficiencies in handling multiple open transactions and reducing the number of database calls. | Feature management |
| Electronic reporting (ER) | In-app PDF conversion for configurable business documents (CBD) | This Electronic reporting (ER) feature enables in-app PDF conversion of configurable business documents in Word and Excel formats using AOS resources, allowing complete processing within the application and eliminating reliance on external services. | Feature management |
| Electronic reporting (ER) | Suppress forced batch job retries on failure for Electronic reporting | When the feature enabled, further batch job retries are suppressed for failed Electronic reporting jobs. | Feature management |
| Electronic reporting (ER) | Validate obsolete elements of Electronic reporting data sources | Validate obsolete elements of Electronic reporting data sources during configuration validation so you can adjust the configuration to address that | Default |
| Electronic reporting (ER) | Enhanced access to labels of the ascendent Electronic reporting data model | This feature enables access to labels of an ascendent Electronic reporting data model in derived Electronic reporting format components. | Default|
| Electronic reporting (ER) | Enable support of Document routing agent running as a service | Enable support of Document routing agent running as a service for network printing scenarios of outbound documents. The Document routing agent lets you select the mode of execution. The process can run either as a desktop application or as a Windows service. For more information, see [Run the Document routing agent as a Windows service](../../fin-ops-core/dev-itpro/analytics/run-document-routing-agent-as-windows-service.md). | Default |
| Electronic reporting (ER) | Apply the **Language preference** parameter to the 'File name' expression | Enables Electronic reporting formats to dynamically compute file names based on the selected language preference, improving localization in outbound file generation. | Default |
| Electronic reporting (ER) | Run Electronic reporting import of manually uploaded documents in batch | The feature provides the possibility to run the Electronic reporting (ER) framework model mapping for importing manually uploaded documents in batch. | Default|
| Electronic reporting (ER) | Forcing to use for data parsing only cell data types that are defined in an Electronic reporting format | When you enable this feature, the Electronic reporting (ER) framework uses for data parsing only cell data types that are defined in an Electronic reporting format. When this feature is disabled, Electronic reporting tries to recognize cell data types based on values of cells of an inbound file in Excel format. | Default|
| Electronic reporting (ER) | Cache the preferred language of the current user for Electronic reporting runs | Enable this feature to cache preferred language of the current user for a single run of an Electronic reporting (ER) format to improve execution performance. | Default |
| Electronic reporting (ER) | Accelerate Electronic reporting ER labels storage | This feature introduces a new label storage schema for imported Electronic reporting configurations to improve performance during editing and execution. Applies to newly added configurations; existing ones require a manual conversion after enabling the feature. | Mandatory |
| Electronic reporting (ER) | Minimize memory consumption by storing datasets at Electronic reporting reports runtime | Enabling this feature reduces the size of cached application data by storing the only values of fields that are actually used for report’s generation during an Electronic reporting (ER) format execution. | Mandatory |
| Electronic reporting (ER) | Optimize datasets memory consumption at Electronic reporting reports runtime | Enabling this feature reduces the number of cursors for fetching application data by releasing cursors as soon as they become unnecessary, not at the end of the current session of an Electronic reporting (ER) format execution. | Mandatory |
|Fixed assets|  Split and transfer fixed assets between legal entities (Preview) | This feature allows users to split and transfer assets between legal entities by selecting the source assets and their books, previewing key financial details such as acquisition cost, accumulated depreciation, and net book value. Users can transfer the source asset's acquisition cost and accumulated depreciation or use its net book value, and either automatically create the destination asset or select an existing one.| Feature management|
|Fixed assets |  Unified posting dates for asset catch-up depreciation (Preview)  | This feature enables users to specify a posting date during the depreciation proposal process, ensuring consistent posting dates for catch-up depreciation transactions. |Feature management|
|Fixed assets |  Fixed assets proposal |This feature creates both acquisition and depreciation proposals from a centralized proposal page, allowing for streamlined asset-related decision-making. |Feature management|
|General ledger |  Reverse out of balance ledger settlements  |  Use the **Out of balance ledger settlements** page to automatically reverse any ledger settlements that are out of balance. A year-end close can't be completed successfully if there are any ledger settlements that aren't balanced. Out of balance ledger settlements happen when they cross fiscal years or if no realized gain or loss was created when settled. For more information, see [Out of balance ledger settlements](https://go.microsoft.com/fwlink/?linkid=2329226).  | Default|
|General ledger|   Check for highly variable dimensions   | The **Check for highly variable dimensions** enables a process to count of dimensions to detect highly variable dimensions. When there are highly variable dimensions the performance of the year-end close, trial balance, and consolidations can be impacted. Two data maintenance tasks run to detect the dimension counts and are then displayed in the **Year end close** page. Submit a support request to enable the flight for this feature. For more information, see [Highly variable dimensions](https://go.microsoft.com/fwlink/?linkid=2329640)  |  Flight|
| Globalization studio | Electronic reporting globalization feature JSON import/export | This feature enables the JSON import/export function for Electronic reporting globalization features. It allows users to import new features from JSON files and export their features into JSON files for storage and transfer purposes. | Feature management |
| Globalization Studio | Dataverse repository | This feature enables the Dataverse-based repositories for Electronic reporting configurations and Globalization features. | Mandatory |
| Globalization Studio | Electronic reporting globalization feature Key Vault parameters | This feature enables a new Key vault parameters page that allows you to set up secrets and certificates stored in Microsoft Azure using service application-based authentication in order to connect to it. | Mandatory |
|Subscription billing |	Backfill journal information for deferral schedule lines from LedgerJournalTrans |	This task involves backfilling the Voucher, JournalNum, and TransDate fields in the SubBillDeferralScheduleLine table by referencing corresponding data from the LedgerJournalTrans table. The objective is to ensure data consistency and completeness by establishing accurate journal linkage for each deferral schedule line.  |	Data maintenance |
|Subscription billing (Preview) |Subscription billing deferral COGS adjustment|	This feature automatically adjusts the Cost of Goods Sold (COGS) for subscription billing deferral schedules. It works through a background automation process. When the inventory closing or recalculation process runs, the related consumption deferral schedules are updated to reflect any changes in the original cost. These updates happen asynchronously and follow an eventually consistent model.  |	Feature management|
|Subscription billing	(Preview) |Project subscription billing deferral COGS adjustment|	This feature enables COGS adjustment functionality for projects related subscription billing deferral schedules. When the inventory recalculation process is run, the associated consumption deferral schedules are updated to reflect any adjustment to the original cost. |	Feature management|




## Feature enhancements included in this release

This section contains a table that lists the enhancements that are included in this release when available. We might update this article to include features that were added to the build after this article was originally published.

| Module or feature area | Feature name | More information | Enabled by |
|---|---|---|---|
|Accounts receivable|	Accounts receivable|	When a free text invoice is created and posted, the posted invoice journal total is incorrect where the calculation isn't considering all total lines amount. Although the Ledger entries are correct but Custtrans amounts and CustInvoiceJour are incorrect.	|Feature management|
|Accounts receivable|	Accounts receivable|	Invoice and invoice line details information in the **Associations** FastTab in **My cases** page. |	Feature management|
| Cash and bank management | Modern bank reconciliation | Unintended matches between bank statement and bank transactions are prevented, unless explicitly defined and configured on the reconciliation rule. | Feature management |
| Cash and bank management | Modern bank reconciliation | When the feature is enabled, customer and vendor bank accounts are automatically found when manual payment journal is created during bank reconciliation process. The suggestion of customer or vendor account is based on bank account number, IBAN, or trading party name available on the bank statement line. | Feature management |
|Credit and collections	|Accounts receivable	|The user should be able to view and select the option for the due date and the terms of payment while posting a customer interest note.|	Feature management|
|Credit and collections|	Accounts receivable|	Email template on the collection process automation uses the variables on the Subject line.	|Feature management |
|Fixed assets |  Asset split logic independent of labels |  The feature involves researching and refactoring code paths that rely on localized labels for the split fixed asset process. It transitions from using labels to using a split subtype, ensuring that the logic is based on stable and consistent criteria. This change addresses issues where user-modifiable labels could cause unexpected behavior in the system.|  |
|General ledger| Validate year-end close enhanced |  When running the **Validate year-end close** process additional checks are done with partial ledger settlements. |  Default|
|General ledger | Ledger settlements audit trail includes description and reason | On the **Ledger settlements** page, the **Description** column displays the description from the original transaction. The **Reason** column displays the comment entered for the ledger settlement. The **Ledger settlements inquiry** page also displays both the **Description** and **Reason** columns.|  Default|
|General ledger |LedgerTransSettlementEntity V2 | When partial ledger settlements is enabled, a new entity is used for export/import in Ledger settlements. The marked column required a new entity when using partial ledger settlements. | Default|
|Subscription billing	|Subscription billing|	At the termination of billing schedule, a credit note is created against the invoices (sales orders) with the same exchange rate used at the time of invoicing.|	Feature management|

## Features turned on by default in this release

The following table lists the features that are turned on by default in version 10.0.45. Most features that have been turned on can be turned off in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md). 

| Feature name | Feature state | Module |
|--------------|---------------|--------|
|Custom search on the customer page|	Mandatory|	Accounts receivable|
|Copy financial dimensions from sales order header to penny difference voucher transaction|	On by default|	Accounts receivable|
|Add support for financial tags to the free text invoice entity within data management|	Released|	Accounts receivable|
| Mark all bank transactions as cleared in account reconciliation | On by default | Cash and bank management |
| Enable prepayment and posting profile when generating payment journal in advanced bank reconciliation | On by default | Cash and bank management |
| Payment journal cancellation from bank reconciliation worksheet | On by default | Cash and bank management |
| Enable offset account financial dimensions for general ledger voucher posting during bank account reconciliation | On by default | Cash and bank management |
| Use latest exchange rate to post bank transactions | On by default | Cash and bank management |
| Enable default descriptions for advanced bank reconciliation | On by default | Cash and bank management |
|Separate accounts for credit notes|	Mandatory	|Credits and collections|
|Automate split transaction posting from main book to derived books|	On by default	|Fixed assets|
|Propagate the **Allow depreciation when placed in service and disposal are in the same fiscal year** from fixed asset parameters for all newly created asset books|	On by default|	Fixed assets|
|Prevent overriding the account on a vendor invoice when creating a fixed asset|	On by default	|Fixed assets|
|Create separate voucher number for journals line related to automatic depreciation adjustment, split transactions, and split disposal|	Mandatory	|Fixed assets|
|Prevent fixed asset acquisition from project purchase  orders when business rules for fixed assets determination are configured	|Mandatory|	Fixed assets|
|Japan localization - Break up split transactions by year	|Mandatory	|Fixed assets|
|Adjust sales tax amount per vendor charged sales tax	|On by default	|Tax|
|Enable adding and synchronizing of tax hierarchy version in batch mode	|On by default	|Tax|
|Copy tax registration number as default tax exempt number |On by default	|Tax|
|Enable external tax solution providers for Tax Calculation |Mandatory |Tax|


## Features removed from Feature management

The following table lists the features that were removed from Feature management in version 10.0.45.

| Feature name | Feature state | Module |
|--------------|---------------|--------|
| Extended look up of Electronic reporting format configurations allowing to inquire the Global repository | The related functionality is enabled out of the box. | Electronic reporting (ER) |
| Globalization Studio | The related functionality is enabled out of the box. | Globalization Studio |
| E-invoicing service workspace designer | The related functionality is enabled out of the box. | Globalization Studio |
| Utilize application resources to perform CBD documents conversion from Word to PDF format | Disabled in Feature management due to replacement by In-App PDF conversion for Configurable Business Documents (CBD) | Electronic reporting (ER) |
|Selection of advance invoices for reversing while posting sales order credit note | Remove or obsolete feature |	Accounts receivable|
|(Lithuania) Don't add the VAT keyword to the beginning of the invoice title| Remove or obsolete feature | Accounts receivable|
| Control zero-amount sales tax difference entries for Czech Republic (CZ) | The related functionality is enabled out of the box | Tax |
| Separate sales tax payment report generation from sales tax settlement | The related functionality is enabled out of the box | Tax |
| Populate financial dimensions to the realized currency adjustment profits/loss accounts for sales tax settlement | The related functionality is enabled out of the box | Tax |
| Sales tax rate on invoice date in purchase order credit note | The related functionality is enabled out of the box | Tax |



## More information

### Platform updates for finance and operations apps

Dynamics 365 Finance version 10.0.45 includes platform updates. To learn more, see [Platform updates for version 10.0.45 of finance and operations apps](../../fin-ops-core/fin-ops/get-started/whats-new-platform-updates-10-0-45.md).

### Bug fixes

For information about the bug fixes that are included in this update, sign in to Microsoft Dynamics 365 Lifecycle Services, and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=1043223).

### Regulatory updates

For information about regulatory updates for finance and operations apps, see [Regulatory updates](../localizations/regulatory-updates.md). Another way to learn about regulatory updates is to sign in to Lifecycle 
Services and view the planned regulatory updates using the issue search tool. Issue search lets you search by country/region, type of feature, and release.

### Dynamics 365 and industry clouds: 2025 release wave 1 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out [Dynamics 365 and industry clouds: 2025 release wave 1 plan](/dynamics365/release-plan/2025wave1/finance-supply-chain/dynamics365-finance). We've captured all the details, end to end, top to bottom, that you can use for planning.

