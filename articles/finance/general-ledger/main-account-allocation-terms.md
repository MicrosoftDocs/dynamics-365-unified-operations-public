---
title: Allocation terms
description: Learn about using allocation terms on a main account, including a step-by-step process for creating an allocation term on a main account. 
author: rachel-profitt
ms.author: raprofit
ms.topic: article
ms.date: 08/05/2026
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2020-06-15
ms.search.form: AccountingDistribution, LedgerAllocationRule, MainAccount, AllocationTerms
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 04c8548a-0af9-492b-954b-946b4f8ca023
---

# Allocation terms

[!INCLUDE [banner](../includes/banner.md)]

This article provides information about using allocation terms on a main account. Use allocation terms to distribute amounts across multiple ledger account combinations. They help ensure that expenses or revenues are charged to the correct object in accounting.

Each allocation term that you create on a main account defines the percentage of a voucher to allocate from a single-source main account and a combination of financial dimensions. In addition, you define the destination main account and financial dimensions where the amount is allocated.

When you define the source financial dimension for the allocation, you can select if each dimension is specific or unspecific. Specific indicates that the financial dimension for the source transaction must match the selected dimension. When you select unspecific, it indicates that any value for the financial dimension can contribute to a match.

When you define the destination ledger account for an allocation term, you must specify the main account that you are allocating the amount to. You can use the same main account where the source transaction is posted to, or a different main account. If you use the same main account, a warning displays when saving the record. In addition to specifying the main account, you must also specify the destination dimensions. For each dimension, you can specify if you want to keep the source financial dimension value or change it. If you select no, then you must select a new value for the financial dimension. If you select yes, no additional information is specified, and the system maintains the original financial dimensions when you post.

You can add unlimited allocation terms to a main account, but the sum of the percent to allocate on an allocation term can't exceed 100. You can create allocations for less than 100 percent if a portion of the original voucher amount should remain in the source financial dimensions. You can add allocation terms to a main account as a legal entity override. If you're using a shared chart of accounts, you must define allocation terms for each legal entity. To access the **Allocation terms** button, you must first select the **Allocation** check box on the Legal entity override.

## Allocation term example

You define a cost center for your organization called CORPORATE that is numbered 000. When you post invoices for utility expenses, you code them to this CORPORATE cost center. Your company has defined a rule that all utility expenses should be allocated by a percentage to each of the individual cost centers. The other financial dimensions for department and business unit stay the same.

In this example, you create a new allocation term for the utility expense main account. You create one row for each cost center with the percentage to allocate. The **Selection criteria** for the source financial dimensions for each row is **Specific** for the **Cost center** and the value is set to 000: CORPORATE. For department and business unit, the **Selection criteria** is **Unspecific**.

On the **Destination ledger account** FastTab, the main account is the same utility expense account, and the **Keep source financial dimensions** is set to **Yes** for **Business unit** and **Department.** The **Keep source financial dimensions** is set to **No** for **Cost center**, and the value selected is each respective cost center that you're allocating to. If there are three cost centers to allocate to, then you create three allocation terms records. The only difference between each allocation term is the cost center that is specified on the destination ledger account.

## Create an allocation term on a main account

1. In the **Navigation pane**, go to **Modules > General ledger > Chart of accounts > Accounts > Main accounts**.
1. In the list, find and select the desired record.
1. On the **Legal entity overrides** FastTab, select **Add**.
1. Select the **Company** and then select **Add**.
1. Select the **Allocation** check box.
1. Select **Allocation terms**.
1. Select **Edit** to modify the default record, or select **New** to add a record.
1. In the **Percent** field, enter the percentage of voucher transactions that you want to allocate.
1. On the **Source financial dimension** FastTab, in the **Selection criteria** for each financial dimension, select an option.
    - If you select **Specific**, select the financial dimension value in the drop-down box on the right.
    - If you select **Unspecific**, no additional information is required for the financial dimension.
1. On the **Destination ledger** account FastTab in the **To account** field, select the main account where you want to allocate the percentage of the voucher transaction.
1. In **Keep source financial dimensions** for each financial dimension, select an option.
    - If you select **No**, select the financial dimension value in the drop-down box on the right where you want the voucher transaction to be allocated to.
    - If you select **Yes**, no additional information is required. The system keeps the value on the original voucher when posting the allocation.
1. Repeat steps 7-11 for each additional allocation. The sum of all allocations is indicated in the **Total percent** field. This amount can't exceed 100.
1. Close all of the pages.

>[!NOTE]
> You can optionally use the **Copy** button to duplicate the selected allocation.

When you create an allocation term for a main account, the system automatically posts a new voucher when a voucher is posted that matches the source financial dimensions on the allocation terms.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
