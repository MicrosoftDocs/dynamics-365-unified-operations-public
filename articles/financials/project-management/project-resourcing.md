---
# required metadata

title: Project resourcing
description: This topic provides information about project resourcing.
author: KimANelson
manager: AnnBe
ms.date: 09/14/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
ms.search.scope: Core, AX 7.0.0, Operations, UnifiedOperations
# ms.tgt_pltfrm: 
ms.custom: 82022
ms.assetid: bd2fb375-84c6-428a-8e54-f0f719045898
ms.search.region: Global
# ms.search.industry: 
ms.author: knelson
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Project resourcing

[!include[banner](../includes/banner.md)]

This topic provides information about project resourcing.

One challenge for project managers and resource managers during the project planning stage is resource allocation, where they must determine and reserve the correct resource to work on a project. In Microsoft Dynamics 365 for Finance and Operations, Enterprise edition, resourcing capabilities for projects let you define roles that are treated as temporary resources that can be reserved for a specific engagement or part of an engagement. This type of resourcing lets project managers and resource managers complete the following tasks:

- Define a role that has the required competencies, so that it's easy to match resources.
- Use roles to define an initial engagement schedule that is based on reserved resources.
- Estimate costs and determine an initial budget, based on assigned roles and resources for a project.
- Use roles to estimate the number of resource reservations that are required for each engagement.
- Estimate the number of resources that are required for the whole life cycle of a project.
- Draft a work breakdown structure (WBS) by using the initial resource assignments.

[![Project life cycle](./media/projectresourcing02-1024x812.jpg)](./media/projectresourcing02.jpg)

As project planning proceeds, planned resources can be replaced with staffed resources. The project manager can also go back and update the resourcing reservations during any project stage.

## Set up project resources
You must set up a calendar and associate it with an employee or a worker. The calendar is used to schedule the project and the working time of the resources that are reserved for the project. During calendar setup, project managers can do resource leveling as part of resource optimization. Based on the calendar schedule, restrictions can be put on resources. You can set up a calendar on the **Calendars** page.

When you set up a worker as a project resource, you can select from workers who work in the company that you're setting up resources for. Alternatively, you can select workers from other companies in your organization. These workers are known as intercompany resources.

The following procedures explain how to set up a worker as a project resource in your company and how to set up an intercompany project resource.

### Set up a worker as a project resource

1. On the **Workers** page, in the **Workers** list, select the worker that you're adding as a project resource, and open the worker record.
2. On the Action Pane, select **Project** &gt; **Setup** &gt; **Project setup**.
3. Select a calendar, and then close the page.

You can also specify default projects for a resource as a type of pre-assignment. Pre-assignments can be used when the resource manager or project manager knows which projects the resource will be working on in advance. Pre-assignments can also be based on the request of a project sponsor or customer. To pre-assign a project, on the **Assign projects** page, on the **Projects** tab, in the **Remaining projects** list, select the appropriate project.

### Set up an intercompany resource

When you set up a worker as an intercompany resource, you must complete the setup in both the lending company and the borrowing company.

**In the lending company**

1. In Finance and Operations, verify that the lending company is selected, and then complete the procedure in the previous section, "Set up a worker as a project resource."
2. On the **Intercompany accounting** page, select **New**.
3. In the **Legal entity ID** field, select the lending company. Fill in the remaining fields as appropriate, and then select **Save**.
4. On the **Transfer price** page, select **New**.
5. In the **Borrowing legal entity** field, select the appropriate company.
6. To lend the borrowing company only the resource that you created at the beginning of this section, in the **Resource** field, select the name of the resource that you created. To make all resources in the lending company available to the borrowing company, leave the **Resource** field blank.
7. On the **Project management and accounting parameters** page, on the **Intercompany** tab, set the **Enable intercompany resource scheduling and timesheets** option to **Yes**.

**In the borrowing company**

- On the **Resources list** page, in the search filter, enter the name of the resource that you created for the lending company, to verify that the name is included in the resource list for the borrowing company.

## Manage resource competencies
Resource competencies are an essential part of resource management. Competencies can be used as a baseline to determine resources that have the correct balance of skills, education, certification, and project experience. You should set up this information for each resource and update it on a regular basis. In this way, you can maximize capabilities when specific resource competencies are matched during project resource assignment.

