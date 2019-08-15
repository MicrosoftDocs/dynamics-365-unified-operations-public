---
# required metadata

title: Work order pools
description: This topic describes how to work with work order pools in Asset Management.
author: josaw1
manager: AnnBe
ms.date: 08/15/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: mkirknel
ms.search.validFrom: 2019-08-15
ms.dyn365.ops.version: 10.0.5


---

# Work order pools


[!include [banner](../../includes/banner.md)]

[!include [banner](../../includes/preview-banner.md)]


You can use work order pools to group work orders that have something in common. For example, you can create work order pools for

- work crews, for example, Maintenance Crew A, Maintenance Crew B  

- professional skills, for example, electricians or plumbers  

- physical locations  

- time schedules, for example, weeks or other periods  


If required, one work order can be placed in many work order pools.


## Create work order pool

In **All work order pools** or **Active work order pools**, you can get an overview of your work order pools and create new pools.

1. Click **Asset management** > **Common** > **Work order pools** > **All work order pools** or **Active work order pools**.

2. Click **New**.

3. Insert a work order pool ID in the **Pool** field and a name in the **Name** field.

4. Select "Yes" on the **Active** toggle button to indicate that the work order pool is active.

5. Select "Yes" on the **Delete work order relations** toggle button if you want work orders to be automatically removed from the work order pool.

6. In the **Delete lifecycle state** field, select the work order lifecycle state. For example, the work order lifecycle state for completing a work order could be set to automatically delete relations to work order pools.

7. You can start adding work orders to your work order pool right away. On the **Work orders** FastTab, click **Add line**.

8. Select a work order in the **Work order** field. The related fields are automatically updated.

9. Repeat steps 7-8 if you want to add more work orders.

10. In the **Sort order** field, you can indicate if the work orders should be carried out in a certain order. Insert numbers 1, 2, 3, and so on to indicate a specific sequence for the selected work orders.

11. Click the **Work orders** button to see a list of all the work orders included in the work order pool.

12. Click the **Capacity load** button to open **Capacity load** to calculate and view capacity load for maintenance schedule, not-scheduled work orders, and scheduled work orders.

13. Click the **Item forecast** button to open **Item forecast** to calculate and view forecasts for items (spare parts and other required items) related to maintenance schedule, not-scheduled work orders, and scheduled work orders.

14. Click the **Work order purchase requisition** button to open the **Work order purchase requisition** list to see a list of purchase requisitions related to the work orders in the work order pool.

15. Click the **Work order purchase** button to open the **Work order purchase** list to see a list of purchase orders related to the work orders in the work order pool.

>[!NOTE]
>When a work order pool is no longer relevant for your work planning, set the **Active** check box for that pool to "No" in the **Work order pool** list view.

Select the **Delete work order relations** check box if you want to delete all work order lines, for example to create an empty pool that you can later use for other work orders. Remember to clear the **Delete work order relations** check box if you want to use the work order pool to create new work order relations later.


![Figure 1](media/22-work-orders.png)


## Add work order to a work order pool

As described in the section above, you can add work orders to a work order pool when you create the pool. You can also add a work order to a work order pool from one of the **All work orders** list.

1. Click **Asset management** > **Common** > **Work orders** > **All work orders** or **Active work orders**.

2. Select the work order in the list, and click **Work order pool**.

3. Select "Add" in the **Add/remove** field.

4. Select the work order pool in the **Pool** field.

5. Click **OK**.

6. After you have added a work order to a work order pool, if you want to place the work order in a specific sequence in the pool: Open one of the work order pools list pages, select the pool and click **Edit**, and adjust the sort order of the work orders included in pool in the **Work order pool** form > **Work orders** FastTab > **Sort order** field.

If you want to remove the selected work order from a work order pool, select "Remove" in step 3.

