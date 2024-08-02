---
title: What's new or changed in Dynamics 365 Finance 10.0.38 (February 2024)
description: Learn about features that are either new or changed in the Microsoft Dynamics 365 Finance version 10.0.38 preview release distributed in February 2024.
author: twheeloc
ms.author: twheeloc
ms.topic: faq
ms.custom: 
  - bap-template
  - evergreen
ms.date: 07/22/2024
ms.reviewer: twheeloc 
ms.search.region: Global
ms.search.validFrom: 2022-09-02
ms.dyn365.ops.version: 10.0.38
---

# What's new or changed in Dynamics 365 Finance 10.0.38 (February 2024)

[!include [banner](../includes/banner.md)]

[!include [banner](../includes/preview-banner.md)]

This article lists features that are new or changed for Microsoft Dynamics 365 Finance version 10.0.38. This version has a build number of 10.0.1777 and is available on the following schedule:

- **Preview of release:** October 2023
- **General availability of release (self-update):** December 2023
- **General availability of release (auto-update):** February 2024

## Features included in this release

The following table lists the features that are included in this release. We might update this article to include features that made it into the build after this article was initially published.

| Feature area | Feature | More information | Enabled by |
|--------------|---------|------------------|------------|
| Cash and bank management | Net customer and vendor balance | This feature enables the netting capability between open customer balances and open vendor balances. Customer and vendor payment journals are no longer created to settle open vendor and customer transactions. Instead, netting journals are created. This feature is a preview feature and is available in sandbox environments in Dynamics 365 Finance version 10.0.38. | Feature management |
| Cash and bank management | Settle bank statement with open customer invoices | This feature enhances the bank statement and reconciliation worksheet. Users can settle open customer invoices directly from selected bank statement lines. Users can turn on the **Generate customer and vendor payments from bank statements and reconciliation** feature in the **Feature management** workspace. This feature is a preview feature and is available in sandbox environments in Finance version 10.0.38. | Feature management |
| Cash and bank management | Generate NACHA payment file by Electronic reporting | This feature enables the generation of Electronic reporting (ER) for National Automated Clearing House Association (NACHA) payment files. To use this feature, users can import ER configurations under **Standard NACHA (US) - customers** and **Standard NACHA (US) - vendors**. | |
| General ledger | Post foreign currency realized gains/losses for ledger settlements | <p>In Finance version 10.0.36, this feature posted foreign currency realized gains and realized losses for ledger settlements when the *reporting currency* values of the debits and credits differ. In Finance version 10.0.38, new capabilities are added that post foreign currency realized gains and realized losses for ledger settlements when the *accounting currency* values of the debits and credits differ.</p><p>This feature also changes the determination of whether a ledger settlement is fully settled. The feature now makes this determination based on the *transaction currency*, unless the ledger settlement and the transaction currencies differ for the marked transactions. In that case, the *accounting currency* values are used to determine whether the marked transactions are balanced. This feature doesn't support partial settlement. | Feature management |
| Tax calculation | [Integration with project transactions](/dynamics365/release-plan/2023wave2/finance-supply-chain/dynamics365-finance/tax-calculation-service-integration-project-operations) | Tax calculation integration is now extended with the following Project management and accounting transactions in finance and operations apps: Project invoice proposal, Journals (Hour/Expense/Item/Fee), Project quotations, and Project Operations integration journal. | Parameter |
| General Ledger | Performance enhancement for general ledger dimension set balance calculation | This feature enables your trial balance inquiry page and reports that use financial dimension sets to run more efficiently. The financial dimension sets store data more efficiently, in less space, and enable the trial balance to show the current balance data more quickly. This feature uses process automation to keep the balance amounts up to date. For more information, see [New financial dimension sets](../general-ledger/financial-dimension-set-new.md). | Feature management |

## Feature enhancements included in this release

The following table lists the feature enhancements that are included in this release. Each of these enhancements provides an incremental improvement to an existing feature. Because they are only enhancements, they aren't listed in the [release plan](/dynamics365/release-plan/2023wave1/finance-operations/dynamics365-finance).

| Feature area | Feature name | More information |
|--------------|--------------|------------------|
| Credit and collections | Credit and collections analytics performance improvements | The credit and collections Power BI analytics reports have improved data joins and filtering for faster rendering of the reports. The currency calculation process and computed columns are redesigned so that the overall performance of the reports is faster. The Day sales outstanding calculation was removed from the report. That calculation is now available in the **Credit statistics** FactBox. For more information, see [Credit and collections management Power BI content](../accounts-receivable/credit-collections-power-bi.md). |


## Additional resources

### Platform updates for finance and operations apps

Dynamics 365 Finance version 10.0.38 includes platform updates. To learn more, see [Platform updates for version 10.0.38 of finance and operations apps](../../fin-ops-core/fin-ops/get-started/whats-new-platform-updates-10-0-38.md).

### Bug fixes

For information about the bug fixes included in this update, sign in to Microsoft Dynamics Lifecycle Services and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=857683).

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
