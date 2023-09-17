---
# required metadata

title: Allocation terms
description: This article provides information about using allocation terms on a main account. 
author: rachel-profitt
ms.date: 06/15/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: AccountingDistribution, LedgerAllocationRule, MainAccount, AllocationTerms
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
ms.assetid: 04c8548a-0af9-492b-954b-946b4f8ca023
ms.search.region: Global
# ms.search.industry: 
ms.author: raprofit
ms.search.validFrom: 2020-06-15
ms.dyn365.ops.version: AX 7.0.0

---

# Allocation terms

[!include [banner](../includes/banner.md)]

This article provides information about using allocation terms on a main account. Allocation terms are used to distribute amounts across multiple ledger account combinations. They help ensure that expenses or revenues are charged to the correct object in accounting.

Each allocation term that you create on a main account defines the percentage of a voucher to be allocated from a single-source main account and a combination of financial dimensions. In addition, you define the destination main account and financial dimensions where the amount will be allocated. 

When you define the source financial dimension for the allocation, you can select if each dimension is specific or unspecific. Specific indicates that the financial dimension for the source transaction must match the selected dimension. When you select unspecific, it indicates that any value for the financial dimension can contribute to a match.

When you define the destination ledger account for an allocation term, you must specify the main account that you are allocating the amount to. You can use the same main account where the source transaction is posted to, or a different main account. If the same main account is used, a warning displays when saving the record. In addition to specifying the main account, you must also specify the destination dimensions. For each dimension, you can specify if you want to keep the source financial dimension value or change it. If you select no, then you must select a new value for the financial dimension. If you select yes, no additional information is specified, and the system will maintain the original financial dimensions when you post.

There is no limit to the number of allocations terms that you can add to a main account; however, the sum of the percent to allocate on an allocation term cannot exceed 100. You can create allocations for less than 100 percent if a portion of the original voucher amount should remain in the source financial dimensions. Allocations terms can be added to a main account as a legal entity override. If you are using a shared chart of accounts, allocation terms must be defined for each legal entity. To access the **Allocation terms** button, you must first select the **Allocation** check box on the Legal entity override.

## Allocation term example
You have defined a cost center for your organization called CORPORATE that is numbered 000. When invoices are posted for utility expenses, they are coded to this CORPORATE cost center. Your company has defined a rule that all utility expenses should be allocated by a percentage to each of the individual cost centers. The other financial dimensions for department and business unit will stay the same.

With this example, a new allocation term would be created for the utility expense main account. One row would be created for each cost center with the percentage to be allocated. The **Selection criteria** for the source financial dimensions for each row would be **Specific** for the **Cost center** and the value would be set to 000: CORPORATE. For department and business unit, the **Selection criteria** would be **Unspecific**.

On the **Destination ledger account** FastTab, the main account will be the same utility expense account, and the **Keep source financial dimensions** will be set to **Yes** for **Business unit** and **Department.** The **Keep source financial dimensions** will be set to **No** for **Cost center**, and the value selected will be each respective cost center that you are allocating to. If there are three cost centers to allocate to, then three allocation terms records would be created. The only difference between each allocation term is the cost center that is specified on the destination ledger account.

## Create an allocation term on a main account

1. In the **Navigation pane**, go to **Modules > General ledger > Chart of accounts > Accounts > Main accounts**.
2. In the list, find and select the desired record.
3. On the **Legal entity overrides** FastTab, select **Add**.
4. Select the **Company** and then select **Add**.
5. Select the **Allocation** check box.
6. Select **Allocation terms** .
7. Select **Edit** to modify the default record, or select **New** to add a record.
8. In the **Percent** field, enter the percentage of voucher transactions that you want to allocate.
9. On the **Source financial dimension** FastTab, in the **Selection criteria** for each financial dimension, select an option.
    - If you select **Specific**, then select the financial dimension value in the drop-down box on the right.
    - If you select **Unspecific**, no additional information is required for the financial dimension.
10. On the **Destination ledger** account FastTab in the **To account** field, select the main account where you want to allocate the percentage of the voucher transaction.
11. In **Keep source financial dimensions** for each financial dimension, select an option.
    - If you select **No**, then select the financial dimension value in the drop-down box on the right where you want the voucher transaction to be allocated to.
    - If you select **Yes**, then no additional information is required. The system will keep the value on the original voucher when posting the allocation.
12. Repeat steps 7-11 for each additional allocation. The sum of all allocations is indicated in the **Total percent** field. This amount cannot exceed 100.
13. Close all of the pages.

>[!NOTE] 
> You can optionally use the **Copy** button to duplicate the selected allocation.

When an allocation term is created for a main account, the system will automatically post a new voucher when a voucher is posted that matches the source financial dimensions on the allocation terms.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
