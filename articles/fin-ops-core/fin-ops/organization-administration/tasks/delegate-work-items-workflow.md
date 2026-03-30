--- 
title: Delegate work items in a workflow
description: Learn about how to delegate work items ina  workflow, including outlines on manually delegating work individual and multiple work items.
author: ChrisGarty
ms.author: cgarty
ms.topic: how-to
ms.date: 03/10/2026
ms.custom:
ms.reviewer: twheeloc
audience: Application User   
ms.search.region: Global
ms.search.validFrom: 2016-06-30
ms.search.form: SysUserSetup, WorkflowDelegationUserListLookup 
ms.dyn365.ops.version: Version 7.0.0 
---

# Delegate work items in a workflow

[!include [banner](../../includes/banner.md)]

## Manually delegate a work item

To delegate an individual work item, select the **Delegate** option in the **Workflow** menu. Enter the user to delegate to along with a comment. This action reassigns the work item to that user so they can complete it.

## Manually delegate multiple work items

You can delegate multiple work items together from the **Work items assigned to me** page. The following workflow types are eligible for mass delegation: Purchase agreement approval workflow, Purchase order workflow, Purchase requisition review, and Vendor invoice workflow. The **Delegate multiple work items** feature is disabled by default. You can enable it in **Workspaces > Feature management**. Contact your system administrator for help with enabling this feature.

1. Go to **Common > Common > Work items > Work items assigned to me**.
1. Select the work items that you want to delegate.
1. Select the **Delegate work items** menu.
1. In the **User** field, select the user to delegate the work items to.
1. In the **Comment** field, enter a comment that explains why you're delegating the work items.
1. Select the **Delegate work items** button to complete the work item delegation.

## Automatically delegate work items

If you plan to be out of the office or otherwise unavailable to act on work items for a period of time, you can automatically delegate new work items to other users by using the **User options** page.

### Set up automatic delegation

1. Go to **Common > Setup > User options**.
1. Select the **Workflow** tab. Make sure the Delegation section is expanded. To configure the system to automatically delegate your work items to other users, create delegation rules that specify when to delegate certain types of work items. Follow these steps to create a delegation rule.  
1. Select **Add**.
1. In the **Scope** field, select an option:
    - All – Delegate all work items that are assigned to you.
    - Module – Delegate only the work items that are related to a specific type of workflow. If you select this option, you must select the type of workflow in the **Name** field.
    - Workflow – Delegate only the work items that are related to a specific workflow. If you select this option, you must select the workflow in the **Name** field.  
1. In the **Name** field:
    - For **Module** scope, select the target module.
    - For **Workflow** scope, select the target workflow.
1. In the **Delegate** field, select the user to delegate the work items to. Use the **Start date/time** and **End date/time** fields to specify when you want the work items to be automatically delegated.  
1. In the **Start date/time** field, enter a date and time.
1. In the **End date/time** field, enter a date and time.
1. Select the **Enabled** check box to activate the delegation rule.
1. In the **Comment** field, enter a comment that explains why you're delegating the work items.

[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
