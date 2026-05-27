--- 
title: Define cycle counting 
description: Learn about cycle counting, which is a warehouse process that you can use to audit on-hand inventory items, including a step-by-step process. 
author: Mirzaab
ms.author: mirzaab
ms.topic: how-to
ms.date: 5/27/2026
ms.custom:
ms.reviewer: kamaybac
ms.search.form: WHSRFMenuItemCycleCount, WHSCycleCountThreshold, WHSCycleCountPlan, WHSCycleCountPlanListPage, WHSParameters, WHSRFMenu, WHSRFMenuItem
---

# Define cycle counting 

[!include [banner](../../includes/banner.md)]

Cycle counting is a warehouse process that you can use to audit on-hand inventory items. This task recording shows how to set up the default counting work priority, enable a mobile device menu item to process both picking and counting operations, enable a counting threshold trigger when a location becomes empty, and enable a cycle counting plan for a specific item in a specific warehouse. Typically, a warehouse manager performs these tasks. You can go through this procedure in the USMF demo data company or in your own data.


## Set the priority of counting work

1. Go to **Warehouse management > Setup > Warehouse management parameters**.
1. Select the **Cycle counting** tab.
1. In the **Default cycle count work priority** field, enter a number. This step changes the priority of cycle counting work compared to other types of work in the warehouse. By entering a number that's lower than the number for other types of work, you raise the priority of the cycle counting work.  
1. Select **Save**.
1. Close the page.

## Enable the mobile device

1. Go to **Warehouse management > Setup > Mobile device > Mobile device menu items**.
1. Select **New**.
1. In the **Menu item name** field, enter a value.
1. In the **Title** field, enter a value.
1. In the **Mode** field, select **Work**.
1. Set the **Use existing work** option to **Yes**. When you set this option to **Yes**, the system looks for existing work when the mobile device menu item is used.  
1. In the **Directed by** field, select **System directed**. When you select **System directed**, the warehouse worker is directed to open work that is in defined work classes. (You create these work classes next.)  
1. Expand the **Work classes** FastTab. Next, you create two work classes to use with this mobile device menu item. When the menu item is used, these work classes are queried, and the work with the highest priority is shown to the user.    
1. Select **New**.
1. In the **Work class ID** field, select a value.
1. Select **New**.
1. In the **Work class ID** field, select a value.
1. In the Action Pane, select **Save**.
1. Close the page.
1. Go to **Warehouse management > Setup > Mobile device > Mobile device menu**.
1. In the list, find and select the desired record.
1. In the tree, select **the menu item that you just created**.
1. Select **Edit**.
1. Select the arrow to add the menu item to the menu.
1. Select **Save**.

## Create a counting threshold

1. Go to **Warehouse management > Setup > Cycle counting > Cycle count thresholds**.
1. Select **New**.
1. In the **Cycle counting threshold ID** field, enter a value.
1. Set the **Process cycle counting immediately** option to **Yes**.
1. In the **Description** field, enter a value.
1. Select **Save**.
1. Select **Select locations**.
1. In the list, select the row.
1. In the **Criteria** field, select a value.
1. Click **OK**.
1. Close the page.

## Create a cycle count plan

1. Go to **Warehouse management > Setup > Cycle counting > Cycle count plans**.
1. Select **New**.
1. In the **Cycle counting plan ID** field, enter a value.
1. In the **Description** field, enter a value.
1. In the **Maximum number of cycle counts** field, enter a number.
1. Select **Save**.
1. Select **Select locations**.
1. In the list, select the row.
1. In the **Criteria** field, select a value.
1. Click **OK**.
1. In the **Days between cycle counting** field, enter a number. For example, if you set the **Days between cycle counting** field to 5, the cycle counting work is created every five days. However, if cycle counting work is processed on day three, the next cycle counting work is created five days after the last cycle counting was processed, on day 8.    
1. Select **Save**.
1. Select **New**.
1. In the **Sequence number** field, enter a number. The sort is from the smallest number to the largest number. The value must be more than 0 (zero).  
1. In the list, select the row.
1. In the **Description** field, enter a value.
1. Select **Save**.
1. Select **Define product** query.
1. In the list, select the row.
1. In the **Criteria** field, enter or select a value.
1. Click **OK**.
1. Close the page.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]