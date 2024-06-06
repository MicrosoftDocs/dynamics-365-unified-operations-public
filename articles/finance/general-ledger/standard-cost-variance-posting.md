---
title: Standard cost variance posting
description: Learn about setting up posting profiles for standard costing, including a sample posting profile configuration and table giving details for posting types.
author: rachelprofitt
ms.author: raprofit
ms.topic: overview
ms.date: 04/25/2022
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.form: InventPosting, InventItemGroup
---

# Standard cost variance posting

When you use standard costing for one or more products in your organization, you must configure the [prerequisites for standard costing](../../supply-chain/cost-management/prerequisites-standard-costs.md). This article explains the posting accounts that are required for step 3 of the prerequisites, "Assign ledger accounts to item postings that are related to standard cost variances."

Different types of variances can occur for purchases and production orders. For examples of production variances, see [Common sources of production variances](../../supply-chain/cost-management/common-sources-of-production-variances.md). Purchase order price variances occur when you use standard cost for a purchased item, and there is a difference between the product's standard cost and the invoiced amount on the purchase order.

## Sample posting profile configuration

The following table shows examples of the default posting types. It includes sample main accounts and descriptions.

- The "Debit/Credit?" column indicates whether the transaction is typically a debit or a credit. In some case, the transaction can post either debits or credits.
- The "Clearing account" column indicates that the posting type is a clearing account. In other words, the amount that is posted in this account is automatically reversed when a later transaction is posted.
- The "P/F" column indicates the type of posting. "P" represents physical posting, and "F" represents financial posting.
- The "Follow" column indicates whether the main account for the posting type is typically the same as the main account for another posting type. Specifically, it indicates the posting type that is typically used.

> [!NOTE]
> The main accounts and main account names in the table are suggestions. We recommend that you work with your accountant to determine the best configuration for your business needs.

| Posting type | Main account example | Main account name example | Account type | Debit/Credit? | Clearing account | P/F | Follow | Description |
|--------------|----------------------|---------------------------|--------------|---------------|------------------|-----|--------|-------------|
| Purchase price variance | 510310 | Purchase price variance | Expense | Either | No | F | Not applicable | This account is used when there is a variance between the purchase price and standard cost on a purchase order. |
| Inventory cost revaluation | 510330 | Inventory cost revaluation | Expense | Either | No | F | Not applicable | This account is used when a new costing version is activated for a standard cost item to revalue the on-hand inventory. |
| Cost change variance | 510320 | Cost change variance | Expense | Either | No | F | Not applicable | This account is used when there is a difference in standard costs between sites, or when an item is returned and there is a change between the original standard cost and the current standard cost for a product. |
| Production lot size variance | 510370 | Production lot size variance | Expense | Either | No | F | Not applicable | This account is used when there are differences between the bill of materials (BOM) calculation basis and the actual quantity for the production order cost calculation. |
| Production price variance | 510340 | Production price variance | Expense | Either | No | F | Not applicable | This account is used when there are price differences between the estimated cost and the actual cost for a production order. |
| Production quantity variance | 510350 | Production quantity variance | Expense | Either | No | F | Not applicable | This account is used when there are quantity differences between the estimated cost and the actual costs for a production order. |
| Production substitution variance | 510360 | Production substitution variance | Expense | Either | No | F | Not applicable | This account is used when there is unexpected consumption on a production order. |
| Rounding variance | 618160 | Rounding difference | Expense | Either | No | F | Not applicable | This account is used when there is a rounding difference when the production costs are calculated from the standard costs. |
