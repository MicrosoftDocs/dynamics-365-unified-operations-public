---
title: What's new or changed in Dynamics 365 Finance 10.0.42 (December 2024)
description: Learn about features that are either new or changed in the Microsoft Dynamics 365 Finance version 10.0.42 preview release distributed in December 2024.
author: twheeloc
ms.author: twheeloc
ms.topic: faq
ms.date: 10/25/2024
ms.custom:   
  - bap-template
  - evergreen
ms.reviewer: twheeloc
ms.search.region: Global
---

# What's new or changed in Dynamics 365 Finance 10.0.42 (December 2024)


[!include [banner](../includes/banner.md)]
[!include [banner](../includes/preview-banner.md)]

This article lists the features that are new or changed for Microsoft Dynamics 365 Finance version 10.0.42. This version has a build number of 10.0.XXXX and is available on the following schedule:

- **Preview of release:** October 2024
- **General availability of release (self-update):** December 2024
- **General availability of release (auto-update):** February 2025

## Features included in this release

This section contains a table that lists the features that are included in this release when available. We might update this article to include features that were added to the build after this article was originally published.

| Module or feature area | Feature name | More information | Enabled by |
|---|---|---|---|
| Cash and bank management | Enable default descriptions for advanced bank reconciliation | This feature enables default descriptions for automatic payment journal posting and voucher posting in advanced bank reconciliation. | Feature management |
| Cash and bank management | Enable prepayment and posting profile when generating payment journal in advanced bank reconciliation | This feature enables prepayment option and posting profile when generating customer payment journal and vendor payment journal from the bank reconciliation worksheet. Users can configure these two options on the reconciliation matching rule setup. | Feature management |
| Cash and bank management | Mark all bank transactions as cleared in account reconciliation | This feature provides additional capabilities to mark all bank transactions as cleared and unmark all bank transactions during the advanced bank account reconciliation process. | Feature management |
| Cash and bank management | Merge payment schedule for customer transactions or vendor transactions | This feature enables the **Merge payment schedule** button on customer/vendor settlement transaction pages. For open transactions split via **Apply payment schedule**, you can merge them again via this button after marking one of the selected transactions as primary payment. | Feature management |
|Fixed assets | Capitalize charges cost into the fixed assets main account |This feature enables the capitalization of charges added during the acquisition of a fixed asset through a purchase order. Any applicable charges are automatically posted to the fixed asset’s main account and included in the total capitalization cost, ensuring accurate financial reporting and asset valuation.|Feature management |
|Fixed assets |(Preview) Fixed assets depreciation processing enhancements|This enhancement improves the efficiency of depreciation proposal batch jobs by ensuring the inclusion of assets with various ID formats, preventing blank journals, and avoiding duplicate journals due to temporary errors. It also boosts the asset transactions cache, leading to faster processing of depreciation proposals.|Feature management |
|Fixed assets | (Preview) Fixed assets transactions cache performance improvements for depreciation proposal |Enabling this feature optimizes the asset transactions cache for depreciation proposals, resulting in enhanced processing performance and faster execution times for generating depreciation calculations.|Feature management |
|General Ledger | (Preview) Financial tag defaulting rules |This feature allows the definition of rules for various transactions to automatically set the default value of Financial tags. The flexibility of this functionality also extends to copying existing rules across different but compatible transaction types, and even between legal entities. This streamlines the process, ensuring consistency and efficiency in transaction tagging, which is essential for accurate financial tracking and reporting. |Feature management |




## Feature enhancements included in this release

This section contains a table that lists the enhancements that are included in this release when available. We might update this article to include features that were added to the build after this article was originally published.

| Module or feature area | Feature name | More information | Enabled by |
|---|---|---|---|
| Cash and bank management | Use Electronic payment number for EndToEndId | The parameter **Use Electronic payment number for EndToEndId** is added to the latest versions of ISO 20022 Credit transfer payment file formats, payment model and payment model mapping. Enable the parameter while generating the payment file, and it will transfer the electronic payment number to the EndToEndId field in the payment file. | Parameter |
| Cash and bank management | Customer and vendor netting | A new filter has been added on the **Customer and vendor balance netting** page to display the cleared netting agreement. The netting history for a fully cleared netting agreement can now be shown. | On by default |
| Cash and bank management | Enhancements to bank foreign currency revaluation | Enabling the feature will allow the bank FCR reset and revaluation on the same day. | Feature management |
| Cash and bank management | Exchange rate type enhancement for accounts payable and accounts receivable foreign currency revaluation | AP/AR FCR simulation function will run using the same setting of the additional exchange rate type option. | Feature management |
|General ledger |Accounting source explorer updated advanced filtering. |Enabling this feature provides an advanced filtering option for the Accounting source explorer, including a convenient date range selection, with different types of date intervals available. Additionally, an advanced filter will be available, which is capable of filtering fields such as ledger account, business unit, cost center, department, etc. |Feature management |


## Features turned on by default in this release

The following table lists the features that are turned on by default in version 10.0.42. Most features that have been turned on atomically can be turned off in [Feature management](../../fin-ops-core/fin-ops/get-
started/feature-management/feature-management-overview.md). In the future, some features that have been turned on automatically might be removed from Feature management and will become mandatory. This change 
ensures that customers are using current functionality, so that as enhancements are added, they can build on the current functionality. Features will never be automatically enabled in less than one year, unless
they are determined to be essential.

| Feature name | Feature state | Module |
|--------------|---------------|--------|


## Features removed from Feature management

The following table lists the features that have been removed from Feature management in version 10.0.41.

| Feature name | Feature state | Module |
|--------------|---------------|--------|


## Additional resources

### Platform updates for finance and operations apps

Dynamics 365 Finance version 10.0.42 includes platform updates. To learn more, see [Platform updates for version 10.0.42 of finance and operations apps](../../fin-ops-core/fin-ops/get-started/whats-new-platform-
updates-10-0-42.md).

### Bug fixes

For information about the bug fixes that are included in this update, sign in to Microsoft Dynamics Lifecycle Services, and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=xxxx).


### Regulatory updates

For information about regulatory updates for finance and operations apps, see [Regulatory updates](../localizations/regulatory-updates.md). Another way to learn about regulatory updates is to sign in to Lifecycle 
Services and view the planned regulatory updates using the issue search tool. Issue search lets you search by country/region, type of feature, and release.

### Dynamics 365 and industry clouds: 2024 release wave 1 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out [Dynamics 365 and industry clouds: 2024 release wave 1 plan](/dynamics365/release-plan/2024wave1/finance-supply-chain/dynamics365-finance). We've captured all the details, end to end, top to bottom, 
that you can use for planning.


