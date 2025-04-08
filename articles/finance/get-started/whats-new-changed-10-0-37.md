---
title: What's new or changed in Dynamics 365 Finance 10.0.37 (November 2023)
description: Learn about features that are either new or changed in the Microsoft Dynamics 365 Finance version 10.0.37 preview release distributed in November 2023.
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
ms.dyn365.ops.version: 10.0.37
---

# What's new or changed in Dynamics 365 Finance 10.0.37 (November 2023)

[!include [banner](../includes/banner.md)]

[!include [banner](../includes/preview-banner.md)]

This article lists features that are new or changed for Microsoft Dynamics 365 Finance version 10.0.37. This version has a build number of 10.0.1725 and is available on the following schedule:

- **Preview of release:** September 2023
- **General availability of release (self-update):** October 2023
- **General availability of release (auto-update):** November 2023

## Features included in this release

The following table lists the features that are included in this release. We might update this article to include features that made it into the build after this article was initially published.

| Feature area | Feature | More information | Enabled by |
|--------------|---------|------------------|------------|
| Accounts payable | Default option for Approved by field in the Invoice register | This feature lets administrators control the mandatory status of the **Approved by** field on the invoice register. The field can be set as optional when formal approval isn't required in the invoice register's business process. |
|Tax and audit regulatory reporting|VAT declaration of Denmark direct submission to the Danish Tax Agency|This feature allows direct submission of VAT returns in XML format to the Danish Tax Agency. For more information, see [Submit a VAT return in XML format to the Danish Tax Agency]( ../localizations/denmark/emea-dnk-vat-declaration-submission.md).|

## Feature enhancements included in this release

The following table lists the feature enhancements that are included in this release. Each of these enhancements provides an incremental improvement to an existing feature. Because they are only enhancements, they aren't listed in the [release plan](/dynamics365/release-plan/2023wave1/finance-operations/dynamics365-finance).

| Feature area | Feature name | More information |
|--------------|--------------|------------------|
| Cash and bank management | Import bank statement | Bank statement import for the ISO20022 camt053.001.08 version is supported in Finance version 10.0.37. Users can import the latest Advanced bank reconciliation statement configuration, ABR Camt.053 format version 3.13. |
| Accounts payable | Match the detail for vendor invoices | In Finance version 10.0.37, invoice validation is available on different invoice amount fields. This enhancement provides specific control over the round-off amount. |
| Cash and bank management | ISO20022 Credit Transfer | The Generic Credit Transfer payment format is supported for the ISO20022 pain.001.001.09 version. Users can generate the latest Credit Transfer configuration, ISO20022 Credit transfer 2019 version 43.73. |
| Cash and bank management | ISO20022 Direct Debit | The Generic Direct Debit payment format is supported for the ISO20022 pain.008.001.08 version. Users can generate the latest Direct Debit configuration, ISO20022 Direct debit 2019 version 12.38. |
| Cash and bank management | ISO20022 Credit Transfer format for Italy | The Italian Credit Transfer payment format is supported for the CBI 00.04.01 version. Users can generate the latest Credit Transfer configuration, ISO20022 Credit transfer 2019 (IT) version 43.73.18. |
| Cash and bank management | ISO20022 Direct Debit format for Italy | The Italian direct debit payment format is supported for the CBI 00.01.01 version. Users can generate the latest Direct Debit configuration, ISO20022 Direct debit 2019 (IT) version 12.38.14. |
| Cash and bank management | ISO20022 Credit Transfer format for Norway | The Norwegian Credit Transfer payment format is supported for the ISO20022 pain.001.001.09 version. Users can generate the latest Credit Transfer configuration, ISO20022 Credit transfer 2019 (NO) version 43.73.28. |
| Accounts payable localization | Apply prepayments to vendor invoices | <p>The capability to automatically apply prepayments to vendor invoices is available for Italy. This update enables access to **Apply prepayment** in the Italian country/region. Here are some of the additional feature enhancements for Italy:</p><ul><li>**Apply prepayment** no longer requires that the **Sales tax group** and **Item sales tax group** fields are set up on the invoice line during posting.</li><li>The prepayment transaction results are recorded in the Italian sales tax book section.</li></ul> |

## Additional resources

### Platform updates for finance and operations apps

Dynamics 365 Finance version 10.0.37 includes platform updates. To learn more, see [Platform updates for version 10.0.37 of finance and operations apps](../../fin-ops-core/fin-ops/get-started/whats-new-platform-updates-10-0-37.md)

### Bug fixes

For information about the bug fixes included in this update, sign in to Microsoft Dynamics Lifecycle Services and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=838613).

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

