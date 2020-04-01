--- 
# required metadata 
 
title: Delegate work items in a workflow
description: If you plan to be out of the office or otherwise unavailable to act on work items, you can delegate, or reassign, your work items to other users. 
author: jasongre
manager: AnnBe 
ms.date: 07/01/2019
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
ms.search.form: SysUserSetup, WorkflowDelegationUserListLookup   
audience: Application User 
# ms.devlang:  
ms.reviewer: sericks
ms.search.scope: Core, Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: jasongre
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Delegate work items in a workflow

[!include [banner](../../includes/banner.md)]

## Manually delegate a work item

To delegate an individual work item, select the **Delegate** option in the **Workflow** menu and then enter the user to be delegated to along with a comment. This will reassign the work item to that user so they can complete it.

## Automatically delegate work items

If you plan to be out of the office or otherwise unavailable to act on work items for a period of time, you can automatically delegate new work items to other users using the **User options** page.

### Set up automatic delegation
1. Go to **Common > Setup > User options**.
2. Click the **Workflow** tab. Make sure the Delegation section is expanded. To configure the system to automatically delegate your work items to other users, you must create delegation rules, which specify when certain types of work items are delegated. Follow these steps to create a delegation rule.  
3. Click **Add**.
4. In the **Scope** field, select an option.
    - All – Delegate all work items that are assigned to you.
    - Module – Delegate only the work items that are related to a specific type of workflow. If you select this option, you must select the type of workflow in the Name field.
    - Workflow – Delegate only the work items that are related to a specific workflow. If you select this option, you must select the workflow in the Name field.  
5. In the **Delegate** field, select the user to delegate the work items to. Use the Start date/time and End date/time fields to specify when you want the work items to be automatically delegated.  
6. In the **Start date/time** field, enter a date and time.
7. In the **End date/time** field, enter a date and time.
8. Select the **Enabled** check box to activate the delegation rule. If you selected **Module** as the Scope, then you must select the module in the Name field. If you selected **Workflow** as the Scope, then you must select the specific workflow to delegate in the Name field.  
9. In the **Comment** field, enter a comment that explains why you are delegating the work items.

