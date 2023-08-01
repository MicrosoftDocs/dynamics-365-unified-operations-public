---
# required metadata

title: What's new or changed in Dynamics 365 Finance 10.0.36 (October 2023)
description: This article describes features that are either new or changed in the Microsoft Dynamics 365 Finance version 10.0.36 preview release.
author: twheeloc
ms.date: 07/28/2023
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
ms.dyn365.ops.version: 10.0.36

---

# What's new or changed in Dynamics 365 Finance 10.0.36 (October 2023)

[!include [banner](../includes/banner.md)]

[!include [banner](../includes/preview-banner.md)]

This article lists features that are new or changed for Microsoft Dynamics 365 Finance version 10.0.36. This version has a build number of 10.0.1695 and is available on the following schedule:

- **Preview of release:** July 2023
- **General availability of release (self-update):** September 2023
- **General availability of release (auto-update):** October 2023

## Features included in this release

The following table lists the features that are included in this release. We might update this article to include features that made it into the build after this article was initially published.

| Feature area | Feature | More information | Enabled by |
|--------------|---------|------------------|------------|
| Cash and bank management | Enable check number validation | This feature enables the **Allow check number validation** feature in Cash and bank management to validate check numbers when users generate a payment. When the parameter is turned on, the check number is validated to determine whether it exceeds the defined interval from last check number. Users can set up the check number interval. If the check number exceeds the defined interval from the last check number, the user must confirm before they proceed, to avoid manually entering the wrong check number. The feature also validates that there's no character in the check number. | Feature management |
| Cash and bank management | Generate customer and vendor payments from bank statements and reconciliation | This feature enhances the bank statement and reconciliation worksheet. Users can generate and post customer and vendor payment journals directly from selected bank statement lines. The posted customer and vendor payment journals are automatically matched with the original bank statement lines. This feature is a preview feature and is available in sandbox environments in Finance version 10.0.36. | Feature management |
| Cash and bank management | Improved advanced bank reconciliation by enabling group conditions in reconciliation matching rules | In advanced bank reconciliation, grouping conditions are available in the reconciliation matching rules setup, so that bank statement lines can be matched with bank documents in a many-to-many manner. | Feature management |
| Cash and bank management | Automatic importing bank statement from a SharePoint folder | This feature imports bank statement files from a SharePoint folder and lets users set up recurrence rules to periodically import the files. | Feature management |
| Cash and bank management | Bank foreign currency revaluation enhancements | <p>Before this feature, the bank foreign currency revaluation process considered every financial dimension value when the gain or loss was calculated. This feature lets your organization select to use all or none of the financial dimensions when the gain or loss is calculated. In addition, this feature changes the calculation logic. The calculation first calculates the balance of the bank account, with either all financial dimensions or no financial dimensions. It then calculates the unrealized gain or loss per ledger account.</p><p>**Important:** This feature can't be disabled after it's been enabled.</p> | Feature management |
| Cash and bank management | Accounts payable and accounts receivable foreign currency revaluation performance improvement by splitting into even batches | This feature improves the performance of foreign currency revaluation by splitting large batches into even batches to prevent large batches from a specific vendor or customer. | Feature management |
| Cash and bank management | Use the time zone option on bank statement import page for BAI2 format bank statement id generation | If a bank statement format uses time stamps to generate bank statement IDs, this feature uses the time zone option on the bank statement import page instead of the user option. | Feature management |
| General ledger | Post foreign currency realized gains/losses for ledger settlements | This feature posts foreign currency realized gains and realized losses for ledger settlements when the reporting currency values of the debits and credits differ. This feature also enhances the usability of the ledger settlement process by reducing the effort that's required to mark vouchers. | Feature management |

## Features turned on by default in this release

The following table lists the features that are turned on by default in version 10.0.36. Most features that have been turned on atomically can be turned off in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md). In the future, some features that have been turned on automatically might be removed from Feature management and will become mandatory. This change ensures that customers are using current functionality, so that as enhancements are added, they can build on the current functionality. Features will never be automatically enabled in less than one year, unless they are determined to be essential.

| Feature name | Feature state | Module |
|--------------|---------------|--------|
| Financial tags | On by default | General ledger |
| (Italy) Fiscal journal page numbering improvements | Mandatory | General ledger |
| Journal reversal no longer requires consecutive number sequence | Mandatory | General ledger |
| Allow edits to internal data on general ledger vouchers | Mandatory | General ledger |
| Amount details from **General journal account** entry are displayed on the **Trial balance with transactional detail** report | Mandatory | General ledger |
| Awareness between ledger settlement and year-end close | On by default | General ledger |
| Add a date filter when viewing unsettled ledger transactions | Mandatory | General ledger |
| New voucher and date for new transactions in the advanced bank reconciliation bank statement | On by default | Cash and bank management |
| Ability to post detailed vendor and customer payments, but summarize amounts to bank account | On by default | Cash and bank management |
| Time zone for importing bank statements using Electronic reporting | On by default | Cash and bank management |

## Features removed from Feature management

The following table lists the features that have been removed from Feature management in version 10.0.36.

| Feature name | Feature state | Module |
|--------------|---------------|--------|
| Reverse reconciled advanced bank reconciliation | The related functionality is enabled out of the box. | Cash and bank management |
| Reverse posted bank statement | The related functionality is enabled out of the box. | Cash and bank management |
| Revert to simple bank reconciliation from advanced bank reconciliation | The related functionality is enabled out of the box. | Cash and bank management |
| Turn off set based updates for customer settlement cash discount date | The related functionality is enabled out of the box. | Accounts Receivable |
| Enable remove open transactions of zero amount from settlement when marking transactions | The related functionality is enabled out of the box. | Cash and bank management |
| Identification information for Bank accounts located in Japan | The related functionality is enabled out of the box. | Cash and bank management |
| Vendor payment proposal automation | The related functionality is enabled out of the box. | Accounts payable |

## Additional resources

### Platform updates for finance and operations apps

Dynamics 365 Finance version 10.0.36 includes platform updates. To learn more, see [Platform updates for version 10.0.36 of finance and operations apps](../../fin-ops-core/dev-itpro/get-started/whats-new-platform-updates-10-0-36.md)

### Bug fixes

For information about the bug fixes included in this update, sign in to Microsoft Dynamics Lifecycle Services and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=831854).

### Regulatory updates

For information about regulatory updates for finance and operations apps, see [Regulatory updates](../localizations/regulatory-updates.md). Another way to learn about regulatory updates is to sign in to Lifecycle Services and view the planned regulatory updates using the issue search tool. Issue search lets you search by country/region, type of feature, and release.

### Dynamics 365 and industry clouds: 2023 release wave 1 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out [Dynamics 365 and industry clouds: 2023 release wave 1 plan](/dynamics365-release-plan/2022wave2/finance-operations/dynamics365-finance). We've captured all the details, end to end, top to bottom, that you can use for planning.

### Removed and deprecated features

The [Removed or deprecated features in Dynamics 365 Finance](removed-deprecated-features-finance.md) article describes features that have been removed or deprecated for Dynamics 365 Finance.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature is not in active development and may be removed in a future update.

Before any feature is removed from the product, the deprecation notice will be announced in the [Removed or deprecated features in Dynamics 365 Finance](removed-deprecated-features-finance.md) article 12 months prior to the removal.

For breaking changes that only affect compilation time, but are binary compatible with sandbox and production environments, the deprecation time will be less than 12 months. Typically, these are functional updates that need to be made to the compiler.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
