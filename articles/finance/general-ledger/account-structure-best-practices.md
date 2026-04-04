---
title: Best practices for account structures
description: Learn best practices for designing, configuring, and activating account structures to optimize performance and reduce maintenance.
author: aprilolson
ms.author: aolson
ms.topic: article
ms.date: 03/25/2026
ms.custom:
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.search.form: DimensionConfigureAccountStructure
ms.dyn365.ops.version: AX 7.0.0
---

# Best practices for account structures

[!include[banner](../includes/banner.md)]

This article covers best practices for designing account structures, preparing for activation, and avoiding common performance issues. Following these guidelines helps keep activation fast, maintenance simple, and the user experience smooth.

## Designing account structures

### Use ranges and wildcards instead of individual values

When you define allowed values for a segment, use ranges and wildcards wherever possible instead of listing individual values one by one. This approach has two benefits:

- **Fewer constraint nodes** — The system builds an internal tree of constraint nodes to validate account entries. Individual values each create their own node, while a single range creates just one. Fewer nodes means faster activation and better runtime performance.
- **Less maintenance** — When new dimension values are created (for example, a new cost center), a range like `100..199` automatically includes the new value. Individual entries require manual updates every time.

For example, instead of listing each allowed department number individually:

| Main account | Department |
|---|---|
| 400000..999999 | 001 |
| 400000..999999 | 002 |
| 400000..999999 | 003 |
| ... | ... |
| 400000..999999 | 020 |

Use a range:

| Main account | Department |
|---|---|
| 400000..999999 | 001..020 |

If you have a specific set of values that fall within a continuous range, the range form is both higher-performing and easier to maintain.

### Reuse account structures across legal entities

Reuse account structures wherever possible to reduce maintenance. When the same structure works for multiple legal entities, assign it to each instead of creating separate copies. For variations across legal entities, consider using advanced rules rather than duplicating entire structures.

### Position the main account first

Make the main account the first segment in the account structure, or as close to the front as possible. This gives users the best guided experience during account entry, because the system identifies the correct structure as soon as the main account value is entered. Verify that any third-party solutions you use support the main account in the first position.

### Don't rely solely on advanced rules

Don't put an asterisk (\*) for every segment in the account structure and then rely entirely on advanced rules for validation. This approach is difficult to manage, often leads to user error during maintenance that can prevent the system from posting, and can cause performance issues during activation and transaction entry.

### Keep structures simple and purpose-driven

Consider your business needs, growth plan, and maintenance plan when designing structures. A structure that's too broad requires more complex rules; a structure that's too narrow requires frequent updates. Find the right balance for your organization.

## Preparing for activation

Account structure activation synchronizes all unposted transactions to match the new structure. The more unposted transactions there are, the longer activation takes. The following practices help keep activation times reasonable.

### Reduce unposted transactions before activating

The single biggest factor in activation time is the volume of unposted transactions. Before activating, consider:

- **Posting pending transactions** — If business rules allow, post any pending journals, free text invoices, vendor invoices, and other documents with open accounting distributions before activation.
- **Cleaning up unused distributions** — Some source documents may have accounting distributions with no associated accounting event. These records can typically be regenerated later. Work with the team that owns the source document process to determine if cleanup is appropriate.
- **Saving and removing journal work** — If posting isn't possible, use Excel to save in-progress journal work, remove the ledger accounts from the journals, activate the structure, and then reimport the saved work afterward.

### Schedule activation during low-activity periods

Activation performs best when the system isn't simultaneously processing new transactions. Plan your activation for off-hours or maintenance windows, and temporarily suspend activity that could interfere with the process:

- **Pause automated batch processes** — Temporarily suspend batch jobs that create or process transactions, such as vendor invoice processing, free text invoice posting, budget register entries, and similar recurring jobs. Resume these jobs after activation completes.
- **Stop data imports and OData integrations** — Temporarily disable recurring data imports, Data Management Framework jobs, and OData integrations that create or modify transactions with financial dimensions.
- **Inform users to avoid entering transactions** — Ask users to hold off on entering journals, invoices, purchase orders, and other documents that generate accounting distributions during the activation window.
- **Turn off ISV and third-party batch jobs** — Temporarily disable batch jobs from third-party modules that process documents. Several are known to cause activation jobs to fail silently. Run these batch jobs and similar third-party processes only after activation completes.

> [!NOTE]
> These suspensions are temporary and only needed for the duration of the activation. Resume all batch jobs, integrations, and normal user activity as soon as activation completes.

### Activate one structure at a time

Only activate one account structure at a time. If multiple activation batch jobs run simultaneously, they block each other because they're updating the same underlying data. This causes each activation to take much longer than it would on its own.

If you need to activate multiple structures, activate them sequentially — wait for one to complete before starting the next.

### Treat activation as a periodic process

Account structure activation is intended to be a periodic process — quarterly, annually, or whenever business requirements change. If you find that you need to update structures on a weekly or daily basis, consider whether the structures can be redesigned for easier maintenance. Structures that require constant changes due to routine events (like adding new project records) may benefit from using ranges or wildcards that automatically accommodate new values.

## Reducing advanced rule complexity

Having too many advanced rules or advanced rule structures associated with a single account structure can significantly slow down activation. Performance issues have been observed when the number of advanced rules per structure exceeds approximately 20.

To reduce complexity:

- **Consolidate rules** — If possible, transfer advanced rule criteria directly into the account structure instead of using separate rules.
- **Reduce the number of rule structures** — Fewer rule structures per account structure means less evaluation time during activation.

### Factors that affect activation performance

The following factors can contribute to slow activation:

| Factor | Description |
|---|---|
| Large volume of unposted transactions | Transactions in tables like LedgerJournalTrans, TaxUncommitted, and AccountingDistribution must all be synced to the new structure. |
| Active users and concurrent processing | Users entering transactions, automated batch processes, and data imports that create transactions during activation compete for the same resources. |
| Multiple simultaneous activations | Running more than one activation at a time causes blocking, as each process updates the same data. |
| [Highly variable dimensions](/dynamics365/finance/cost-accounting/high-var-dimensions) | Non-financial data (like document numbers, serial numbers, or timestamps) used as financial dimensions creates unique dimension combinations that can't be grouped for bulk updates. |
| Too many advanced rules | More than approximately 20 advanced rules per structure can cause extended AOS processing time with no SQL activity. |
| ISV extensions on transaction tables | Extensions that override set-based operations can force the system to fall back to slower row-by-row updates. |
| Open budget data | Large volumes of open budget records add to the processing workload. |

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
