--- 
title: Define inventory counting processes
description: Learn about the configuration of basic inventory counting processes by creating a counting group and a counting journal with a step-by-step process. 
author: banluo-ms
ms.author: banluo
ms.topic: how-to
ms.date: 05/04/2026
ms.custom:
ms.reviewer: kamaybac 
ms.search.form: InventCountGroup, InventJournalName, InventParameters, EcoResProductDetailsExtended, InventItemLocation, InventLocationIdLookup
---

# Define inventory counting processes

[!include [banner](../../includes/banner.md)]

This article describes how to configure basic inventory counting processes by creating a counting group and a counting journal. It also shows you how to enable counting policies at the warehouse and item levels.

For more information about advanced warehouse scenarios, see [Cycle counting](../../warehousing/cycle-counting.md).

## Create a counting group

1. Go to **Inventory management** > **Setup** > **Inventory** > **Counting groups**.
1. Select **New**.
1. In the **Counting group** field, enter a value.
1. In the **Name** field, type a value.
1. In the **Counting code** field, choose one of the following values:

    - *Manual* – Add lines to the counting journal every time you run the job. In other words, you decide the counting interval for the counting group.  
    - *Period* – Add lines to the counting journal according to the period interval set in the **Counting period** field. When you choose this option, the job for creating new lines in the counting journal adds them only at the specified interval, regardless of how often you run the job. For example, suppose **Counting period** is set to *7* and counting journal lines were last generated on January 1. If another job is started on January 5, then no lines are generated in the counting journal because seven days haven't passed. However, if you start the job again on January 8, then lines are generated because seven days have passed.
    - *Zero in stock* – If on-hand inventory reaches zero (0), generate lines in the counting journal when the job is run. If the on-hand inventory reaches 0 after a count, lines are generated the next time that you start the count.  
    - *Minimum* – Insert lines in the counting journal if the on-hand inventory is equal to or less than the minimum that is specified.

1. If you set **Counting code** to *Period*, enter the period interval (in days) in the **Counting period** field.
1. Select **Save**.

## Create a counting journal name

1. Go to **Inventory management** > **Setup** > **Journal names** > **Inventory**.
1. Select **New**.
1. In the **Name** field, type a value.
1. In the **Description** field, enter a value.
1. In the **Journal type** field, select *Counting*.
1. In the **Voucher series** field, select the number sequence to use for generating voucher IDs for new counting journals.
1. In the **Detail level** field, select the level of detail to apply when posting the journal.
1. In the **Reservation** field, choose the method used to reserve items during counting. Choose one of the following values:
    - *Manual* – The items are reserved manually on the **Reservation** page.
    - *Automatic* – The order quantity is reserved from the available on-hand inventory for the item.
    - *Explosion* – The reservation is part of the master planning of the transaction.

1. Select **Save**.

## Set standard counting journal name

1. Go to **Inventory management** > **Setup** > **Inventory and warehouse management parameters**.
1. Open the **Journals** tab.
1. In the **Counting** field, select the journal you created for this purpose. This journal name is the default for inventory journals of the *Counting* type.  
1. Open the **General** tab. If you want to lock items during the counting process to prevent updates for packing slips, picking lists, or picking list registrations, set **Lock items during count** to *Yes*. Otherwise, set it to *No*.

## Set the counting policy for an item

1. Go to **Product information management** > **Products** > **Released products**.
1. Open the item that you want to set counting policies on. You must select an item that is inventory tracked. Non-stocked products can't be counted.
1. Select **Edit**.
1. Expand the **Manage inventory** FastTab.
1. In the **Counting group** field, assign a counting group. This product is now included when inventory counting journal lines are created by using this counting group.  
1. Select **Save**.

## Implement advanced counting scenarios

To prevent double-counting mistakes, the system normally only allows items to be part of a single active counting journal at a time. However, if your company processes require it, you can relax this constraint to count items independently per warehouse or turn this integrity check off completely. The following subsections explain how.

### Count items independently per warehouse

To set the counting policy to allow items to be counted independently in each warehouse, and ensure that items with identical dimension values can only be included within the same counting journal, follow these steps:

1. Go to **Product information management** > **Products** > **Released products**.
1. Open the item that you want to be counted. You must select an item that is inventory tracked. Non-stocked products can't be counted.
1. On the Action Pane, open the **Manage inventory** tab and, from the **Warehouse** group, select **Warehouse items**.
1. On the Action Pane, select **New**.
1. On the **General** FastTab, set the **Warehouse** field to the warehouse you want to set up specific counting policies for.
1. On the Action Pane, select **Save**.
1. Repeat from step 4 for each warehouse where the item should be counted.
1. Repeat from step 2 for each item that should be counted independently in each warehouse.
1. Go to **Inventory management** > **Journal entries** > **Items counting** > **Counting**.
1. On the Action Pane, select **New**.
1. On the **Overview** FastTab, select the **Site** and **Warehouse**.
1. On the **Counting by** FastTab, set **Warehouse** to *Yes*.
1. Select **OK** to create the journal.
1. In the newly created counting journal, add items as usual.

### Disable counting status registration

To disable counting status registration, which allows duplicate item and dimension combinations to be placed in multiple active counting journals, follow these steps:

1. Go to **Inventory management** > **Setup** > **Journal names** > **Inventory**.
1. Select or create a journal name with a **Journal type** of *Counting*.
1. Set **Counting status registration policy** to *Disable counting status registration*.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
