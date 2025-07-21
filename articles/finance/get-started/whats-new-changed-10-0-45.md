---
title: What's new or changed in Dynamics 365 Finance 10.0.45 (September 2025)
description: Learn about features that are either new or changed in the Microsoft Dynamics 365 Finance version 10.0.45 preview release.
author: twheeloc
ms.author: twheeloc
ms.topic: whats-new
ms.date: 07/25/2025
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

This article lists the features that are new or changed for Microsoft Dynamics 365 Finance version 10.0.45. This version has a build number of 10.0.XXXX and is available on the following schedule:

- **Preview of release:** July 2025
- **General availability of release (self-update):** September 2025
- **General availability of release (auto-update):** October 2025

## Features included in this release

| Module or feature area | Feature name | More information | Enabled by |
|---|---|---|---|
| Electronic reporting (ER) | In-App PDF conversion for configurable business documents (CBD) | This Electronic Reporting (ER) feature enables in-app PDF conversion of configurable business documents in Word and Excel formats using AOS resources, allowing complete processing within the application and eliminating reliance on external services. | Feature management |
| Electronic reporting (ER) | Suppress forced batch job retries on failure for Electronic reporting | When the feature enabled, further batch job retries are suppressed for failed Electronic reporting jobs. | Feature management |
| Globalization studio | Electronic reporting globalization feature JSON import/export | This feature enables the JSON import/export function for Electronic reporting globalization features. It allows users to import new features from JSON files and export their features into JSON files for storage and transfer purposes. | Feature management |
| Electronic reporting (ER) | Validate obsolete elements of Electronic reporting data sources | Validate obsolete elements of Electronic reporting data sources during configuration validation so you can adjust the configuration to address that | Default |
| Electronic reporting (ER) | Enhanced access to labels of the ascendent Electronic reporting data model | This feature enables access to labels of an ascendent Electronic reporting data model in derived Electronic reporting format components even when you selected for the derived Electronic reporting component an Electronic reporting data model that differs from the one that was used in the base Electronic reporting component. | Default|
| Electronic reporting (ER) | Enable support of Document routing agent running as a service | Enable support of Document routing agent running as a service for network printing scenarios of outbound documents. The Document routing agent lets you select the mode of execution. The process can run either as a desktop application or as a Windows service. For more information, see [Run the Document routing agent as a Windows service](../../fin-ops-core/dev-itpro/analytics/run-document-routing-agent-as-windows-service.md). | Default |
| Electronic reporting (ER) | Apply the **Language preference** parameter to the 'File name' expression | Enables Electronic reporting formats to dynamically compute file names based on the selected language preference, improving localization in outbound file generation. | Default |
| Electronic reporting (ER) | Run Electronic reporting import of manually uploaded documents in batch | The feature provides the possibility to run the Electronic reporting (ER) framework model mapping for importing manually uploaded documents in batch. | Default|
| Electronic reporting (ER) | Forcing to use for data parsing only cell data types that are defined in an Electronic reporting format | When you enable this feature, the Electronic reporting (ER) framework uses for data parsing only cell data types that are defined in an Electronic reporting format. When this feature is disabled, Electronic reporting tries to recognize cell data types based on values of cells of an inbound file in Excel format. | Default|
| Electronic reporting (ER) | Cache the preferred language of the current user for Electronic reporting runs | Enable this feature to cache preferred language of the current user for a single run of an Electronic reporting (ER) format to improve execution performance. | Default |
| Electronic reporting (ER) | Accelerate Electronic reporting ER labels storage | This feature introduces a new label storage schema for imported Electronic reporting configurations to improve performance during editing and execution. Applies to newly added configurations; existing ones require a manual conversion after enabling the feature. | Mandatory |
| Electronic reporting (ER) | Minimize memory consumption by storing datasets at Electronic reporting reports runtime | Enabling this feature reduces the size of cached application data by storing the only values of fields that are actually used for report’s generation during an Electronic reporting (ER) format execution. | Mandatory |
| Electronic reporting (ER) | Optimize datasets memory consumption at Electronic reporting reports runtime | Enabling this feature reduces the number of cursors for fetching application data by releasing cursors as soon as they become unnecessary, not at the end of the current session of an Electronic reporting (ER) format execution. | Mandatory |
| Globalization Studio | Dataverse repository | This feature enables the Dataverse-based repositories for Electronic reporting configurations and Globalization features. | Mandatory |
| Globalization Studio | Electronic reporting globalization feature Key Vault parameters | This feature enables a new Key vault parameters page which allows you to set up secrets and certificates stored in Microsoft Azure using service application-based authentication in order to connect to it. | Mandatory |
|Subscription billing |	Backfill journal information for deferral schedule lines from LedgerJournalTrans |	This task involves backfilling the Voucher, JournalNum, and TransDate fields in the SubBillDeferralScheduleLine table by referencing corresponding data from the LedgerJournalTrans table. The objective is to ensure data consistency and completeness by establishing accurate journal linkage for each deferral schedule line.  |	Data maintenance |
|Subscription billing (Preview) |Subscription billing deferral COGS adjustment|	This feature automatically adjusts the Cost of Goods Sold (COGS) for subscription billing deferral schedules. It works through a background automation process. When the inventory closing or recalculation process runs, the related consumption deferral schedules is updated to reflect any changes in the original cost. These updates happen asynchronously and follow an eventually consistent model.  |	Feature management|
|Subscription billing	(Preview) |Project subscription billing deferral COGS adjustment|	This feature enables COGS adjustment functionality for projects related subscription billing deferral schedules. When the inventory recalculation process is run, the associated consumption deferral schedules are updated to reflect any adjustment to the original cost. |	Feature management|
|Account receivable	(Preview)| Customer invoice logging framework for sales order and free text invoice history tracking	|This feature introduces a structured logging framework to track the lifecycle of customer invoice documents, including sales orders and free text invoices. The logged data supports a detailed posting history in the **Customer invoice** workspace, improving traceability and diagnostics. The tab pages on the **Customer invoicing** workspace remain unchanged before and after enabling this feature. Users can now view detailed error messages for sales orders that failed during the posting process. The **Sales order posting history** and **Free text invoice posting history** tabs continue to display data for the past 14 days by default. |Feature management|


