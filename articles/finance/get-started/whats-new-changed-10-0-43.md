---
title: What's new or changed in Dynamics 365 Finance 10.0.43 (January 2025)
description: Learn about features that are either new or changed in the Microsoft Dynamics 365 Finance version 10.0.42 preview release distributed in January 2025.
author: twheeloc
ms.author: twheeloc
ms.topic: faq
ms.date: 01/25/2025
ms.custom:   
  - bap-template
  - evergreen
ms.reviewer: twheeloc
ms.search.region: Global
---

# What's new or changed in Dynamics 365 Finance 10.0.43 (January 2025)

[!include [banner](../includes/banner.md)]
[!include [banner](../includes/preview-banner.md)]

This article lists the features that are new or changed for Microsoft Dynamics 365 Finance version 10.0.43. This version has a build number of 10.0.XXXX and is available on the following schedule:

- **Preview of release:** January 2025
- **General availability of release (self-update):** March 2025
- **General availability of release (auto-update):** April 2025

## Features included in this release

This section contains a table that lists the features that are included in this release when available. We might update this article to include features that were added to the build after this article was 
originally published.

| Module or feature area | Feature name | More information | Enabled by |
|---|---|---|---|
| Accounts receivable  |	Return order Invoice support through dual write |	Established new entities in Microsoft Dynamics 365 Finance and set up new mappings to synchronize return orders invoice from Microsoft Dynamics 365 Finance to customer environment. |   |
|Subscription billing|	Performance improvement for consumption quantity update	|This feature enhances recurring contract billing performance when the consumption quantity is updated on the billing detail line for a usage-based billing schedule line.|	 Feature management|

## Feature enhancements included in this release

This section contains a table that lists the enhancements that are included in this release when available. We might update this article to include features that were added to the build after this article was 
originally published.