[![Examples of skills, certifications, education, and project experience](./media/projectresourcing06-1024x383.jpg)](./media/projectresourcing06.jpg)

The following procedures explain how to set up some of the competencies for a resource.

To set up competencies for a worker, you can use either the **Workers** list page in Human resources or the **Resources** list page in Project management and accounting. For the following procedures, the **Workers** list page in Human resources is used.

### Set up competencies: Certificates

1. On the **Workers** list page, select the line for the worker to add certificate information for.
2. On the Action Pane, on the **Worker** tab, in the **Competencies** group, select **Certificates**.
3. Select **New**, and then, in the **Certificate type** field, select **PMP**.
4. In the **Start date** field, select **10/1/2015**, and select **Save**.

### Set up competencies: Skills

1. On the **Workers** list page, make sure that the worker that you used in the previous procedure is still selected. Then, on the Action Pane, on the **Worker** tab, in the **Competencies** group, select **Skills**.
2. Select **New**.
3. In the **Skill** field, select **Project management**.
4. In the **Level** field, select **5 Expert**.
5. In the **Level date** field, select **1-/14/2014**.
6. In the **Years of experience** field, enter **10**.
7. Select **Save**, and then close the page.

## Create a new project
1. On the **Project management** page, select **New project**, and enter the following values:

    - **Project type:** Time and material
    - **Project name:** XYZ Upgrade Phase 2
    - **Project group:** TM\_WIP
    - **Project contract ID:** 00000002

2. Select **Create project**.

### Assign a resource to a project

1. On the **Workers** page, in the **Workers** list, select the record for the worker that you previously set up competencies for, and open the worker record.
2. On the Action Pane, on the **Project** tab, in the **Setup** group, select **Assign projects**.
3. On the **Resource validation project assignments** page, on the **Projects** tab, in the **Add the project to selected projects** field, filter on the **XYZ Upgrade Phase 2** project.
4. In the **Remaining projects** pane, select a project, and then select the arrow button to add it to the **Selected projects** pane.

You can also assign categories for a resource as you require. The category type is either **Cost** or **Revenue**. The category type is determined by your organization. If no categories are assigned for a resource, Finance and Operations looks up the default category on hour prices for cost and revenue.

### Set up project resource and role characteristics

A project manager can use the project resourcing functionality to create the roles that are required for the project. Roles can be used if confirmed resources are still unknown when resources are being reserved. Roles can be temporarily reserved as planned resources, so that you can continue the project planning stages.

[![Example of a role](./media/projectresourcing05.jpg)](./media/projectresourcing05.jpg) 

**Scenario:** Contoso was hired to complete a Time and material project that has an approved project charter. The junior project manager is still completing the scope of the project. The resource manager is currently identifying specific resources that will be reserved to work on the new project. Because of the critical nature of the project, the project sponsor requested Senior project manager as one of the roles. The resource manager must acquire the new resource and define the role in the system in case the junior project manager requires the resource information during project planning.

The following steps show how the resource manager can set up the Senior project manager role and associate resource characteristics with it. Later, the role can be used to search for available resources that match the required resource competencies.

1. On the **Setup roles** page, select **New**, and enter the following values:

    - **Role ID:** Senior Project Manager
    - **Description:** Senior Project Manager

2. Select **Create**.
3. Select the **Senior Project Manager** role, and then select **Configure characteristics**.
4. In the **Characteristics type** field, select **Skill**.
5. In the **Available characteristics** field, enter the skill to search for.
6. In the **Characteristic type** field, select **Certificate**.
7. In the **Available characteristics** field, enter the certificate type to search for.

### Assign a project resource to a project

1. On the **All projects** page, select the **XYZ Upgrade Phase 2** project.
2. On the **Project team and scheduling** tab, select **Add**.
3. In the **Role** field, select **Team member**.
4. Select **Book from calendar**.
5. On the **Resource availability** page, select **View settings**.
6. On the **Adjust view settings** page, enter the following values:

    - **Format for date range view:** Day
    - **Display availability descriptions:** Yes
    - **Display remaining capacity:** Yes

