---
# required metadata

title: Project resourcing
description: This topic provides information about project resourcing.
author: rschloma
manager: AnnBe
ms.date: 2016-04-13 17 - 38 - 35
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: annbe
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 82022
ms.assetid: 8fd15e0a-c6fd-4c23-bc54-04ab4792aecf
ms.search.region: Global
# ms.search.industry: 
ms.author: cmercado
ms.dyn365.intro: Feb-16
ms.dyn365.version: AX 7.0.0

---

# Project resourcing

This topic provides information about project resourcing.

One challenge for project managers and resource managers during the project planning stage is resource allocation, where they must determine and reserve the correct resource to work on a project. In Microsoft Dynamics 365 for Operations, resourcing capabilities for projects let you define roles that are treated as temporary resources that can be reserved for a specific engagement, or part of an engagement. This type of resourcing lets project managers and resource managers complete the following tasks:

-   Define a role that has the required competencies to make it easy to match resources.
-   Use roles to define an initial engagement schedule that is based on reserved resources.
-   Estimate costs and determine an initial budget, based on assigned roles and resources for a project.
-   Use roles to estimate the number of resource reservations that are required for each engagement.
-   Estimate the number of resources that are required for the entire life cycle of a project.
-   Draft a work breakdown structure (WBS) by using the initial resource assignments.

[![Project life cycle](./media/projectresourcing02-1024x812.jpg)](./media/projectresourcing02.jpg) As project planning proceeds, planned resources can be replaced with staffed resources. The project manager can also go back and update the resourcing reservations during any of the project stages.

## Set up project resources
You must set up a calendar and associate it with an employee or a worker. The calendar is used to schedule the project and the working time of the resources that are reserved for the project. During calendar setup, project managers can perform resource leveling as part of resource optimization. Based on the calendar schedule, restrictions can be placed on resources. You can set up a calendar on the **Calendars** page (**Organization administration** &gt; **Setup** &gt; **Calendars** &gt; **Calendars**).

### Set up a worker as a project resource

1.  Click **Human resources** &gt; **Workers** &gt; **Workers**.
2.  In the **Workers** list, select the worker that you're adding as a project resource, and open the worker record.
3.  On the Action Pane, click **Project** &gt; **Setup** &gt; **Project setup**.
4.  Select a** **calendar, and then close the page.

You can also specify default projects for a resource as a type of pre-assignment. Pre-assignments can be used when the resource manager or project manager knows which projects the resource will be working on in advance. Pre-assignments can also be based on the request of a project sponsor or customer. To pre-assign a project, on the **Assign projects** page, on the **Projects** tab, in the **Remaining projects** list, select the appropriate project.

## Manage resource competencies
Resource competencies are an essential part of resource management. Competencies can be used as a baseline to determine resources that have the correct balance of skills, education, certification, and project experience. You should set up this information for each resource and update it on a regular basis. In this way, you can maximize capabilities when specific resource competencies are matched during project resource assignment. [![Examples of skills, certifications, education, and project experience](./media/projectresourcing06-1024x383.jpg)](./media/projectresourcing06.jpg) The following procedures explain how to set up some of the competencies for a resource. To set up competencies for a worker, you can use either the **Workers** list page in Human resources or the **Resources** list page in Project management and accounting. For the following procedures, the **Workers** list page in Human resources is used.

### Set up competencies: Certificates

1.  On the **Workers** list page, select the line of the worker that you're adding certificate information for.
2.  On the Action Pane, on the **Worker** tab, in the **Competencies** group, click **Certificates**.
3.  Click **New**.
4.  In the **Certificate type** field, select **PMP**.
5.  In the **Start date** field, select **10/1/2015**.
6.  Click **Save**, and then close the page.

### Set up competencies: Skills

1.  On the **Workers** list page, make sure that the worker that you used in the previous procedure is still selected. Then, on the Action Pane, on the **Worker** tab, in the **Competencies** group, click **Skills**.
2.  Click **New**.
3.  In the **Skill** field, select **Project management**.
4.  In the **Level** field, select **5 Expert**.
5.  In the **Level date** field, select **1-/14/2014**.
6.  In the **Years of experience** field, enter **10**.
7.  Click **Save**, and then close the page.

## Create a new project
1.  Click **Project management and accounting** &gt; **Workspaces** &gt; **Project management**.
2.  Click **New project**, and enter the following values:
    -   **Project type** - Time and material
    -   **Project name** - XYZ Upgrade Phase 2
    -   **Project group** - TM\_WIP
    -   **Project contract ID**  - 00000002

3.  Click **Create project**.

### Assign a resource to a project