| Module or feature area | Feature name | More information | Enabled by |
|---|---|---|---|
|Accounts receivable|	(Japan) Default value for the sales tax adjustment transaction posted in the consolidated invoice process	|Enabling this feature will set default value for method of payment, terms of payment and due date on the sales tax adjustment transaction during the posting for the consolidated invoice process in Accounts Payable and Account Receivable. For more information, see [Consolidate invoices](../localizations/japan/apac-jpn-consolidate-invoices.md#tax-adjustment-on-consolidated-invoice). |Feature management|
|Accounts receivable|	Removal of Duplicate and Overlapping Indexes|	Removal of Duplicate and overlapping Indexes has reduced the spacing issue in the database, hence, more efficiency	|   |
|Accounts receivable|	Financial Dimension Posting Error on Sales Order	|The feature ensures that the financial dimensions for automatic transactions inherit the financial dimensions from the sales order. This resolves the issue of posting into the rounding difference account from a sales order due to missing financial dimensions|	Feature management|
|Accounts receivable|	Improve the performance of settlement and selection of invoices for matching	|A performance improvement has been implemented to address the delay in enabling the post button during the settlement and selection of invoices for matching."	|  |
|Subscription billing|	Mass stubbing	|The Mass stubbing page is updated with **Add renewal term** to add a renewal term for usage billing schedule lines that are set to auto renew.|  |	
|Subscription billing|	Generate invoice	|Performance improvement when creating invoice proposal for billing schedule lines that are deferred.	| |
|Tax	|Enable applicability rules value lookup for Tax Calculation|	This feature enables applicability rules value lookup for Tax Calculation. User could select conditions value and output value by dropdown list instead of free text. It is controlled by “Enable lookups in applicability rules” parameter in Tax feature setup.|	Parameter|
|Tax	|Calculate GST based on invoice account |	The functionality is now controlled by the “Calculate GST based on invoice account” parameter in the Accounts payable parameters (under the Invoice FastTab of Invoice tab) and the Accounts receivable parameters (under the Invoice FastTab of the Updates tab).	|Parameter|
|Tax	|Tax calculation maintenance mode|	This functionality allows admin users to enable maintenance mode for the tax calculation feature. In this mode, if a draft version of the selected tax calculation feature exists, it will be used for tax calculations.|   | 
Important Note. The functionality is controlled by the flight: TaxIntegrationEnableMaintenanceModeFlight. It is recommended to use this mode in sandbox environments only.	
Tax	Withholding tax performance improvement	The performance of the withholding tax calculation process is improved when customer or vendor invoices are settled.	
|Tax calculation - Universal tax rate| API	Support setting up flexible fields label and help text	A new 'Sync Flexible Field Labels' API has been introduced in the tax feature. It allows independent software vendors (ISVs) to define flexible field labels and help text in multiple languages.	|   |
|Tax|	Interval tax calculation|	The “Interval” calculation method is now supported when the Enable advance tax calculation parameter is enabled in the Tax calculation parameters.	|   |
|Tax|	Advance invoices for Eastern Europe integration	|Tax calculation is supported in the Advance invoices when the Journal business process is enabled on the Tax calculation parameters page.|	Parameter|
|Tax	|Interest note and Collection letter integration| 	Tax calculation is supported in the Interest note and Collection letter journal when the Interest and Collection business process is enabled on the Tax calculation parameters page.|	Parameter|


## Features turned on by default in this release

The following table lists the features that are turned on by default in version 10.0.43. Most features that have been turned on atomically can be turned off in 
[Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md). In the future, some features that have been turned on automatically might be removed from Feature 
management and will become mandatory. This change ensures that customers are using current functionality, so that as enhancements are added, they can build on the current functionality. Features will never be 
automatically enabled in less than one year, unless they are determined to be essential.

| Feature name | Feature state | Module |
|--------------|---------------|--------|
|Enable exchange rate types for sales tax|	On by default|	Tax |
|Packing slip date as the delivery date for the advanced Tax Calculation (tax rate determination)|	On by default|	Tax|
|Selection of advance invoices for reversing while posting sales order credit note|	Mandatory|	Accounts receivable|
|(Lithuania) Do not add the VAT keyword to the beginning of the invoice title	|Mandatory	|Accounts receivable|
| Enable tax adjustment on consolidated invoice for Japan|	On by default|	Accounts receivable|


## Features removed from Feature management

The following table lists the features that have been removed from Feature management in version 10.0.43.

| Feature name | Feature state | Module |
|--------------|---------------|--------|
|Tax setup validation	|The related functionality is enabled out of the box.|	Tax|
|Enable Globalization feature setup for Tax Calculation Service	|The related functionality is enabled out of the box.	|Tax|
|Tax in transfer order|	The related functionality is enabled out of the box.|	Tax|
|Deprecated Obsolete code for Shared Accounts Receivable/ Accounts Payable Invoicing Localization|	The related functionality is enabled out of the box.|	Accounts receivable|
|Deprecated Obsolete code for Accounts Receivable|	The related functionality is enabled out of the box.|	Accounts receivable|
|(Mexico) Add fields for customs information into the free text invoice lines|	The related functionality is enabled out of the box.|	Accounts receivable|
|Resetting the workflow status for free text invoices from Unrecoverable to Draft|	The related functionality is enabled out of the box.|	Accounts receivable|

## Additional resources

### Platform updates for finance and operations apps

Dynamics 365 Finance version 10.0.43 includes platform updates. To learn more, see [Platform updates for version 10.0.43 of finance and operations apps](../../fin-ops-core/fin-ops/get-started/whats-new-platform-updates-10-0-43.md).

### Bug fixes

For information about the bug fixes that are included in this update, sign in to Microsoft Dynamics Lifecycle Services, and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=xxxx).

### Regulatory updates

For information about regulatory updates for finance and operations apps, see [Regulatory updates](../localizations/regulatory-updates.md). Another way to learn about regulatory updates is to sign in to Lifecycle Services and view the planned regulatory updates using the issue search tool. Issue search lets you search by country/region, type of feature, and release.

### Dynamics 365 and industry clouds: 2024 release wave 1 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out [Dynamics 365 and industry clouds: 2024 release wave 1 plan](/dynamics365/release-plan/2024wave1/finance-supply-chain/dynamics365-finance). We've captured all the details, end to end, top to bottom, that 
you can use for planning.