7. In the list of resources, select a resource.
8. Select **Hard book** and **Full capacity**.


### Assign a resource to a default role

To help project or resource managers can drill down further on the resources that can be reserved for a project. You can associate a default role with an existing resource or a newly acquired resource. For example, when Daniel was hired, he had the experience and skills to fill the Business analyst role. The resource manager assigned this role as Daniel's default role. Therefore, the resource manager added Daniel to a pool of business analysts who are available to work on projects.

During resource reservation, project managers can filter the role resources that are available to work on projects. They can use this information as one criterion when they perform multi-criteria decision analysis during resource fulfillment. They can also add other resource characteristics to the filter to search for resources that have specific skills, education, and experience for a given project.

**Scenario:** An approved project has started, and the Senior project manager role was reserved as a planned resource during the project planning stage. The resource manager has now acquired a resource to fulfill the Senior project manager role.

1. On the **Resources list** page, select **Daniel Goldschmidt**.
2. On the **Resource role** page, select **New**, and enter the following values:

    - **Effective:** Enter the current date.
    - **Expiration:** Enter **Never**.
    - **Role:** Enter **Senior Project Manager**.

3. Select **Save**, and then close the page.
4. On the **Competencies** tab, add the **ProjectMgmt** skill and the **PMP** certificate.

## Set up role-based pricing
All cost, sales, and transfer prices can be set up for roles.

1. On the **Sales price (hour)** page, select **New**, and enter an effective date.
2. In the **Role** column, select a role.
3. In the **Pricing** column, enter a price for the selected resource role.

## Form a project team
To use the roles that were previously set up in a project, a project manager must associate the roles with the project. Multiple roles can be assigned for a project. To prevent confusion, Finance and Operations automatically labels these roles during reservation. For example, if the project manager requires three software engineers, three Software engineer roles that have **software engineer 1**, **software engineer 2**, and **software engineer 3** as their labels are automatically generated. If role characteristics were previously set for the role, they are applied as a filter during searches for a resource. Additional characteristics can be added as required to further refine the search.

View settings can also be customized to give a better view of resource availability. There are options to show hourly, daily, weekly, monthly, quarterly, and annual availability. There is also an option to show available and remaining capacity on resources. This option is useful for time management, when you're estimating available time for activities or resource availability.

The project manager can select a role on the page and then, if there is an available resource that fits the requirement, select to reserve a resource to fill the role. Note that the resources don't have to be reserved at this point in the planning stage. When you create a WBS, you can replace roles with staffed resources for the project. If roles are replaced with staffed resources in the WBS, the resource setup automatically updates the project team listing and scheduling.

[![Project team listing that includes both roles and actual resources](./media/projectresourcing03-1024x368.jpg)](./media/projectresourcing03.jpg) 

The project manager has various options for booking a resource for a project, such as **Remaining capacity**, **Full capacity**, **Capacity percentage**, and **Specify hours**. These booking options can be canceled at any time if resource assignments change. Two types of booking are supported:

- **Hard Book** – The resource reservation was approved and confirmed to work on the engagement for the specified duration.
- **Soft book** – The resource reservations was tentatively set to work on the engagement for the specified duration.

The following procedure explains how to create a project team.

### Create a project team

1. On the **All projects** list page, select a project, and then select **Edit**.
2. On the **Project team and scheduling** tab, in the **Schedule end date** field, enter the schedule start date plus one month. For example, if the schedule start date is June 24, 2017 (24/06/2017), enter **24/07/2017**.
3. Select **Add**.
4. In the **Add roles to the project** pane, in the **Role** field, select **Senior Project Manager**.
5. Select **Required competencies**.
6. On the **Choose characteristics** page, the characteristics that you previously set for the Senior project manager role are selected by default. Select **OK**.
7. On the **Add roles to project** page, in the **Number of resources** field, enter **1**.
8. In the **Resource** field, the lookup shows all resources that have the required competencies. Select **Daniel Goldschmidt**, and then select **Create**.
9. On the **Project** page, select **Add**.
10. In the **Add roles to the project** pane, in the **Role** field, select **Team member**. In the **Number of resources** field, enter **5**.
11. Select **Create**.
12. On the **Projects** page, select **Fulfill resource**.

