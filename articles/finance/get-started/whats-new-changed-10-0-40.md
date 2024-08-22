---
title: What's new or changed in Dynamics 365 Finance 10.0.40 (June 2024)
description: Learn about features that are either new or changed in the Microsoft Dynamics 365 Finance version 10.0.40 preview release distributed in June 2024.
author: twheeloc
ms.author: twheeloc
ms.topic: faq
ms.custom: 
  - bap-template
  - evergreen
ms.date: 07/22/2024
ms.reviewer: twheeloc
ms.search.region: Global
---

# What's new or changed in Dynamics 365 Finance 10.0.40 (June 2024)

[!include [banner](../includes/banner.md)]
[!include [banner](../includes/preview-banner.md)]

This article lists the features that are new or changed for Microsoft Dynamics 365 Finance version 10.0.40. This version has a build number of 10.0.1935.5 and is available on the following schedule:

- **Preview of release:** April 2024
- **General availability of release (self-update):** May 2024
- **General availability of release (auto-update):** June 2024

## Features included in this release

This section contains a table that lists the features that are included in this release when available. We might update this article to include features that were added to the build after this article was originally published.

| Module or feature area | Feature name | More information | Enabled by |
|---|---|---|---|
| Cash and bank management | Bank account lifecycle management | This feature enables approval workflows for bank account activation, modification, and deactivation. It provides a bank account change history for auditing purposes. A protected field list is available to control the bank account fields that trigger the modification approval workflow. | Feature management |
| Cash and bank management | Customer and vendor netting | This feature enables netting capability between open customer balances and open vendor balances. Customer and vendor payment journals are no longer created to settle open vendor and customer transactions. Instead, netting journals are created. This feature is generally available in Dynamics 365 Finance version 10.0.40. | Feature management |
| Accounts receivable | Improve performance and efficiency of Sales invoice entities. | To improve the performance and efficiency of our sales invoice entities, we eliminated inefficient views and computed columns. The new entities no longer rely on inefficient views but instead fetch all columns directly from the data sources. Therefore, data retrieval is faster. | Feature management |
| Accounts payable | Post document with distribution process splitting | This feature optimizes memory usage. To help prevent memory overflow when long invoices are handled, it splits the distribution process into individual batch tasks. | Feature management |
| Accounts payable | Extend the length of vendor invoice numbers | This feature extends the invoice number from 20 characters to 50 characters in the vendor invoice and invoice journal. Before you enable the feature, create a Microsoft Dynamics Lifecycle Services ticket to open the EableEdtStringDatabaseStringLengthAttributeInComputation flight. | Default off |
| Document management | Export attachments in Document management | This feature exports files and metadata that are attached to records of tables in finance and operations apps. For more information, see [Configure document management](../../fin-ops-core/dev-itpro/organization-administration/configure-document-management.md). | |
| Credit and collections | Credit and collections workspace | The **Collections coordinator** workspace centralizes essential collection information for the collections agent (coordinator). Therefore, it streamlines customer communication and decision-making. By offering an overview of customer accounts, activities, and balances, the workspace facilitates efficient collections management. | Feature management |
| Credit and collections | Customer balance statistics deletion job | Users can now  efficiently manage long-term data that's stored in the Customer balance statistics table. This enhancement includes a **Delete outdated balance statistics records** periodic task that removes unnecessary records from the table. Therefore, it alleviates potential performance impacts that are associated with data overload. **Customer balance statistics deletion job** is enabled in Feature management. | Feature management |
| Credit and collections | Customer account rename data maintenance | A new data maintenance page helps streamline data consistency. Customers can use this page to view and manually retry failed updates. | Feature management |
| General ledger | Consolidation templates | Consolidation online templates let you set up the consolidation information one time and then use it every time that the consolidation process is run. The updated **Consolidate online** page now shows all consolidation runs, reruns, and reversals. To use this functionality, enable the **Consolidate online using templates** feature in Feature management. | Feature management |
| General ledger | Reverse related journals | This feature reverses all related journals in a single step. As part of the automatic split of large journals, multiple journals can be created from one large journal. Users can now reverse all those journals at the same time. For more information, see [Reverse related journals with journals that were automatically split](../general-ledger/reverse-journal-posting.md#reverse-related-journals-with-journals-that-were-automatically-split). | |
|Workflow |Workflow history summary|This feature displays an AI-generated summary on the **Workflow history** page. The concise summary shows the submitter, current status, due date and any comments and most recent approvals, rejections and change requests with comments. The most relevant history featured in the **Summary by copilot** fastTab helps approvers make faster decisions because they don't need to search through the history page.|Feature management |
|Electronic Invoicing |E-Invoicing for Chile: ISV last-mile connector with Edicom|This feature is the last-mile integration with the Chilean Tax Authorities via the Certification Authorization Provider Edicom. It provides the required end-to-end process of the outbound flow of e-invoices submission. For more information, see: [Get started with Electronic invoicing for Chile](../localizations/iberoamerica/ltm-chile-elec-invo-conncection.md).|  |

## Feature enhancements included in this release

This section contains a table that lists the enhancements that are included in this release when available. We might update this article to include features that were added to the build after this article was originally published.

| Module or feature area | Feature name | More information | Enabled by |
|---|---|---|---|
| Cash and bank management | Import bank statement | The import of bank statements through data entities is supported. **Bank statement header** and **Bank statement lines** data entities are available. | Default on |
| Cash and bank management | Modern bank reconciliation | When the **Modern bank reconciliation** feature is enabled, a redesigned bank reconciliation report is available. The new report saves snapshots by bank reconciliation cut-off date. Both unreconciled transaction details and reconciled transaction details are available on the report. | Feature management |
| Cash and bank management | Modern bank reconciliation | When the **Modern bank reconciliation** feature is enabled, the **Matching ID** field is available. A unique matching ID is generated when bank statement transactions are matched. This ID is shown on the **Matched transactions** tab. | Feature management |
| Cash and bank management | Modern bank reconciliation | When the **Modern bank reconciliation** feature is enabled, the **Matching type** field is available. This field indicates how the bank statement transactions are reconciled. (For example, transactions can be reconciled through matching with bank documents or by generating a voucher.) This information is shown on the **Matched transactions** tab. | Feature management |
| Cash and bank management | Modern bank reconciliation | If a bank statement transaction is posted to the general ledger as a voucher, relevant company transactions are shown on the **Company transaction** page. | Feature management |
| Accounts payable | Vendor invoice center (Preview) | This feature enhancement lets users drill down to the detailed invoice list pages by selecting the subtitle number in the new **Vendor invoice center** workspace. | Feature management |
| Accounts payable (Invoice capture) | Support line level financial dimensions | The line-level financial dimensions (business unit, cost center, and department) are introduced in Invoice capture version 1.3.0.x and later. To streamline the process, this feature transfers the financial dimensions value from Invoice capture to Dynamics 365 Finance without requiring any additional extensions. | |
| Tax | Support Invoice number in Posted sales tax transactions | The **Invoice ID** field is now added to posted sales tax transactions. This change helps prevent the loss of invoice numbers in transactions that are posted through the general ledger journal (**Account type** = **Ledger**) when the cleanup journal periodic job is run. | |
| Tax calculation | Support unit conversion for "By quantity" calculation | If a sales or purchase transaction is entered in a unit other than the unit that's specified on the sales tax code, the unit is now automatically converted based on the unit conversions that are set up on the **Unit conversions** page. | |
| Tax calculation | (POL) SAD documents integration | Single Administrative Documents (SAD) are now integrated with Tax calculation. This functionality enables tax amounts to be configured and recorded with **Sales tax payable** and **Sales tax receivable** tax directions. | |
| Tax calculation - Universal tax rate API | Support setting up error handling for tax solution providers | A new **Retrieve ISV Error Messages Codes** API type is introduced in the tax feature. This new API type lets independent software vendors (ISVs) define their own error codes and messages. When you select **Sync result codes** on the **Error Handling** tab of the **Tax calculation parameters** page, you receive a list of error codes from the API that's specified in the tax feature. These error codes are stored in the database. | |
| Credits and collections | Customer payment journals | Payment journals that have multiple payment lines that have an undisputed collections status are now faster and more efficient. | |
| Credits and collections | Customer aging report | Performance is improved when the aging bucket balances are calculated on the customer aging report. | |
| General ledger| Awareness between ledger settlement and year-end close |The awareness feature, including its dependent features for automating ledger settlements and posting foreign currency gains/losses, has been moved to **General ledger parameters**. These options, found on the **Ledger settlement** page, are controlled by the **Enable advanced awareness options**, **Enable process automation for ledger settlement**, and **Enable post currency realized gains/losses for ledger settlements** settings.| |

## Additional resources

### Platform updates for finance and operations apps

Dynamics 365 Finance version 10.0.40 includes platform updates. To learn more, see [Platform updates for version 10.0.40 of finance and operations apps](../../fin-ops-core/fin-ops/get-started/whats-new-platform-updates-10-0-40.md).

### Bug fixes

For information about the bug fixes that are included in this update, sign in to Microsoft Dynamics Lifecycle Services, and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=932660).


### Regulatory updates

For information about regulatory updates for finance and operations apps, see [Regulatory updates](../localizations/regulatory-updates.md). Another way to learn about regulatory updates is to sign in to Lifecycle Services and view the planned regulatory updates using the issue search tool. Issue search lets you search by country/region, type of feature, and release.

### Dynamics 365 and industry clouds: 2024 release wave 1 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out [Dynamics 365 and industry clouds: 2024 release wave 2 plan](/dynamics365/release-plan/2024wave1/finance-supply-chain/dynamics365-finance). We've captured all the details, end to end, top to bottom, that you can use for planning.

### Removed and deprecated features

The [Removed or deprecated features in Dynamics 365 Finance](removed-deprecated-features-finance.md) article describes features that have been removed or deprecated for Dynamics 365 Finance.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature is not in active development and may be removed in a future update.

Before any feature is removed from the product, the deprecation notice will be announced in the [Removed or deprecated features in Dynamics 365 Finance](removed-deprecated-features-finance.md) article 12 months prior to the removal.


