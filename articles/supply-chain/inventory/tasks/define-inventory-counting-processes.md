--- 
title: Define inventory counting processes
description: Learn about the configuration of basic inventory counting processes by creating a counting group and a counting journal with a step-by-step process. 
author: yufei-huang
ms.author: yufeihuang
ms.topic: how-to
ms.date: 11/04/2024
ms.custom:
ms.reviewer: kamaybac 
ms.search.form: InventCountGroup, InventJournalName, InventParameters, EcoResProductDetailsExtended, InventItemLocation, InventLocationIdLookup
---

# Define inventory counting processes

[!include [banner](../../includes/banner.md)]

This article describes the configuration of basic inventory counting processes by creating a counting group and a counting journal. It also shows you how to enable counting policies on a warehouse and item level.

Learn more about advanced warehouse scenarios in [Cycle counting](../../warehousing/cycle-counting.md).

## Create a counting group

1. Go to **Inventory management** \> **Setup** \> **Inventory** \> **Counting groups**.
1. Select **New**.
1. In the **Counting group** field of the new row, type a value.
1. In the **Name** field, type a value.
1. In the **Counting code** field, choose one of the following values:

    - *Manual* – Add lines to the counting journal every time you run the job. In other words, you decide the counting interval for the counting group.  
    - *Period* – Add lines to the counting journal according to the period interval set in the **Counting period** field. With this option, when you run the job for creating new lines in the counting journal, it creates new lines at the specified interval, regardless of how often you run the job. For example, suppose **Counting period** is set to *7* and journal lines were last generated for a count on January 1. If another job is started on January 5, then no lines are generated in the journal for that period interval because seven days haven't passed. However, if you start the job again on January 8, then lines are generated for the period because seven days have passed.
    - *Zero in stock* – If on-hand inventory reaches zero (0), generate lines in the counting journal when the job is run. If the on-hand inventory reaches 0 after a count, lines are generated the next time that you start the count.  
    - *Minimum* – Insert lines in the counting journal if the on-hand inventory is equal to or less than the minimum that is specified.

1. If you set **Counting code** to *Period*, then enter the period interval (in days) in the **Counting period** field.
1. Select **Save**.

## Create a counting journal name

1. Go to **Inventory management** \> **Setup** \> **Journal names** \> **Inventory**.
1. Select **New**.
1. In the **Name** field, type a value.
1. In the **Description** field, type a value.
1. In the **Journal type** field, select *Counting*.
1. In the **Voucher series** field, select the number sequence to use for generating voucher IDs for new counting journals.
1. In the **Detail level** field, select the level of detail to apply when posting the journal.
1. In the **Reservation** field, choose the method used to reserve items during counting. Choose one of the following values:
    - *Manual* – The items are reserved manually on the **Reservation** page.
    - *Automatic* – The order quantity is reserved from the available on-hand inventory for the item.
    - *Explosion* – The reservation is part of the master planning of the transaction.

1. Select **Save**.

## Set standard counting journal name

1. Go to **Inventory management** \> **Setup** \> **Inventory and warehouse management parameters**.
2. Open the **Journals** tab.
3. In the **Counting** field, select the journal you created for this purpose. This is the default journal name for inventory journals of the *Counting* type.  
4. Open the **General** tab. If you want to lock items during the counting process to prevent updates for packing slips, picking lists, or picking list registrations, then set **Lock items during count** to *Yes*. Otherwise, set it to *No*.

## Set the counting policy for an item

1. Go to **Product information management** \> **Products** \> **Released products**.
2. In the list, select the link for the item number of the product that you want to set counting policies on. You must select an item that is inventory tracked. A non-stocked product can't be counted.
3. Select **Edit**.
4. Toggle the expansion of the **Manage inventory** section.
5. In the drop-down menu of the **Counting group** field, select the counting group you previously created. This product will now be included when inventory counting journal lines are created using this counting group.  
6. Select **Save**.

## Implement advanced counting scenarios

To prevent double-counting mistakes, the system normally allows items to be part of just one active counting journal at a time. However, if your company processes require it, you can relax this constraint to count items independently per warehouse or turn this integrity check off completely. The following subsections explain how.

### Count items independently per warehouse

To set the counting policy to allow items to be counted independently in each warehouse, follow these steps.

1. On the Action Pane, select **Manage inventory**.
2. Select **Warehouse items**.
3. Select **New**.
4. In the **Warehouse** field, select the warehouse you want to set up specific counting policies for.
5. In the **Counting group** field, select the counting group that should apply to the item in the selected warehouse. When counting is performed in that warehouse, this counting policy overrides the general counting policy for the item.  
6. Select **Save**.

### Disable counting status registration

To disable counting status registration, effectively allowing duplicate item and dimension combinations to be placed in multiple active counting journals, follow these steps.

1. Go to **Inventory management** \> **Setup** \> **Journal names** \> **Inventory**.
2. Select or create a journal name with a **Journal type** of *Counting*.
3. Set **Counting status registration policy** to *Disable counting status registration*.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
