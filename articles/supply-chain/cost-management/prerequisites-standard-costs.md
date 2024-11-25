---
title: Prerequisites for standard costs
description: Learn about the basic steps for using standard costs, including a step-by-step process for setting up standard costs and additional resources. 
author: prasungoel
ms.author: prasungoel
ms.topic: how-to
ms.date: 05/27/2024
ms.custom:
  - bap-template
ms.reviewer: kamaybac
ms.search.form: InventStdCostConv, CostingVersion
---

# Prerequisites for standard costs

[!include [banner](../includes/banner.md)]

This article describes the basic steps for using standard costs. Subsequent steps depend on the company's operations. For example, the steps differ for a nonmanufacturing environment, a manufacturing environment that doesn't use routings, and a manufacturing environment that uses routings.

To set up standard costs, follow these steps.

1. Create an item model group for standard costs.

    Use the **Item model groups** page to create a new group for standard costs, and assign an inventory model of **Standard cost**. The identifier for the item model group should be meaningful, such as **Std Cost**. Select the check boxes to indicate that the group should allow financial negative inventory, and that it should post physical inventory and financial inventory. This standard cost group will be assigned to items.

2. Define ledger accounts that are related to standard cost variances.

    Use the **Chart of accounts** page to define ledger accounts that are related to standard cost variances. These ledger accounts must be defined before they can be assigned on the **Posting** page. The ledger accounts can reflect item groups and cost groups.

3. Assign ledger accounts to item postings that are related to standard cost variances.

    Use the **Posting** page to assign the ledger accounts that are related to standard cost variances. You can specify a variance's ledger account by item (or item group) and by cost group (or cost group type), or you can specify that the ledger account applies to all items and all cost groups. These options correspond to cost relations for tables, groups, and all.

    Before you define the item posting rules, use the **Transaction combinations** page to enable cost relations (for tables, groups, and all).

4. Define inventory parameters that are related to standard costs.

    1. Use the **Inventory accounting** tab on the **Inventory accounting policies setup > Parameters** page to define two cost control parameters that are related to standard costs.

        - In the **Cost breakdown** field, select **None** or **Sub ledger**. If you select **Sub ledger**, the cost breakdown is an *active* cost breakdown. An active cost breakdown is critical for calculating, retaining, and viewing cost group segmentation across a multilevel product structure for standard cost items. When the cost breakdown is active, you can report and analyze inventory, work in process (WIP), and cost of goods sold (COGS) per cost group in a single-level, multilevel, or total format. When the cost breakdown is active, if you activate a manufactured item's cost, the cost group segmentation will be stored in the item's cost record.

        - If you select **None**, cost group segmentation won't be maintained for standard cost items. In other words, a manufactured item's standard cost will be calculated and maintained as a single amount, without cost group segmentation. The cost contributions of manufactured components will be aggregated into the single amount.

    1. In the **Variances to standard** field, select **Summarized** or **Per cost group**. If you select **Per cost group**, you can identify purchase price variances and production variances by cost group. You can also identify the four types of production variances: the lot size, quantity, price, and substitution variances. If you select **Summarized**, you can't identify variances by cost group, and you can't identify the four types of production variances. You can just view a summarized production variance.

        The policy about variance to standard works independently of the cost breakdown policy. In other words, you can select a cost breakdown policy of **None** and select variances per cost group, so that production variances by cost group will still be captured.

5. Create costing versions for standard costs.

    Use the **Costing version setup** page to create one or more costing versions for standard costs. Each costing version must be designated by a costing type of **Standard cost** and must allow content to include cost data.

6. Prepare an existing customer to use standard costs.

    Customers who want to change their existing items to a standard cost inventory model must use the **Standard cost conversions** page.

## Related information

### Help articles

- [Standard cost conversion overview](standard-cost-conversion-overview.md)

### Community blogs

- [How to set up standard costs for direct materials in finance and operations](https://financefunction.tech/2018/06/07/how-to-set-up-standard-costs-for-direct-materials-in-dynamics-365-for-finance-and-operations)
- [Standard direct labor costs in finance and operations](https://financefunction.tech/2018/07/16/standard-direct-labor-cost-in-dynamics-365-for-finance-and-operations)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