1.  Click **Human resources** &gt; **Workers** &gt; **Workers**.
2.  In the **Workers** list, select the record for the worker that you previously set up competencies for, and open the worker record.
3.  On the Action Pane, on the **Project** tab, in the **Setup** group, click **Assign projects**.
4.  On the **Resource validation project assignments** page, click the **Projects** tab.
5.  In the **Add the project to selected projects**, filter on the project, XYZ Upgrade Phase 2
6.  In the **Remaining projects** pane, select a project, and then click the arrow to add it to the **Selected projects** pane.
7.  Close the page.

If needed, you can also assign categories for a resource. The category type is either Cost or Revenue. This is determined by your organization. If there are no assigned categories for the resource, Dynamics 365 for Operations will look up the default category on hour prices for cost and revenue.

### Set up project resource and role characteristics

A project manager can use the project resourcing functionality to create the roles that are required for the project. Roles can be used when confirmed resources are still unknown when reserving resources. Roles can be temporarily reserved as planned resources, so that you can continue the project planning stages. [![Example of a role](./media/projectresourcing05.jpg)](./media/projectresourcing05.jpg) **Scenario:** Contoso was hired to complete a Time and material project that has an approved project charter. The junior project manager is still completing the scope of the project. The resource manager is currently identifying specific resources that will be reserved to work on the new project. One of the roles that the project sponsor requested, because of the critical nature of the project, is the Senior project manager. The resource manager must acquire the new resource and define the role in the system in case the junior project manager requires the resource information during the project planning. The following steps show how the resource manager can set up the Senior project manager role and associate resource characteristics with it. Later, the role can be used to search for available resources that match the required resource competencies.

1.  Click **Project management and accounting** &gt; **Setup** &gt; **Resources** &gt; **Setup roles**.
2.  Click **New**, and enter the following values:
    -   **Role ID** - Senior Project Manager
    -   **Description** - Senior Project Manager

3.  Click **Create**.
4.  Select the **Senior Project Manager** role, and then click **Configure characteristics**.
5.  In the **Characteristics type** field, select **Skill**.
6.  In the **Available characteristics** field, enter the skill that you're searching for.
7.  In the **Characteristic type** field, select **Certificate**.
8.  In the **Available characteristics** field, enter the certificate type to search for.
9.  Click **OK**, and close the page.

### Assign a project resource to a project

1.  Click **Project management and accounting** &gt; **Common** &gt; **Projects** &gt; **All projects**, and open the **XYZ Upgrade Phase 2** project.
2.  On the **Project team and scheduling** tab, click **Add**.
3.  In the **Role** field, select **Team member**.
4.  Click **Book from calendar**.
5.  On the **Resource availability** page, click **View settings**.
6.  On the **Adjust view settings** page, enter the following values:
    -   **Format for date range view** - Day
    -   **Display availability descriptions** - Yes
    -   **Display remaining capacity** - Yes

7.  In the list of resources, select a resource.
8.  Click **Hard book** &gt; **Full capacity**.
9.  Close the page.

### Assign a resource to a default role

To help project or resource managers, you can drill down further on the resources that can be reserved for a project. You can associate a default role with an existing resource or a newly acquired resource. For example, when Daniel was hired, he had the experience and skills to fill the Business analyst role. The resource manager assigned this role as Daniel's default role. Therefore, the resource manager added Daniel to a pool of business analysts who are available to work on projects. During resource reservation, project managers can filter the role resources that are available to work on projects. They can use this information as one criterion when they perform multi-criteria decision analysis during resource fulfillment. They can also add other resource characteristics to the filter to search for resources that have specific skills, education, and experience for a given project. **Scenario:** An approved project has started, and the Senior project manager role was reserved as a planned resource during the project planning stage. The resource manager has now acquired a resource to fulfill the Senior project manager role.

1.  Click **Project management and accounting** &gt; **Project resources** &gt; **Resources list**.
2.  In the **Resource** list, select **Daniel Goldschmidt**.
3.  Click **Project resource** &gt; **Maintain** &gt; **Resource role**.
4.  Click **New**, and enter the following values:
    -   **Effective** -** **(The current date)
    -   **Expiration** - Never
    -   **Role** - Senior Project Manager

5.  Click **Save**, and then close the page.
6.  On the **Competencies** tab, add the **ProjectMgmt** skill and the **PMP** certificate.

## Set up rolebased pricing
All cost, sales, and transfer prices can be set up for roles.

1.  Click **Project management and accounting** &gt; **Setup** &gt; **Prices** &gt; **Sales price (hour)**.
2.  Click **New**.
3.  Enter an effective date.
4.  In the **Role** column, select a role.
5.  In the **Pricing** column, enter a price for the selected resource role.

