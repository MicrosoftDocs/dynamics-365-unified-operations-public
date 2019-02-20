---
# required metadata

title: Set up and submit general budget reservations to workflow
description: This topic provides information about setting up and submitting general budget reservations to workflow for public sector in Microsoft Dynamics 365 for Finance and Operations.
author: ShylaThompson
manager: AnnBe
ms.date: 02/20/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: shylaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
# ms.assetid: 
ms.search.region: Global
ms.search.industry: Public sector
ms.author: brpotter
ms.search.validFrom: 
ms.dyn365.ops.version: 

---

# Set up and submit general budget reservations to workflow

[!include [banner](../includes/banner.md)]

When a general budget reservation is setup to use workflow, the document must first be submitted and approved through workflow. After it completes workflow it remains editable. The option to Post becomes available but the other controls and fields in the page are locked unless you chose to edit. Note that if you edit an approved reservation, its workflow status is reset to Draft, and the option to Post is no longer available, but the other controls and fields are available. You must resubmit the changed reservation for approval.

The following illustration shows how to set up a general budget reservation workflow. The numbers correspond to the procedures later in this topic.

![General budget reservation workflow setup](media/9d17d77d3b80f97f627b38a127fa72c9.jpg)

## 1. Optional: Set up reviewers for general budget reservations

You can set up reviewer workflow elements to route general budget reservations for review. The workflow process uses the specified owner of the project role or financial dimension to determine whom to route the expenditure to.

Alternatively, you can simply assign a specific user or user group as a reviewer when you define the workflow. However, if you have a complex organization, you can improve the efficiency of the approval process by specifying reviewer elements, and you won’t have to change the workflow reviewer assignments every time that a reviewer changes job roles.

## 2. Create a workflow for general budget reservations

General budget reservation workflows are based on reservation type. You can therefore create multiple workflows for general budget reservations.

If the general budget reservation requires a purchase requisition, note that purchase requisitions require their own workflow. The workflow for the purchase requisition must be completed before the general budget reservation can reference it.

To create a workflow for general budget reservations, use the following steps.

1.  Go to **Budgeting \> Setup \> Basic budgeting \> Budgeting workflows**.

2.  Click **New**.

3.  On the **Create workflow** page, click the **General budget reservation workflow** template, and then click **Create workflow**.

4.  On the workflow page, under **Approvals** in the **Workflow elements** list, click **Approve general budget reservation**, and then drag it under the Start icon.

5.  Drag the border of the Start icon to create a connecting line to the approval element.

6.  Click the approval element, and then, on the Action bar, click **Basic settings** to configure the element.


## 3. Optional: Configure manual and automated tasks for general budget reservation workflows. 

Complete this step to reflect the approval or review tasks that are part of your business practice:

-   A manual review of a general budget reservation
-   An automated process to evaluate field values for general budget reservation

You can use a combination of these tasks in the same workflow. The difference between a review manual task and an approval workflow element is as follows:

-   If the manual review task is assigned to multiple users, the workflow can continue after any one of those users completes the task.

-   If you assign an approval workflow element to multiple users, you can specify whether all those users must approve the document before the workflow can continue.

When defining the steps for the review in the description section of the workflow, you assign the task to a user who is authorized to review the lines that are in the general budget reservation.

## 4. Optional: Create conditional decisions. 

Complete this step if your business processes require different workflow processes depending on the amount of the general budget reservation. You can also create decisions that are based on accounting date, reservation type, reservation title, start or end date, and other criteria.

## 5. Assign participants to workflow elements.

You can associate a workflow element with the following groups of participants.

| **User group**             | **Description**                                                                                                                                                                                                                   |
|----------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Security role participants | Assign the workflow element to a Microsoft Dynamics 365 security role. You might use this option if a group of workers can approve general budget reservations and it doesn’t matter which person approves a particular document. |
| User group participants    | Assign the workflow element to a Microsoft Dynamics 365 user group. You might use this option if a group of workers can approve general budget reservations and anyone in that group can approve a particular document.           |

You can also have the workflow element assigned based on a hierarchy or user.

## 6. Save the workflow.

When you have finished adding elements, use the following steps to check it for errors and then save it.

The Errors and warnings pane, located at the bottom of the workflow editor, displays messages that are generated for the workflow. To locate the element where an error or warning occurs, double-click the error or warning message. All errors and warnings must be resolved before you can make the workflow active.

1.  When the workflow is completed and error-free, click **Save and close**. Click **OK** in the **Save workflow** dialog.

2.  If you want to activate the workflow now, click **OK** in the **Activate workflow** dialog

    >   –or–

    >   If you want to activate the workflow later, do the following at any time:

3.  Go to **Budgeting \> Setup \> Basic budgeting \> Budgeting workflows**.

4.  Select the workflow you created.

5.  On the Action bar, in the **Manage** group, click **Versions**.

6.  Select the version of the workflow that you want.

7.  Click **Make active**, and then click **OK**.

## Submit to workflow

To submit a general budget reservation to workflow, you must be the preparer. All required fields must be filled in, and the budget reservation must contain at least one line item before it can be submitted. The reservation must have a workflow status of Draft.

To submit a general budget reservation to workflow, follow these steps.

1.  Go to **Budgeting \> General budget reservations**.

2.  Select the budget reservation that you want to submit to workflow.

3.  Click **Submit** in the Action bar.

4.  Add a note in the **Comment** field if you want, and then click **Submit**. The budget reservation status will move to the next step of the workflow.

5.  The **Submit** button in the Action bar changes to a **Workflow** dropdown. You can click it at any time to do the following:

    -   View the history and see where the document stands in the workflow process.

    -   If the reservation is in workflow, recall the workflow status to **Draft** status, make any changes you want to the reservation, and then resubmit the amended reservation to workflow.

6.  As the reservation moves through workflow, the reservation status and workflow status change and are reflected in the header of the general budget reservation.

7.  When the workflow is completed and the reservation status is set to **Approved**, the document can then be posted.
