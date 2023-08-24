--- 
# required metadata 
 
title: Delegate work items in a workflow
description: If you plan to be out of the office or otherwise unavailable to act on work items, you can delegate, or reassign, your work items to other users. 
author: ChrisGarty
ms.date: 07/07/2020
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: SysUserSetup, WorkflowDelegationUserListLookup   
audience: Application User 
# ms.devlang:  
ms.reviewer: twheeloc
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: cgarty
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Delegate work items in a workflow

[!include [banner](../../includes/banner.md)]


[!INCLUDE [PEAP](../../../../includes/peap-3.md)]

## Manually delegate a work item

To delegate an individual work item, select the **Delegate** option in the **Workflow** menu and then enter the user to be delegated to along with a comment. This will reassign the work item to that user so they can complete it.

## Manually delegate multiple work items

Multiple work items can be delegated together from the **Work items assigned to me** page. The following workflow types are eligible for mass delegation: Purchase agreement approval workflow, Purchase order workflow, Purchase requisition review, and Vendor invoice workflow. The **Delegate multiple work items** feature is disabled by default and can be enabled in **Workspaces > Feature management**. Contact your system administrator for help with enabling this feature.
1.	Go to **Common > Common > Work items > Work items assigned to me**.
2.	Select the work items that will be delegated.
3.	Click the **Delegate work items** menu.
4.	In the **User** field, select the user to delegate the work items to.
5.	In the **Comment** field, enter a comment that explains why you're delegating the work items.
6.	Click the **Delegate work items** button to complete the work item delegation.

## Automatically delegate work items

If you plan to be out of the office or otherwise unavailable to act on work items for a period of time, you can automatically delegate new work items to other users using the **User options** page.

### Set up automatic delegation
1. Go to **Common > Setup > User options**.
2. Click the **Workflow** tab. Make sure the Delegation section is expanded. To configure the system to automatically delegate your work items to other users, you must create delegation rules, which specify when certain types of work items are delegated. Follow these steps to create a delegation rule.  
3. Click **Add**.
4. In the **Scope** field, select an option:
    - All – Delegate all work items that are assigned to you.
    - Module – Delegate only the work items that are related to a specific type of workflow. If you select this option, you must select the type of workflow in the **Name** field.
    - Workflow – Delegate only the work items that are related to a specific workflow. If you select this option, you must select the workflow in the **Name** field.  
5. In the **Name** field:
    - For **Module** scope, select the target module.
    - For **Workflow** scope, select the target workflow.
6. In the **Delegate** field, select the user to delegate the work items to. Use the **Start date/time** and **End date/time** fields to specify when you want the work items to be automatically delegated.  
7. In the **Start date/time** field, enter a date and time.
8. In the **End date/time** field, enter a date and time.
9. Select the **Enabled** check box to activate the delegation rule. 
10. In the **Comment** field, enter a comment that explains why you're delegating the work items.


[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