## Resource capacity synchronization
The processes for resource synchronization help guarantee that information for the calendar and base calendar trickles down into project resource scheduling. If the calendar is changed, the processes make the required updates to the scheduling of project resources. The processes also help improve performance, because the calendar's resource information is synchronized in advance. Therefore, updates to resource scheduling information occur more quickly. We recommend that you schedule the processes as a batch instead of one at a time. Otherwise, there is a risk that someone will forget the inclusive dates when the information was last synchronized. If inclusive dates aren't used, gaps can occur during date synchronization.

![Calendar synchronization](./media/projectresourcing04-1024x471.jpg)

### Synchronize resource capacity roll-ups

The synchronization process is designed to synchronize all resource calendar information. This information includes base calendar information about any changes to the project's Resource calendar capacity table. If new resources are added in the project, synchronization helps guarantee that the updated calendar information is available. This synchronization can be done at any time.

We recommend that you use a batch. The options are available during synchronization of capacity reservations.

1. Select **Project management and accounting** &gt; **Periodic** &gt; **Capacity synchronization** &gt; **Synchronize resources capacity roll-ups**.
2. Set the options in the following table.

    | Option      | Description |
    |-------------|-------------|
    | Period code | Optionally select the General ledger date interval code to set the start and end dates for the synchronization process for resource capacity roll-ups. |
    | Start date  | Enter the start date for the synchronization process for resource capacity roll-ups. |
    | End date    | Enter the end date for the synchronization process for resource capacity roll-ups. |

[![Synchronization process](./media/projectresourcing09.jpg)](./media/projectresourcing09.jpg)

## Set up roles on WBS templates
Project managers can set up WBS templates that they can apply when they create a WBS for new projects. Project managers can add roles when they create a template. Use the following procedure to assign a role to a WBS template.

1. Select **Project management and accounting** &gt; **Setup** &gt; **Projects** &gt; **Work breakdown structure templates**.
2. Select **Details** for a selected WBS template.
3. Select a task in the list, and then, in the **Role** field, select a role to assign to the task.

### Work with a WBS

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
<td>Automatically add planned resources by using roles that are associated with a task. Finance and Operations automatically suggests planned resources by using multi-criteria decision analysis that is based on roles. After the roles and effort (hours) have been set for the tasks in a WBS, and after the structure has been released, select <strong>Auto generate team</strong>. The required number of planned resources is added to the WBS and the <strong>Project and team scheduling</strong> tab.</td>
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
2. Select **Plan** &gt; **Activities** &gt; **Work breakdown structure**.
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

## Resource fulfillment for planned resources
A project manager can plan required resource roles for a project. The resource manager will see these planned resources as requests on the **Resource fulfillment** page and can assign actual resources.

1. On the **All projects** page, select the **XYZ Upgrade Phase 2** project.
2. Select **Project**, and then select **Edit**.
3. On the **Project team and scheduling** tab, select **Add**.
4. In the **Add roles** dialog box, select the **Software developer** role.
5. Select **Create**, and then close the project page.
6. On the **Resource fulfillment** page, select **Software developer 1** for the **XYZ Upgrade project Phase 2** project.
7. Select a worker, and then select **Assign**.
8. Verify that the line for **Software developer 1** has been removed for the **XYZ Upgrade project Phase 2** project.
9. On the **Project team and scheduling** tab, for the **XYZ Upgrade Phase 2** project, verify that the worker that you selected in the previous step has been added as **Software developer**.

## Requests for project resources
The functionality for project resource scheduling only lets resource managers distribute staffed resources on engagements or projects. To enable this functionality, complete the following tasks, or verify that they have been completed:

- Set up number sequences.
- Set up project management and accounting workflows.
- Enable resource request workflows.

After the preceding tasks have been completed, you can complete the following tasks as you require:

- Create a resource request from a soft-booked staffed resource.
- Monitor resource requests.
- Fulfill resource requests.
- Request a staffed resource from a WBS.
- Book resources to a project without having a request for a staffed resource.

## Monitor project teams
1. On the **All projects** page, select the **Project ID** link for the **XYZ Upgrade Phase 2** project.
2. On the **Project team and scheduling** FastTab, verify that the project resources that are listed are correct.
