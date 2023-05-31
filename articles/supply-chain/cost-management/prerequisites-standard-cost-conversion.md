---
# required metadata

title: Prerequisites for a standard cost conversion
description: This article discusses tasks to perform before you run a standard cost conversion. 
author: JennySong-SH
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: InventStdCostConv
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.assetid: 73af66cf-c924-45be-837a-a648dbd05a31
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: yanansong
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Prerequisites for a standard cost conversion

[!include [banner](../includes/banner.md)]

This article discusses tasks to perform before you run a standard cost conversion. 

Before you run a standard cost conversion, follow these steps:

1.  Define an **item model group** for standard costs. Use the Item model groups page to create an item model group that uses a standard cost inventory model. When setting up a standard cost conversion, you assign this item model group to the items that are being converted.
2.  Assign a **cost group** to each item.
    -   The cost group that is assigned to a purchased item can act as the basis for assigning ledger accounts that are related to standard costs. This can include assigning ledger accounts for purchase price variances. In a manufacturing environment, the cost group that is assigned to purchased components also provides cost segmentation in the calculated costs of a manufactured item.
    -   The cost group that is assigned to a manufactured item can act as the basis for assigning ledger accounts that are related to standard costs, such as assigning ledger accounts for production variances.

3.  Assign a **standard order quantity** to a manufactured item when it has constant costs. The standard order quantity for a manufactured item acts as an accounting lot size for amortizing, or prorating, constant costs. These can include setup times in routing operations or a constant component quantity in a bill of material (BOM).
4.  Assign **general ledger accounts** that are related to standard costs, especially the revaluation variance. Use the **Posting** page (**Inventory management** &gt; **Setup**) to assign general ledger accounts that are related to standard costs. As a minimum for the standard cost conversion process, you must assign the account for the revaluation variance for all items and all cost groups. Use the **Chart of accounts** page to define the general ledger accounts that will be needed for standard costs. Use the **Transaction combinations** page to enable cost relations (for tables, groups, and all) before you define the item posting rules.
5.  Define the inventory parameters that are related to standard costs. Use the **Number sequences** tab on the **Inventory and warehouse management parameters** page to assign a number sequence to revaluation vouchers. A revaluation voucher is generated when the standard cost conversion creates a change of an item's inventory value. Use the **Inventory and warehouse management parameters** page to define Cost Control parameters (on the **Inventory accounting** tab) to define two parameters that are related to standard costs.
    -   Use the **Cost breakdown** field to select No or Sub ledger. The selection of Sub ledger is termed an active cost breakdown. An active cost breakdown is very important for calculating, retaining, and viewing cost group segmentation across a multilevel product structure for standard cost items. When the cost breakdown is active, you can report and analyze the following in a single level, multi-level, or total format:
        1.  Inventory
        2.  Work in process (WIP)
        3.  Cost of goods sold (COGS) per cost group

        An active cost breakdown means that if you enable a manufactured item's cost, the result will be stored in the cost group segmentation in the item's cost record. If you put no value in the **Cost breakdown** field, the cost group segmentation will not be maintained for standard cost items. That is, a manufactured item's standard cost will be calculated and maintained as a single amount without cost group segmentation, and the cost contributions of manufactured components will be aggregated into the single amount.
    -   Use the **Variances to standard** field to select summarized or per cost group. The selection of per cost group enables you to identify purchase price variances and production variances by cost group. This also enables you to identify the four types of production variances (the lot size, quantity, price, and substitution variances). If you select summarized, you cannot identify variances by cost group, and you cannot identify the four types of production variances. You can only view a summarized production variance. The policy about variance to standard is independent of the cost breakdown policy. That is, you can select a cost breakdown policy of none, and select variances per cost group, so that production variances by cost group will still be captured.







[!INCLUDE[footer-include](../../includes/footer-banner.md)]