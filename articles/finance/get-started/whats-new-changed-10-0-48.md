---
title: What's new or changed in Dynamics 365 Finance 10.0.48 (April 2026)
description: Learn about features that are either new or changed in the Microsoft Dynamics 365 Finance version 10.0.48 preview release.
author: twheeloc
ms.author: twheeloc
ms.topic: whats-new
ms.date: 04/26/2026
ms.update-cycle: 1095-days
ms.custom:   
  - bap-template
  - evergreen
ms.reviewer: twheeloc
ms.search.region: Global
---

# What's new or changed in Dynamics 365 Finance 10.0.48 (April 2026)

[!include [banner](../includes/banner.md)]
[!include [banner](../includes/preview-banner.md)]

This article lists the features that are new or changed for Microsoft Dynamics 365 Finance version 10.0.48. This version has a build number of 10.0.xxxx and is available on the following schedule:

- **Preview of release:** April 2026
- **General availability of release (self-update):** June 2026
- **General availability of release (auto-update):** July 2026

## Features included in this release

This section contains a table that lists the features that are included in this release when available. We might update this article to include features that were added to the build after this article was
originally published.

| Module or feature area | Feature name | More information | Enabled by |
|---|---|---|---|
| Accounts payable | [Vendor ship‑from address support on invoices](https://go.microsoft.com/fwlink/?linkid=2348316) | Introduces support for specifying and storing a vendor ship‑from address on vendor invoices in Dynamics 365 Finance. The ship‑from address represents the vendor establishment involved in the transaction and is used during invoice processing and posting. The address is captured on vendor invoices posted from purchase orders and journals and is immutably stored on the posted invoice. This capability enables correct identification of the vendor establishment, supports validation and immutable storage of mandatory [**Registration category**](../../fin-ops-core/dev-itpro/organization-administration/registration-ids.md), and ensures compliance, auditability, and accurate regulatory reporting for vendor invoices when this feature is enabled together with the Establishment and Registration ID governance on invoices feature. | Feature management |
| Budgeting | Inquiry of purchase orders processed during purchase order year-end | This feature provides finance teams with a dedicated inquiry to review purchase orders that were processed as part of the Purchase order year-wnd process, including which fiscal year was closed, the original and current accounting dates, and the resulting document status. This inquiry enables finance users to validate which purchase orders were successfully carried forward during year-end close and trace how purchasing commitments moved across fiscal years. The report aims to support audit, reconciliation, and period-close reviews without manual investigation. | Feature management |
| Cash and bank management | Automatic clearing of centralized bridged vendor payments during bank reconciliation | The feature enables automatic clearing of bridge transactions created by centralized vendor payments when bank reconciliation is completed. The system posts clearing journals in the centralized payment legal entity, and reconciliation and inquiry pages expose legal entity and related party information for improved traceability and auditability. | Feature management |
| Cash and bank management | Enable cash discount support for settle customer invoice matching rules | When you enable this feature, you can optionally apply cash discount as part of **Settle customer invoice reconciliation matching**. Cash discount is applied only when explicitly enabled on the rule. | Feature management |
| Cash and bank management | Enable In operator for one-to-one matching | Enables the IN operator for **Statement** and **Document matching rules** bank reconciliation. This enhancement applies only to one-to-one matching scenario. | Feature management |
| General ledger| Correct ledger settlement records with mismatched partial ledger settlement records | Detects and corrects transactions that have ledger settlement records but aren't marked as settled. | Data maintenance|
|General ledger | Clean up partial ledger settlement records | Detects and removes partial ledger settlement records where all ledger settlement records are fully reversed or missing. |Data maintenance|
|General ledger |Correct ledger settlement record status and remaining balance | Detects and corrects partial ledger settlement record status and remaining balance. | Data maintenance|
| Organization administration | Establishment and Registration ID governance on invoices | This feature introduces a unified governance model for invoicing in Dynamics 365 Finance by enabling [**Establishment**](../../fin-ops-core/fin-ops/organization-administration/organizations-organizational-hierarchies.md#establishments) handling and [**Registration ID**](../../fin-ops-core/dev-itpro/organization-administration/registration-ids.md) validation and immutable storage across all invoice creation paths. The feature extends support to all business documents that can generate an invoice, such as **Free text invoices**, **Sales orders**, **Purchase orders**, **Vendor invoices**, **Pending vendor invoices**, **Project invoice proposals**, **Intercompany customer invoices**, **General journals**, where the **Establishment** is captured at the document level and immutably stored on the posted invoice. <br> In addition, the feature enables extended [**Invoice party applicability rules**](../../fin-ops-core/dev-itpro/organization-administration/invoice-party-applicability-rules.md) for [**Registration category**](../../fin-ops-core/dev-itpro/organization-administration/registration-ids.md) and a unified **Registration IDs** review experience across Dynamics 365 finance and operations modules. During document processing and invoice posting, the system validates all mandatory **Registration IDs** according to **Invoice party applicability rules** set up for **Registration category** and immutably stores them on customer, vendor, and project invoices at posting time. | Feature management |
| Globalization studio | Electronic invoicing for France | The feature provides Dynamics 365 Finance compliance with French regulatory requirements for electronic invoicing.<p></p><ul><li>Supports the generation of electronic invoices XML files in the French extension of the UBL‑based format for domestic business‑to‑business (B2B) invoices and credit notes generated from sales orders, free text invoices, and project invoices</li><li>Transmits generated electronic invoices to counterparties and to the French tax authorities through EDICOM that act as an Accredited Service Provider</li><li>Enables the receipt of vendor electronic invoices in the UBL‑based format through EDICOM</li><li>Supports **mandatory** invoices lifecycle statuses sending and reception.</li><p></p><p>Learn more: [**Electronic invoicing for France**](../../finance/localizations/france/emea-fra-einv-ereport.md)</p>| Feature management |
| Tax | (Preview) Automate tax feature creation based on tax master data | The automated tax calculation feature migrates existing core tax master data in the legal entity using Tax Data Migration (preview). The system automatically creates the required records in the Tax feature setup, reusing existing tax codes, sales tax groups, and item sales tax groups. This approach minimizes setup complexity, preserves current configurations, and ensures a smoother transition to the advanced Tax calculation experience. Note: The functionality is supported globally, except for Brazil and India. | Feature management |

## Feature enhancements included in this release

This section contains a table that lists the enhancements that are included in this release when available. We might update this article to include features that were added to the build after this article was originally published.

| Module or feature area | Feature name | More information | Enabled by |
|---|---|---|---|
|General ledger |Recreate missing consolidation transactions |The **Recreate missing consolidation transactions** option in Dynamics 365 Finance helps resolve data inconsistencies that can occur when a consolidation process unexpectedly stops, for example, due to a system interruption or manual termination. For more information, see Recreate missing consolidations (<https://go.microsoft.com/fwlink/?LinkId=2356505>). | Enabled by default |
| Regulatory reporting | \[Netherlands\] Audit File Financial XAF 4.0 - performance improvement | This feature replaces the legacy model mapping within the `Audit file mode` with the new `Audit file model mapping` under the `Audit file model` in Electronic Reporting. This new model mapping improves the performance of the export of key financial data, including balances and transactions, in accordance with Audit File Financial XAF 4.0 in XML v4.0. It supports v4.0 of the XAF schema and introduces a redesigned export process that ensures faster generation, reduced system load, and a simplified workflow. By adopting this feature, legal entities with primary address in **Netherlands** can efficiently meet statutory reporting obligations while benefiting from a more scalable, performant, and maintainable export solution. <br> The **\[Netherlands\] Audit File Financial XAF 4.0 - performance improvement** feature leverages the **Performance enhancement for general ledger dimension set balance calculation** feature for the [**Audit File Financial XAF 4.0 for Netherlands**](https://go.microsoft.com/fwlink/?linkid=2346022). | Feature management |
| [Electronic Reporting](../../fin-ops-core/dev-itpro/analytics/general-electronic-reporting?context=/dynamics365/context/finance) | **BCC** recipients support in **Electronic reporting email destinations** | The Electronic reporting (ER) email destination now supports Blind Carbon Copy (BCC) recipients. When configuring an [ER file destination](../../fin-ops-core/dev-itpro/analytics/er-destination-type-email.md) with an email action, users can specify **BCC** email addresses in addition to the existing **To** and **CC** fields. This enhancement allows organizations to send copies of generated electronic reports to compliance, audit, or archival mailboxes without exposing those recipients to other email participants.| Enabled by default |

## Features turned on by default in this release

The following table lists the features that are turned on by default in version 10.0.47. You can still turn these features off in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) if necessary.

| Module | Feature name | Feature state |
|--|--|--|

## Features removed from feature management

The following table lists features that were removed from Feature management in version 10.0.47. These features are no longer listed in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) and are now a permanent part of Finance.

| Module | Feature name | More information |
|--|--|--|

## More information

### Platform updates for finance and operations apps

Dynamics 365 Finance version 10.0.48 includes platform updates. To learn more, see
[Platform updates for version 10.0.48 of finance and operations apps](../../fin-ops-core/fin-ops/get-started/whats-new-platform-updates-10-0-48.md).

### Bug fixes

For information about the bug fixes that are included in this update, sign in to Microsoft Dynamics 365 Lifecycle Services, and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=xxxx).

### Regulatory updates

For information about regulatory updates for finance and operations apps, see [Regulatory updates](../localizations/regulatory-updates.md). Another way to learn about regulatory updates is to sign in to Lifecycle
Services and view the planned regulatory updates using the issue search tool. Issue search lets you search by country/region, type of feature, and release.

### Dynamics 365 and industry clouds: 2026 release wave 1 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out [Dynamics 365 and industry clouds: 2026 release wave 1 plan](/dynamics365/release-plan/2026wave1/). We've captured all the details, end to end, top to bottom, that you can use for planning.
