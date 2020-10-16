---
# required metadata

title: Set up roles on Work breakdown structure templates
description: This topic provides information about setting up role information on Work breakdown structure templates.
author: Yowelle
manager: AnnBe
ms.date: 09/01/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: ProjProjectsListPage
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 82022
ms.assetid: bd2fb375-84c6-428a-8e54-f0f719045898
ms.search.region: Global
# ms.search.industry: 
ms.author: kfend
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Set up roles on Work breakdown structure templates

[!include [banner](../includes/banner.md)]

Project managers can set up Work breakdown structure (WBS) templates that they can apply when they create a WBS for new projects. Project managers can add roles when they create a template. Use the following procedure to assign a role to a WBS template.

1. Select **Project management and accounting** > **Setup** > **Projects** > **Work breakdown structure templates**.
2. Select **Details** for a selected WBS template.
3. Select a task in the list, and then, in the **Role** field, select a role to assign to the task.

## Work with a WBS

You can create a new WBS, or you can copy a WBS from an existing WBS template. A project manager can easily manage the resources by assigning roles to new tasks on the WBS. Roles can be replaced either after a resource is acquired or after a confirmed resource to work on the task is identified. This flexibility lets project managers perform the following tasks:

- Identify the number of resources that are required for WBS work packages.
- Estimate project costs.
- Determine a preliminary budget.
- Estimate activity duration, based on roles and resources.
- Develop some project management plans, based on the available project information.

Additional options have been added in the WBS to better use the resourcing functionality.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Option</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Resource assignments</td>
<td>View the assigned resources, dates, number of hours, and booking type for tasks on the WBS.</td>
</tr>
<tr class="even">
<td>Auto generate team</td>
<td>Automatically add planned resources by using roles that are associated with a task. Finance automatically suggests planned resources by using multi-criteria decision analysis that is based on roles. After the roles and effort (hours) have been set for the tasks in a WBS, and after the structure has been released, select <strong>Auto generate team</strong>. The required number of planned resources is added to the WBS and the <strong>Project and team scheduling</strong> tab.</td>
</tr>
<tr class="odd">
<td>Resource (drop-down list)</td>
<td>On the <strong>Launch resource assignment</strong> page, you can select resources to hard-book or soft-book, based on the specified duration. You can adjust the view settings to see and set the duration of resource activities. You can select and assign resources at the work package level by using the following options:
<ul>
<li><strong>Accept</strong> – Confirm changes to the resource that is assigned to a task.</li>
<li><strong>Cancel</strong> – Cancel changes to the resource that is assigned to a task.</li>
<li><strong>Assign automatically</strong> – An available staffed resource that has a matching role is automatically selected and assigned to the selected task.</li>
</ul></td>
</tr>
</tbody>
</table>

1. On the **All projects** page, select the **XYZ Upgrade Phase 2** project.
2. Select **Plan** > **Activities** > **Work breakdown structure**.
3. Select **New** to add the following level-one activities to the WBS:

    - Initiating
    - Planning
    - Executing
    - Monitoring and Control
    - Close

4. Set the dates and effort (hours), as shown in the following illustration.

    [![Setting the dates and effort](./media/projectresourcing10.jpg)](./media/projectresourcing10.jpg)

5. Select the **Initiating** task line, and then, in the **Role** field, select **Senior Project Manager**.
6. Select **Publish**.
7. On the same line, in the **Resource** field, select **Daniel Goldschmidt**, and then select **Accept**.
8. Select the **Planning** task line, and then, in the **Role** field, select **Business analyst**.
9. Select **Publish**, and then select **Auto generate team**.
10. In the message box that appears, select **Yes**.
11. In the **Resource** field, verify that the value is **Business analyst 1**.
12. For the **Business analyst 1** resource, open the lookup, and select **Launch resource assignments**. Then select a worker for the task.
13. Select **Soft assign** &gt; **Full capacity**.

    > [!NOTE] 
    > You don't receive a warning that the specified resource is now 2, because the number of resources remains 1.

14. On the **Work breakdown structure** page, validate the resource assignment on the WBS, and then select **Save**.
