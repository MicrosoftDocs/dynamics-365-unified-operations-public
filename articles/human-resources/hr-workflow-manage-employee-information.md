---
# required metadata

title: Use workflows to manage employee information
description: This topic explains how you can use workflows to manage employee information. 
author: twheeloc
ms.date: 11/03/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: WorkflowParametersAdmin, WorkflowtableListPageRnr, WorkflowStatus
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.search.scope: Human Resources
# ms.tgt_pltfrm: 
ms.custom: 269074
ms.assetid: 426c6127-42ee-4163-8dd0-b2867f95581d
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611

---

# Use workflows to manage employee information


[!INCLUDE [PEAP](../includes/peap-1.md)]

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

This topic explains how you can use the workflow capability for Human resources to manage employee information. For example, you can associate a workflow with a position and configure an approval workflow that is started when employees change their record.

The workflow capability for Human resources provides numerous workflows for managing human resources activities. Additionally, numerous options are available so that you can modify specific workflows and associate them with a reporting hierarchy. Workflows are available to help manage changes to several types of employee information. You can associate a workflow with a position. Then, if employees change their employee record, a workflow is started that requires approval before the new information is saved. Workflows are predefined for the following types of information to help you efficiently manage changes and keep your employees' data accurate:

-   Identification numbers
-   Courses
-   Education
-   Image
-   Loaned items
-   Professional experience
-   Project experience
-   Skills
-   Positions of trust
-   Human resources actions
-   Course registration

When employees are hired, transferred, or terminated, the workflow can include a review process. In this way, a document can be revised, or the terms of an action can be defined as part of the workflow. When the review process is completed, the document or action is completed, and the workflow moves to a final approval step.

## Associate a workflow with a position hierarchy
You can associate a workflow with any hierarchy that you configure. For example, if a position is associated with a matrix reporting hierarchy, you might configure a workflow that routes expenses for a specific project to the project lead instead of the manager of the employee who is associated with that position. To create a new workflow or modify an existing workflow, on the **Human resources workflow** page, select **New**. Select a workflow in the list to open the Workflow designer. You can use the designer to create a new workflow or change the steps in an existing workflow. When you change an existing workflow, your changes are saved as a new version. Therefore, you can always go back to a previous version if you have to.

## Configure a Human resources workflow
To configure a basic workflow that is started when employees request changes to their personal identification, follow these steps.

1.  On the **Human resources workflows** page, select **New**.
2.  In the list of available workflows, select **Identification numbers**.
3.  Select **Run** to open the Workflow designer, and then enter your user name and password when you're prompted.
4.  Drag the **Approve identification number** element from the list of workflow elements to the designer canvas.
5.  Connect the approval element to **Start** and **Finish**.
6.  Double-tap (or double-click) **Approve element**, select and hold (or right-click), and then select **Properties**.
7.  Follow these steps to add work item instructions:

    1.  Select **Assignment**, and then select **Hierarchy** under the assignment type.
    2.  Under the **Hierarchy** selection, select **Configurable hierarchy**.
    3.  Add a stop condition, and close the page.

8.  Complete any additional instructions (no additional warnings should exist).
9.  Select **Save and close**. Activate the new workflow when the dialog box opens, and select **Make active**.
10. Go to **Human Resources** &gt; **Positions** &gt; **Position hierarchy types**.
11. Select **Matrix**.
12. Add the **Worker identification number** workflow to the list.

## Additional resources

[View and manage address changes](hr-personnel-view-address-changes.md) 





[!INCLUDE[footer-include](../includes/footer-banner.md)]