## Form a project team
To use the roles that were previously set up in a project, a project manager must associate the roles with the project. Multiple roles can be assigned for a project, and Dynamics 365 for Operations automatically labels these roles during reservation to prevent confusion. For example, if the project manager requires three software engineers, three Software engineer roles that have software engineer 1, software engineer 2, and software engineer 3 as their labels are automatically generated. If role characteristics were previously set for the role, they are applied as a filter during searches for a resource. Additional characteristics can be added as required to further refine the search. View settings can also be customized to give a better view of resource availability. There are options to show hourly, daily, weekly, monthly, quarterly, and annual availability. There is also an option to show available and remaining capacity on resources. This option is useful for time management when you're estimating available time for activities or resource availability. The project manager can select a role on the page and then, if there is an available resource that fits the requirement, select to reserve a resource to fill the role. Note that the resources don't have to be reserved at this point during the planning stage. When you create a WBS, you can replace roles with staffed resources for the project. If roles are replaced with staffed resources in the WBS, the resource setup automatically updates the project team listing and scheduling. [![Project team listing that includes both roles and actual resources](./media/projectresourcing03-1024x368.jpg)](./media/projectresourcing03.jpg) The project manager has various options for booking a resource for a project, such as **Remaining capacity**, **Full capacity**, **Capacity percentage**, and **Specify hours**. These booking options can be canceled at any time if resource assignments change. Two types of booking are supported:

-   **Hard Book** – The resource reservation was approved and confirmed to work on the engagement for the specified duration.
-   **Soft book** – The resource reservations was tentatively set to work on the engagement for the specified duration.

The following procedure explains how to create a project team.

### Create a project team

1.  On the **All projects** list page, select a project, and then click **Edit**.
2.  On the **Project team and scheduling** tab, in the **Schedule end date** field, enter the schedule start date plus one month. For example, if the schedule start date is June 24, 2017 (24/06/2017), enter **24/07/2017**.
3.  Click **Add**.
4.  In the **Add roles to the project** pane, in the **Role** field, select **Senior Project Manager**.
5.  Click **Required competencies**.
6.  On the **Choose characteristics** page, the characteristics that you previously set for the Senior project manager role are selected by default. Click **OK**.
7.  On the **Add roles to project** page, in the **Number of resources** field, enter **1**.
8.  In the **Resource** field, the lookup shows all resources that have the required competencies. Select **Daniel Goldschmidt**, and then click **Create**.
9.  On the **Project** page, click **Add**.
10. In the **Add roles to the project** pane, in the **Role** field, select **Team member**. In the **Number of resources** field, enter **5**.
11. Click **Create**.
12. On the **Projects** page, click **Fulfill resource**.

## Resource capacity synchronization
The processes for resource synchronization helps guarantee that the calendar and base calendar information trickles down into project resource scheduling. If the calendar is changed, the processes make the required updates to the scheduling of project resources. The processes also help improve performance, because the calendar’s resource information is synchronized in advance, so that updates to resource scheduling information occur more quickly. We recommend that you schedule the processes as a batch instead of one at a time. Otherwise, there is a risk that someone will forget the inclusive dates when the information was last synchronized. If inclusive dates aren't used, gaps can occur during date synchronization.

### ![Calendar synchronization](./media/projectresourcing04-1024x471.jpg)Synchronize resource capacity roll-ups

The synchronization process is designed to synchronize all resource calendar information. This information includes base calendar information about any changes to the project’s Resource calendar capacity table. If new resources are added in the project, synchronization helps ensure that the updated calendar information is available. This synchronization can be done at any time. We recommend that you use a batch. The options are available in synchronizing capacity reservations.

-   Click **Project management and accounting** &gt; **Periodic** &gt; **Capacity synchronization** &gt; **Synchronize resources capacity roll-ups**.

| Option | Description                                                                                                                                                                                          |
|--------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Yes    | Synchronize all resource data with calendar and base calendar information, and replace all information in the project's resource capacity calendar.                                                  |
| No     | Synchronize resource data, based on the date interval code, and the specified start and end dates. This option doesn't remove existing data, and updates information only for newly added resources. |

[![Synchronization process](./media/projectresourcing09.jpg)](./media/projectresourcing09.jpg)

## Set up roles on WBS templates
Project managers can set up WBS templates that they can apply when they create a WBS for new projects. Project managers can add roles when they create a template. Use the following procedure to assign a role to a WBS template.** **

1.  Click **Project management and accounting** &gt; **Setup** &gt; **Projects** &gt; **Work breakdown structure templates**.
2.  Click **Details** for a selected WBS template.
3.  Select a task in the list, and then, in the **Role** field, select a role to assign to the task.

### Work with a WBS

You can create a new WBS, or you can copy a WBS from an existing WBS template. A project manager can easily manage the resources by assigning roles to new tasks on the WBS. Roles can be replaced after a resource is acquired, or after a confirmed resource to work on the task is identified. This flexibility lets project managers perform the following tasks:

-   Identify the number of resources that are required for WBS work packages.
-   Estimate project costs.
-   Determine a preliminary budget.
-   Estimate activity duration, based on roles and resources.
-   Develop some project management plans, based on the available project information.

Additional options have been added in the WBS to better use the resourcing functionality.

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
<td>Automatically add planned resources by using roles that are associated with a task. Dynamics 365 for Operations automatically suggests planned resources by using multi-criteria decision analysis that is based on roles. After the roles and effort (hours) have been set for the tasks in a WBS, and the structure has been released, click <strong>Auto generate team</strong>. The required number of planned resources is added to the WBS and the <strong>Project and team scheduling</strong> tab.</td>
</tr>
<tr class="odd">
<td>Resource (drop-down list)</td>
<td>On the <strong>Launch resource assignment </strong>page, you can select resources to hard-book or soft-book, based on the specified duration. You can adjust the view settings to see and set the duration of resource activities. You can select and assign resources at the work package level by using the following options:
<ul>
<li><strong>Accept</strong> – Confirm changes to the resource that is assigned to a task.</li>
<li><strong>Cancel</strong> – Cancel changes to the resource that is assigned to a task.</li>
<li><strong>Assign automatically</strong> – This option selects an available staffed resource with a matching role to the selected task.</li>
</ul></td>
</tr>
</tbody>
</table>

1.  Click **Project management and accounting** &gt; **Projects** &gt; **All projects**.
2.  In the list, select the **XYZ Upgrade Phase 2** project.
3.  Click **Plan** &gt; **Activities** &gt; **Work breakdown structure**.
4.  Click **New** to add the following level-one activities to the WBS:
    -   Initiating
    -   Planning
    -   Executing
    -   Monitoring and Control
    -   Close

5.  Set the dates and effort (hours), as shown in the following screenshot.[![Setting the dates and effort](./media/projectresourcing10.jpg)](./media/projectresourcing10.jpg)
6.  Select the **Initiating** task line, and then, in the **Role** field, select **Senior Project Manager**.
7.  Click **Publish**.
8.  On the same line, in the **Resource** field, select **Daniel Goldschmidt**.
9.  Click **Accept**.
10. Select the **Planning** task line, and then, in the **Role** field, select **Business analyst**.
11. Click **Publish**, and then click **Auto generate team**.
12. In the dialog box that appears, click **Yes**.
13. In the **Resource** field, verify that the value is **Business analyst 1**.
14. For the **Business analyst 1** resource, open the lookup, and click **Launch resource assignments form**.
15. Select a worker for the task.
16. Click **Soft assign** &gt; **Full capacity**.
17. Click **Save**, and close the page. **Note:** You don't receive a warning that the specified resource is now 2, because the number of resources remains at 1.
18. On the **Work breakdown structure** page, validate the resource assignment on the WBS, and then click **Save**.

## Resource fulfillment for planned resources
A project manager can plan required resource roles for a project. The resource manager will see these planned resources as requests on the **Resource fulfillment** page and can assign actual resources.

1.  Click **Project management and accounting** &gt; **Projects** &gt; **All projects**.
2.  In the list, select the **XYZ Upgrade Phase 2** project.
3.  Click **Project**.
4.  Click **Edit**.
5.  On the **Project team and scheduling** tab,** **click **Add**.
6.  In the **Add roles** dialog box, select the **Software developer** role.
7.  Click **Create**.
8.  Close the project page.
9.  Click **Project management and accounting** &gt; **Project resources** &gt; **Resource fulfillment**.
10. Select **Software developer 1** for the **XYZ Upgrade project Phase 2** project.
11. Select a worker, and then click **Assign**.
12. Verify that the line for **Software developer 1** has been removed for the **XYZ Upgrade project Phase 2** project.
13. On the **Project team and scheduling** tab, for the **XYZ Upgrade Phase 2** project, verify that the worker that you selected in step 11 has been added as **Software developer**.

## Requests for project resources
The project resource scheduling functionality only supports resource managers to distribute staffed resources on engagements or projects. To enable this functionality, complete the following tasks, or verify that they have been completed.

-   Set up number sequences.
-   Set up project management and accounting workflows.
-   Enable resource request workflow.

After you have either verified or completed the tasks above, you can complete the following tasks as needed.

-   Create a resource request from a soft-booked staffed resource.
-   Monitor resource requests.
-   Fulfill resource requests.
-   Request a staffed resource from WBS.
-   Book resources to a project without a request for a staffed resource.

## Monitor project teams
1.  Click **Project management and accounting** &gt; **Projects** &gt; **All projects**.
2.  In the list of projects, click the **Project ID** link for the **XYZ Upgrade Phase 2** project.
3.  On the **Project team and scheduling** FastTab, verify that the project resources that are listed are correct.


