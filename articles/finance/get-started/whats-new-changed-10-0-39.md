---
# required metadata

title: What's new or changed in Dynamics 365 Finance 10.0.39 (April 2024)
description: This article describes features that are either new or changed in the Microsoft Dynamics 365 Finance version 10.0.39 preview release.
author: twheeloc
ms.date: 1/19/2024
ms.topic: faq
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2022-09-02
ms.dyn365.ops.version: 10.0.39

---

# What's new or changed in Dynamics 365 Finance 10.0.39 (April 2024)

[!include [banner](../includes/banner.md)]

[!include [banner](../includes/preview-banner.md)]

This article lists features that are new or changed for Microsoft Dynamics 365 Finance version 10.0.39. This version has a build number of 10.0.XXXX and is available on the following schedule:

- **Preview of release:** January 2024
- **General availability of release (self-update):** March 2024
- **General availability of release (auto-update):** April 2024

## Features included in this release

The following table lists the features that are included in this release. We might update this article to include features that made it into the build after this article was initially published.

| Feature area | Feature | More information | Enabled by |
|--------------|---------|------------------|------------|
|Cash and bank management|Modern bank reconciliation|This feature redesigns advanced bank reconciliation including usability improvements, feature enhancements and performance improvements. Bank reconciliation matching rules are enhanced in 10.0.39 to support four new automatic matching scenario including generating voucher, generating customer and vendor payment journal, settling customer open invoices, and clear reversal company transactions. This feature is a preview feature and is available in sandbox environments in Dynamics 365 Finance version 10.0.39.|Feature management|
|Cash and bank management|Petty cash|Petty cash is extended from localization feature to a global feature for all countries in 10.0.39. You can use the petty cash functionality to automate operations for receipts and expenditures of cash, the creation of primary documents, and the printing of related reports.|Feature management|
|Cash and bank management|Customer and vendor netting |This feature enables the netting capability between open customer balances and open vendor balances. Customer and vendor payment journals are no longer created to settle open vendor and customer transactions. Instead, netting journals are created. This feature is a preview feature and is available in production environments in Dynamics 365 Finance version 10.0.39.|Feature management|
|Cash and bank management|Automatic clear bridged transactions through advanced bank reconciliation |This feature allows you to automatically clear bridged payment transactions through bank reconciliation instead of manually clearing them in general ledger. It also allows you to set up a bridging account per bank account. This feature is a preview feature and is available in production environments in Dynamics 365 Finance version 10.0.39.|Feature management|
|Cash and bank management|Exchange rate type enhancement for accounts payable and accounts receivable foreign currency revaluation |This feature provides additional exchange rate type options for accounts payable and accounts receivable foreign currency revaluation. Users can define accounting currency exchange rate type and reporting currency exchange rate type per legal entity or per customer and vendor group to override the default type on ledger setup when running foreign currency revaluation.|Feature management|
|Cash and bank management|Exchange rate type enhancement for bank foreign currency revaluation |This feature provides additional exchange rate type options for bank foreign currency revaluation. Users can define accounting currency exchange rate type and reporting currency exchange rate type per legal entity or per bank account to override the default type on ledger setup when running foreign currency revaluation.|Feature management|

## Feature enhancements included in this release

The following table lists the feature enhancements that are included in this release. Each of these enhancements provides an incremental improvement to an existing feature. Because they are only enhancements, they aren't listed in the [release plan](/dynamics365/release-plan/2023wave1/finance-operations/dynamics365-finance).

| Feature area | Feature name | More information |
|--------------|--------------|------------------|
|Cash and bank management|Customer and vendor netting|Automatic netting is available in 10.0.39. Users can configure netting rules and run batch job or process automation to automatically net the open balance under the selected netting agreements and additional critera|
|Cash and bank management|Customer and vendor netting|Two data entities, Netting agreement and Netting agreement pair, are available in 10.0.39 to import netting agreements. |
|Cash and bank management|Payment reversals|Check reversal is not allowed if the original check is marked as cleared in 10.0.39.|

## Additional resources

### Platform updates for finance and operations apps

Dynamics 365 Finance version 10.0.39 includes platform updates. To learn more, see [Platform updates for version 10.0.39 of finance and operations apps](../../fin-ops/get-started/whats-new-platform-updates-10-0-38.md).

### Bug fixes

For information about the bug fixes included in this update, sign in to Microsoft Dynamics Lifecycle Services and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=xxxxx).

### Regulatory updates

For information about regulatory updates for finance and operations apps, see [Regulatory updates](../localizations/regulatory-updates.md). Another way to learn about regulatory updates is to sign in to Lifecycle
Services and view the planned regulatory updates using the issue search tool. Issue search lets you search by country/region, type of feature, and release.

### Dynamics 365 and industry clouds: 2024 release wave 1 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out [Dynamics 365 and industry clouds: 2024 release wave 1 plan](/dynamics365-release-plan/2024wave1/finance-operations/dynamics365-finance). We've captured all the details, end to end, top to bottom, that 
you can use for planning.

### Removed and deprecated features

The [Removed or deprecated features in Dynamics 365 Finance](removed-deprecated-features-finance.md) article describes features that have been removed or deprecated for Dynamics 365 Finance.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature is not in active development and may be removed in a future update.

Before any feature is removed from the product, the deprecation notice will be announced in the [Removed or deprecated features in Dynamics 365 Finance](removed-deprecated-features-finance.md) article 12 months 
prior to the removal.
