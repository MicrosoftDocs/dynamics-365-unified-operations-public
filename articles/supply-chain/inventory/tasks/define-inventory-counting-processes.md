---
# required metadata

title: Define inventory counting processes
description: This procedure walks you through the configuration of basic inventory counting processes by creating a counting group and a counting journal.
author: MarkusFogelberg
manager: AnnBe
ms.date: 11/14/2016
ms.topic: business-process
ms.prod:  
ms.service: dynamics-ax-applications
ms.technology:  

# optional metadata

# ms.search.form:   
audience: Application User
# ms.devlang:  
ms.reviewer: YuyuScheller
ms.search.scope: Operations
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
ms.search.industry: Distribution
ms.author: mafoge
ms.search.validFrom: 2016-06-30
ms.dyn365.ops.version: AX 7.0.0
---
# Define inventory counting processes

[!include[task guide banner](../../includes/task-guide-banner.md)]

This procedure walks you through the configuration of basic inventory counting processes by creating a counting group and a counting journal. It also shows you how to enable counting policies on a warehouse and item level. These tasks would typically be carried out by a warehouse supervisor. It is a prerequisite to have some existing released products and warehouses. If you're using a demo data company, you can run this procedure in the USMF company with any stocked item.


## Create a counting group
1. Go to Inventory management > Setup > Inventory > Counting groups.
2. Click New.
3. In the Counting group field, type a value.
4. In the Name field, type a value.
5. In the Counting code field, select an option.
    * Manual – Includes lines every time you run the job. In other words, you decide the counting interval for the counting group.  Period – Includes lines for the period in the counting journal when the period interval has expired.   Zero in stock – If on-hand inventory reaches zero (0), lines are generated in the counting journal when the job is run. If the on-hand inventory reaches 0 after a count, lines are generated the next time that you start the count.   Minimum – Inserts lines in the counting journal if the on-hand inventory is equal to or less than the minimum that is specified.  
    * Optional: If you have specified Period in the Counting code field, you must type the interval for the period in the Counting period field. The unit for intervals is days.  
    * When you run the job for creating new lines in the counting journal, new lines are created at the interval specified in this field, regardless of how often you run the same job. For example, if Counting period is set to 7, and journal lines were last generated for a count on January 1, if another job is started on January 5, seven days have not passed and so no lines are generated in the journal for that period interval. If you start the job again on January 8, lines are generated for the period in the counting journal, because 7 days have passed.  
6. Click Save.

## Create a counting journal name
1. Go to Inventory management > Setup > Journal names > Inventory.
2. Click New.
3. In the Name field, type a value.
4. In the Description field, type a value.
5. In the Journal type field, select 'Counting'.
    * Optional: you can select a different voucher series ID if you want a specific number sequence for the voucher IDs generated when creating counting journals. Voucher series are created in the Number sequences page.  
6. In the Detail level field, select an option.
    * This is the level of detail that is applied when the journal is posted.  
    * Optional: you can change the value in the Reservation field. This is the method used to reserve items during counting.   
    * Manual – The items are reserved manually in the Reservation form.   Automatic – The order quantity is reserved from the available, on-hand inventory for the item.   Explosion – The reservation is part of the master planning of the transaction.  
7. Click Save.

## Set standard counting journal name
1. Go to Inventory management > Setup > Inventory and warehouse management parameters.
2. Click the Journals tab.
3. In the Counting field, click the drop-down button to open the lookup.
4. Select the journal you previously created.
    * This journal will then be the default journal name for inventory journals of the Counting type.  
5. Click the General tab.
    * Optional: Select this option to lock an item during the counting process to prevent updates for packing slips, picking lists, or picking list registrations.  

## Set the counting policy for an item
1. Go to Product information management > Products > Released products.
2. In the list, click on the link for the Item number of the product that you want to set counting policies on.
    * Note that you need to select an item that is inventory tracked. A non-stocked product can't be counted. If you are using USMF demo data you can select item A0001.  
3. Click Edit.
4. Toggle the expansion of the Manage inventory section.
5. In the Counting group field, click the drop-down button to open the lookup.
6. In the list, click on the counting group you previously created.
    * This product will now be included when inventory counting journal lines are created using this counting group.  
7. Click Save.

## Set the counting policy for an item in a specific warehouse
1. On the Action Pane, click Manage inventory.
2. Click Warehouse items.
3. Click New.
4. In the Warehouse field, click the drop-down button to open the lookup.
5. In the list, select the warehouse you want set up specific counting policies for.
6. In the Counting group field, click the drop-down button to open the lookup.
7. In the list, select a counting group
    * Here you can select a specific counting group that should apply to the item in the specific warehouse you have selected. When counting is performed in that warehouse, this counting policy will override the general counting policy for the item.  
8. Click Save.
