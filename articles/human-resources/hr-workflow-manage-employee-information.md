---
# required metadata

title: Use workflows to manage employee information
description: This article explains how you can use workflows to manage employee information. 
author: twheeloc
ms.date: 11/03/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: WorkflowParametersAdmin, WorkflowtableListPageRnr, WorkflowStatus
# ROBOTS: 
audience: Application User
# ms.devlang: 

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

This article explains how you can use the workflow capability for Human resources to manage employee information. For example, you can associate a workflow with a position and configure an approval workflow that is started when employees change their record.

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
You can associate a workflow with any position hierarchy that you configure. There are two hierarchy types that are used for workflow routing: **Managerial** and **Configurable**.

A **Managerial** hierarchy represents the reporting structure of the company or organization. For more information about this hierarchy type, go to [Positions](hr-personnel-positions.md#reports-to-position).

A **Configurable** hierarchy represents a matrix or custom hierarchy. For more information about this hierarchy type, see [Positions]((hr-personnel-positions.md#relationships). 

## Managerial hierarchy example 

If submitting a purchase request for a new computer, a workflow could be configured that routes an employee’s purchase request to their manager, and their skip level manager. When configuring the **Assignment type** of the workflow step, select **Hierarchy**. Once the **Assignment type** is set to **Hierarchy**, the **Hierarchy type** tab is available. For this example, select **Managerial** hierarchy.

## Configurable hierarchy example 

If a position is associated with a matrix reporting hierarchy, you might configure a workflow that routes expenses for a specific project to the project lead instead of the manager of the employee. Using the same steps as above, the assignment type would be set to hierarchy. In this example, select **Configurable** hierarchy. Once the workflow is setup, select **Associate** hierarchy on the **Workflow setup** page to select the hierarchy that should be used for the workflow routing.

>[!Important] 
>When submitting a document, transaction or master record for workflow approval, the submitter’s primary position will be used when determining who the document should be routed to next.  

## Hierarchy setting in Workflow parameters

On the **Workflow parameters** page, follow these steps:
1. Go to **Hierarchy routing**. 
2. The option **Use position hierarchy** defaults as **No**. 
3. When this option is set to **Yes**, the workflow will use the positions parent when navigating the hierarchy instead of using the primary position of the worker.

## Example with the option off and on:

Employee Grace Sturman has two positions; Consultant and Trainer. Graces’s primary position is trainer. However, when she is not training new employees, she’s available for some consulting work. Grace reports to Claire the director of human resources via her primary position. Claire reports to Charlie. For her consulting position, she has multiple dotted line relationships, depending on the project.

Grace’s company creates workflow routing rules based on a **Configurable** hierarchy (matrix/project based hierarchies) – which uses Grace’s consultant position. With the parameter **Off**, a document will be routed to Grace for her approval. The workflow will look at her primary position to see where the document should be routed next. In this instance, it would be routed to Claire, and then onto Charlie.

If the parameter is **On** and the workflow uses a configurable hierarchy, the workflow will look at Grace’s consulting position, and the reporting relationship, to determine who should receive the document next.

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
