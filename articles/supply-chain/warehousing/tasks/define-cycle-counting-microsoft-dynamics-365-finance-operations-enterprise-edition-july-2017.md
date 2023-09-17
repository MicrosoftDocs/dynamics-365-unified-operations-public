--- 
# required metadata 
 
title: Define cycle counting 
description: Cycle counting is a warehouse process that you can use to audit on-hand inventory items. 
author: Mirzaab
ms.date: 08/12/2019
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
ms.search.form: WHSRFMenuItemCycleCount, WHSCycleCountThreshold, WHSCycleCountPlan, WHSCycleCountPlanListPage, WHSParameters, WHSRFMenu, WHSRFMenuItem
audience: Application User 
# ms.devlang:  
ms.reviewer: kamaybac
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: mirzaab
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Define cycle counting 

[!include [banner](../../includes/banner.md)]

Cycle counting is a warehouse process that you can use to audit on-hand inventory items. This task recording shows how to set up the default counting work priority, enable a mobile device menu item to process both picking and counting operations, enable a counting threshold trigger when a location becomes empty, and enable a cycle counting plan for a specific item in a specific warehouse. Typically, these tasks are performed by a warehouse manager. You can go through this procedure in the USMF demo data company or in your own data.


## Set the priority of counting work
1. Go to **Warehouse management > Setup > Warehouse management parameters**.
2. Click the **Cycle counting** tab.
3. In the **Default cycle count work priority** field, enter a number. This step changes the priority of cycle counting work compared to other types of work in the warehouse. By entering a number that is lower than the number for other types of work, you raise the priority of the cycle counting work.  
4. Click **Save**.
5. Close the page.

## Enable the mobile device
1. Go to **Warehouse management > Setup > Mobile device > Mobile device menu items**.
2. Click **New**.
3. In the **Menu item name** field, type a value.
4. In the **Title** field, type a value.
5. In the **Mode** field, select 'Work'.
6. Set the **Use existing work** option to Yes. When you set this option to Yes, the system will look for existing work when the mobile device menu item is used.  
7. In the **Directed by** field, select 'System directed'. When "System directed" is selected, the warehouse worker will be directed to open work that is in defined work classes. (We will create these work classes next.)  
8. Expand the **Work classes** fastTab. Next, we will create two work classes that will be used with this mobile device menu item. When the menu item is used, these work classes will be queried, and the work that has the highest priority will be shown to the user.  
9. Click **New**.
10. In the**Work class ID** field, select a value.
11. Click **New**.
12. In the **Work class ID** field, select a value.
13. In the **Action Pane**, click **Save**.
14. Close the page.
15. Go to **Warehouse management > Setup > Mobile device > Mobile device menu**.
16. In the list, find and select the desired record.
17. In the tree, select 'the menu item that you just created'.
18. Click **Edit**.
19. Click the arrow to add the menu item to the menu.
20. Click **Save**.

## Create a counting threshold
1. Go to **Warehouse management > Setup > Cycle counting > Cycle count thresholds**.
2. Click **New**.
3. In the **Cycle counting threshold ID** field, type a value.
4. Set the **Process cycle counting immediately** option to Yes.
5. In the **Description** field, type a value.
6. Click **Save**.
7. Click **Select locations**.
8. In the list, mark the selected row.
9. In the **Criteria** field, select a value.
10. Click **OK**.
11. Close the page.

## Create a cycle count plan
1. Go to **Warehouse management > Setup > Cycle counting > Cycle count plans**.
2. Click **New**.
3. In the **Cycle counting plan ID** field, type a value.
4. In the **Description** field, type a value.
5. In the **Maximum number of cycle counts** field, enter a number.
6. Click **Save**.
7. Click **Select locations**.
8. In the list, mark the selected row.
9. In the **Criteria** field, select a value.
10. Click **OK**.
11. In the **Days between cycle counting** field, enter a number. For example, if the **Days between cycle counting** field is set to 5, cycle counting work will be created every five days. However, if cycle counting work is processed on day three, the next cycle counting work will be created five days after the last cycle counting was processed, on day 8.  
12. Click **Save**.
13. Click **New**.
14. In the **Sequence number** field, enter a number. The sort is from the smallest number to the largest number. The value must be more than 0 (zero).  
15. In the list, mark the selected row.
16. In the **Description** field, type a value.
17. Click **Save**.
18. Click **Define product** query.
19. In the list, mark the selected row.
20. In the **Criteria** field, enter or select a value.
21. Click **OK**.
22. Close the page.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]