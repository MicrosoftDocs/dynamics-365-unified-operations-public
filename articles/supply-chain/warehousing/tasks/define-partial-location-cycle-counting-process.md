--- 
title: Define partial location cycle counting process 
description: Learn how to guide the actual counting operations by requesting that only specific products be counted instead of all on-hand inventory at the location. 
author: Mirzaab
ms.author: mirzaab
ms.topic: how-to
ms.date: 06/23/2017
ms.custom:
ms.reviewer: kamaybac
ms.search.form: WHSRFMenuItemCycleCount, WHSCycleCountPlan, WHSCycleCountPlanListPage, WHSWorkTemplateTable
---

# Define partial location cycle counting process

[!include [banner](../../includes/banner.md)]

When you use cycle count plans to create counting work, you can guide the actual counting operations by requesting that only specific products and product variants be counted instead of all on-hand inventory at the location. By filtering on specific products, the warehouse manager can reduce review overhead, help prevent consolidation mistakes, and save time. Typically, a warehouse manager performs the setup tasks.

## Create a cycle counting work template

1. Go to **Warehouse management** \> **Setup** \> **Work** \> **Work templates**.
1. In the **Work order type** field, select *Cycle counting*.
1. Select **New**.
1. In the **Sequence number** field, enter a number. The sort order is from the smallest number to the largest number. The value must be more than 0 (zero).  
1. In the list, mark the selected row.
1. In the **Work template** field, type a value.
1. In the **Work template** description field, type a value.
1. In the **Work pool ID** field, enter or select a value.
1. In the **Work priority** field, enter a number.
1. Select **Save**.
1. Select **New**.
1. In the list, mark the selected row.
1. In the **Work type** field, select *Counting*.
1. In the **Work class ID** field, enter or select a value.
1. Select **Save**.
1. Select **Work line breaks**.
1. Select **New**.
1. In the **Sequence number** field, enter a number. The sort order is from the smallest number to the largest number. The value must be more than 0 (zero).  
1. Select **Save**.
1. Close the page.
1. Close the page.

## Create a cycle counting plan

1. Go to **Warehouse management** \> **Setup** \> **Cycle counting** \> **Cycle count plans**.
1. Select **New**.
1. In the **Cycle counting plan ID** field, type a value.
1. In the **Description** field, type a value.
1. In the **Maximum number of cycle counts** field, enter a number.
1. In the **Work template** field, enter or select a value.
1. Select **New**.
1. In the **Sequence number** field, enter a number. The sort order is from the smallest number to the largest number. The value must be more than 0 (zero).  
1. In the **Description** field, type a value.
1. Select **Save**.
1. Select **Define product query**.
1. In the list, mark the selected row.
1. In the **Criteria** field, enter or select a value.
1. Select **OK**.
1. Close the page.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