## Feature enhancements included in this release

This section contains a table that lists the enhancements that are included in this release when available. We might update this article to include features that were added to the build after this article was originally published.

| Module or feature area | Feature name | More information | Enabled by |
|---|---|---|---|
|Subscription billing	|Subscription billing|	At the termination of billing schedule, a credit note is created against the invoices (sales orders) with the same exchange rate used at the time of invoicing.|	Feature management|
|Accounts receivable|	Accounts receivable|	When a free text invoice is created and posted, the posted invoice journal total is incorrect where the calculation isn't considering all total lines amount. Although the Ledger entries are correct but Custtrans amounts and CustInvoiceJour are incorrect.	|Feature management|
|Accounts receivable|	Accounts receivable|	Invoice and invoice line details information in the **Associations** fasttab in **My cases** page. |	Feature management|
|Credit and collections	|Accounts receivable	|The user should be able to view and select the option for the due date and the terms of payment while posting a customer interest note.|	Feature management|
|Credit and collections|	Accounts receivable|	Email template on the collection process automation uses the variables on the Subject line.	|Feature management |


## Features turned on by default in this release

The following table lists the features that are turned on by default in version 10.0.45. Most features that have been turned on can be turned off in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md). 

| Feature name | Feature state | Module |
|--------------|---------------|--------|
|Custom search on the customer page|	Mandatory|	Accounts receivable|
|Separate accounts for credit notes|	Mandatory	|Credits and collections|
|Copy financial dimensions from sales order header to penny difference voucher transaction|	On by default|	Accounts receivable|
|Add support for financial tags to the free text invoice entity within data management|	Released|	Accounts receivable|

## Features removed from Feature management

The following table lists the features that were removed from Feature management in version 10.0.45.

| Feature name | Feature state | Module |
|--------------|---------------|--------|
| Extended lookup of Electronic reporting format configurations allowing to inquire the Global repository | The related functionality is enabled out of the box. | Electronic reporting (ER) |
| Globalization Studio | The related functionality is enabled out of the box. | Globalization Studio |
| E-invoicing service workspace designer | The related functionality is enabled out of the box. | Globalization Studio |
| Utilize application resources to perform CBD documents conversion from Word to PDF format | Disabled in Feature management due to replacement by In-App PDF conversion for Configurable Business Documents (CBD) | Electronic reporting (ER) |
Selection of advance invoices for reversing while posting sales order credit note	Remove or obsolete feature	Accounts receivable
(Lithuania) Do not add the VAT keyword to the beginning of the invoice title	Remove or obsolete feature	Accounts receivable


## More information

### Platform updates for finance and operations apps

Dynamics 365 Finance version 10.0.45 includes platform updates. To learn more, see [Platform updates for version 10.0.45 of finance and operations apps](../../fin-ops-core/fin-ops/get-started/whats-new-platform-updates-10-0-45.md).

### Bug fixes

For information about the bug fixes that are included in this update, sign in to Microsoft Dynamics 365 Lifecycle Services, and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=xxxxx).

### Regulatory updates

For information about regulatory updates for finance and operations apps, see [Regulatory updates](../localizations/regulatory-updates.md). Another way to learn about regulatory updates is to sign in to Lifecycle 
Services and view the planned regulatory updates using the issue search tool. Issue search lets you search by country/region, type of feature, and release.

### Dynamics 365 and industry clouds: 2025 release wave 1 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out [Dynamics 365 and industry clouds: 2025 release wave 1 plan](/dynamics365/release-plan/2025wave1/finance-supply-chain/dynamics365-finance). We've captured all the details, end to end, top to bottom, that you can use for planning.






This section contains a table that lists the features that are included in this release when available. We might update this article to include features that were added to the build after this article was originally published.
