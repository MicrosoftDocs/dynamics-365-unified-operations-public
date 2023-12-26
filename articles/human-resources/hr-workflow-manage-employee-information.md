---
# required metadata

title: Use workflows to manage employee information
description: This article explains how you can use workflows to manage employee information. 
author: twheeloc
ms.date: 07/12/2023
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

You can associate a workflow with any position hierarchy that you configure. Two hierarchy types are used for workflow routing: **Managerial** and **Configurable**.

- A **Managerial** hierarchy represents the reporting structure of the company or organization. For more information about this hierarchy type, see [Reports-to position](hr-personnel-positions.md#reports-to-position).
- A **Configurable** hierarchy represents a matrix or custom hierarchy. For more information about this hierarchy type, see [Relationships](hr-personnel-positions.md#relationships).

### Managerial hierarchy example

You might configure a workflow so that when an employee submits a purchase request for a new computer, the request is routed to the employee's manager and skip-level manager. When you configure the workflow step, set the **Assignment type** field to **Hierarchy**. The **Hierarchy type** tab then becomes available. For this example, select the **Managerial** hierarchy.

### Configurable hierarchy example

If a position is associated with a matrix reporting hierarchy, you can configure a workflow that routes expenses for a specific project to the project lead instead of the employee's manager. In this case, set the **Assignment type** field to **Hierarchy**. Then, on the **Hierarchy type** tab, select the **Configurable** hierarchy. After the workflow is set up, select the **Associate** hierarchy on the **Workflow setup** page to select the hierarchy that should be used for the workflow routing.

> [!IMPORTANT]
> When a document, transaction, or master record is submitted for workflow approval, the submitter's primary position will be used to determine who the document should be routed to next.

### Hierarchy setting in Workflow parameters

1. On the **Workflow parameters** page, go to **Hierarchy routing**.
2. By default, the **Use position hierarchy** option is set to **No**. In this case, the workflow will use the worker's primary position when it navigates the hierarchy. Set the option to **Yes** to make the workflow use the position's parent when it navigates the hierarchy.

### Additional example 

Employee Grace Sturman has two positions: consultant and trainer. Grace's primary position is trainer. When she isn't training new employees, she's available for consulting work. Through her primary position, Grace reports to Claire, the director of human resources. Claire reports to Charlie. For her consultant position, Grace has multiple dotted-line relationships, depending on the project.

Grace's company creates workflow routing rules that are based on a **Configurable** hierarchy (matrix/project-based hierarchies). This hierarchy uses Grace's consultant position. If the **Use position hierarchy** option is set to **No**, when a document is routed to Grace for her approval, the workflow will look at her primary position (trainer) to determine where the document should be routed next. In this case, it will be routed first to Claire and then to Charlie. If the option is set to **Yes**, and the workflow uses a **Configurable** hierarchy, the workflow will look at Grace's consultant position and the reporting relationship to determine where the document should be routed next.

### Configure multiple approvers

If a workflow requires the approval of multiple users, the separate approval processes can be combined into a single approval process that has multiple steps. The completion policy can be set to **All approver** or **Single approver**.

For example, the completion policy for an approval process is set to **Single approver**. Employee Sam submits a workflow that requires the approval of line manager Brian and HR manager Christine. If Brian is the first person to respond, his action is applied to the document. If Brian rejects the document, it's returned to Sam, and the status is **Rejected**. If Brian approves the document, it's forwarded to Christine for review.

For more information, see [Configure approval steps in a workflow](../fin-ops-core/fin-ops/organization-administration/configure-approval-step-workflow.md).

To configure the workflow, follow these steps.

1. Create a single approval process that has multiple steps.
2. Create the approval process steps. For the previously described example, the approval process has two steps: one for the line manager approval and one for the HR manager approval.
3. Set the **Completion Policy** field to **All approver** or **Single approver**.

### Configure a Human resources workflow
To configure a basic workflow that is started when employees request changes to their personal identification, follow these steps.

1.  On the **Human resources workflows** page, select **New**.
2.  In the list of available workflows, select **Identification numbers**.
3.  Select **Run** to open the Workflow designer, and then enter your user name and password.
4.  Move the **Approve identification number** element from the list of workflow elements to the designer canvas.
5.  Connect the approval element to **Start** and **Finish**.
6.  Double-tap (or double-click) **Approve element**, select and hold (or right-click), and then select **Properties**.
7.  Follow these steps to add work item instructions:

    1.  Select **Assignment**, and then select **Hierarchy** under the assignment type.
    2.  Under the **Hierarchy** selection, select **Configurable hierarchy**.
    3.  Add a stop condition, and close the page.

8.  Complete any additional instructions.
9.  Select **Save and close**. Activate the new workflow when the dialog box opens, and select **Make active**.
10. Go to **Human Resources** &gt; **Positions** &gt; **Position hierarchy types**.
11. Select **Matrix**.
12. Add the **Worker identification number** workflow to the list.

## Additional resources

[View and manage address changes](hr-personnel-view-address-changes.md) 

[!INCLUDE[footer-include](../includes/footer-banner.md)]
