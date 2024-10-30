--- 
title: Define inventory counting processes
description: Learn about the configuration of basic inventory counting processes by creating a counting group and a counting journal with a step-by-step process. 
author: yufei-huang
ms.author: yufeihuang
ms.topic: how-to
ms.date: 07/26/2019
ms.custom:
ms.reviewer: kamaybac 
ms.search.form: InventCountGroup, InventJournalName, InventParameters, EcoResProductDetailsExtended, InventItemLocation, InventLocationIdLookup
---

# Define inventory counting processes

[!include [banner](../../includes/banner.md)]

This article describes the configuration of basic inventory counting processes by creating a counting group and a counting journal. It also shows you how to enable counting policies on a warehouse and item level. These tasks would typically be carried out by a warehouse supervisor. It is a prerequisite to have some existing released products and warehouses. If you're using a demo data company, you can run this procedure in the USMF company with any stocked item.

For advanced warehouse scenarios see: [Cycle Counting](../../warehousing/cycle-counting.md).

## Create a counting group
1. Go to **Inventory management > Setup > Inventory > Counting groups**.
2. Select **New**.
3. In the **Counting group** field of the new row, type a value.
4. In the **Name** field, type a value.
5. In the **Counting code** field, select an option.

    - **Manual** – Includes lines every time you run the job. In other words, you decide the counting interval for the counting group.  
    - **Period** – Includes lines for the period in the counting journal when the period interval has expired.  
    - **Zero in stock** – If on-hand inventory reaches zero (0), lines are generated in the counting journal when the job is run. If the on-hand inventory reaches 0 after a count, lines are generated the next time that you start the count.  
    - **Minimum** – Inserts lines in the counting journal if the on-hand inventory is equal to or less than the minimum that is specified.  
    - Optional: If you have specified **Period** in the **Counting code** field, you must type the interval for the period in the **Counting period** field. The unit for intervals is days.  
    - When you run the job for creating new lines in the counting journal, new lines are created at the interval specified in this field, regardless of how often you run the same job. For example, if **Counting period** is set to 7, and journal lines were last generated for a count on January 1, if another job is started on January 5, seven days have not passed and so no lines are generated in the journal for that period interval. If you start the job again on January 8, lines are generated for the period in the counting journal, because 7 days have passed.  

6. Select **Save**.

## Create a counting journal name
1. Go to **Inventory management > Setup > Journal names > Inventory**.
2. Select **New**.
3. In the **Name** field, type a value.
4. In the **Description** field, type a value.
5. In the **Journal type** field, select **Counting**. Optional: you can select a different voucher series ID if you want a specific number sequence for the voucher IDs generated when creating counting journals. Voucher series are created in the **Number sequences** page.  
6. In the **Detail level** field, select an option.  

    - This is the level of detail that is applied when the journal is posted.  
    - Optional: you can change the value in the Reservation field. This is the method used to reserve items during counting.   
    - **Manual** – The items are reserved manually in the Reservation form.  
    - **Automatic** – The order quantity is reserved from the available, on-hand inventory for the item.   
    - **Explosion** – The reservation is part of the master planning of the transaction.  

7. Select **Save**.

## Set standard counting journal name
1. Go to **Inventory management > Setup > Inventory and warehouse management parameters**.
2. Select the **Journals** tab.
3. In the drop down menu of the **Counting** field, select the journal you previously created. This journal will then be the default journal name for inventory journals of the **Counting** type.  
4. Select the **General** tab. Optional: Select this option to lock an item during the counting process to prevent updates for packing slips, picking lists, or picking list registrations.  

## Set the counting policy for an item
1. Go to **Product information management > Products > Released products**.
2. In the list, select the link for the Item number of the product that you want to set counting policies on. You must select an item that is inventory tracked. A non-stocked product can't be counted. If you are using USMF demo data you can select item A0001.  
3. Select **Edit**.
4. Toggle the expansion of the **Manage inventory** section.
5. In the drop-down menu of the **Counting group** field, select the counting group you previously created. This product will now be included when inventory counting journal lines are created using this counting group.  
6. Select **Save**.

> [!NOTE]
> To avoid double-counting mistakes, items are restricted to be part of only 1 active counting journal at a time. If your company processes require more advanced scenarios, you can relax this constraint and count independently per warehouse, or turn this integrity check off.

## Set the counting policy for an item in a specific warehouse
This configuration enables you to count items independently per warehouse.
1. On the Action Pane, select **Manage inventory**.
2. Select **Warehouse items**.
3. Select **New**.
4. In the drop-down menu of the **Warehouse** field, select the warehouse you want to set up specific counting policies for.
5. In the drop-down menu of the **Counting group** field, select a counting group. You can select a specific counting group that should apply to the item in the specific warehouse you have selected. When counting is performed in that warehouse, this counting policy will override the general counting policy for the item.  
6. Select **Save**.

## Disable the counting status registration
This configuration disables registration of counting status, effectively allowing to place the same item and dimension combination in multiple active counting journals.
1. Go to **Inventory management > Setup > Journal names > Inventory**.
2. Select (or create new) name of journal type **Counting**
3. Set the **Counting status registration policy** to **Disable counting status registration**.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
