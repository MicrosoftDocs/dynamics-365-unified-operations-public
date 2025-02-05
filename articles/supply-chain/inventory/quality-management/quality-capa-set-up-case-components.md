---
title: Set up CAPA case components
description: Before you can begin creating and working with CAPA cases, you must set up the components needed to categorize and process CAPA cases.
author: johanhoffmann
ms.author: johanho
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 04/25/2025
ms.custom: 
  - bap-template
---

# Set up CAPA case components

[!include [banner](../../includes/banner.md)]

Before you can begin creating and working with corrective and preventive action (CAPA) cases, you must set up the components needed to categorize and process CAPA cases.

## Set up CAPA worker groups

CAPA worker groups let you group users together for CAPA purposes. You can assign a CAPA work group to each activity and stage in your CAPA process. The system uses worker groups to validate worker assignments and each group can include a default worker to use when a specific worker isn't assigned. When a CAPA case, CAPA process stage, or CAPA process activity assigned to a worker or worker group becomes active, then the system sends that worker or worker group an email notification to let them know.

> [!TIP]
> To get started quickly, you can load a set of standard CAPA worker groups from a template provided with Supply Chain Management. You can use the standard groups as-is or modify them to meet your specific needs as described in the rest of this section. For instructions, go to [CAPA administration](quality-capa-admin.md).

To set up your CAPA worker groups, follow these steps.

1. Go to **Inventory management** \> **Setup** \> **CAPA management** \> **CAPA worker groups**.
1. Use the buttons on the Action Pane to add, remove, and edit worker groups as needed. (You can't delete worker groups that are assigned to CAPA case activities.)
1. For your new or selected worker group, make the following settings in the header:

    - **CAPA worker group** – Enter a name for the worker group. Common examples include *Investigator*, *Implementer*, *Approver* and*Verifier*.
    - **Name** – Enter a short description of the worker group.

1. Use the settings on the **Group settings** FastTab to set up the group, including details related to whether all members of the group can change the stage of a CAPA case and whether the CAPA administrator should be an implied member and/or default worker for the group. Make the following settings:
    - **Allow any member to change stage** – Select this check box if all workers within this CAPA worker group are allowed to change the stage of CAPA cases assigned to this group. Clear this checkbox if you if you want to limit which workers within the group can advance the stage of the CAPA Case.
    - **Implied member of this worker group** – Select this check box if the CAPA administrator, assigned on the Inventory management parameters, should be an implied member of this CAPA worker group. Alternatively, the CAPA administrator can be assigned to the CAPA worker group but if the CAPA administrator is changed, this will require more maintenance.
    - **Default worker** – Select this check box if the CAPA administrator should be the default worker for this CAPA worker group. <!-- KFM: This setting seemed to be ignored during the original bug bash with Traci. Does it work? -->

1. Use the **Worker assignments** FastTab to add and remove workers in the group.
    - Too add a worker, use the **New** button the **Overview** tab or go to the **Assign** tab and use the right arrow button move workers into the **Selected workers** list.
    - To remove a worker, use the **Delete** button on the **Overview** tab or go to the **Assign** tab and use the left arrow button move workers out of the **Selected workers** list.

1. On the **Overview** tab of the **Worker assignments** FastTab, set the following options for each worker in the group:
    - **Allowed** – If the the **Allow any member to change stage** checkbox is cleared on the **Group settings** FastTab, then select the **Allowed** checkbox for each worker that should be allowed to advance CAPA cases to the next stage. If the **Allow any member to change stage** checkbox is selected, then the **Allowed** checkbox on the **Worker assignments** FastTab is disabled.
    - **Default worker** – If the the **Default worker** checkbox is cleared on the **Group settings** FastTab, then select this check box for the worker that should be the default worker for this CAPA worker group. The default worker is used when creating a CAPA case and when advancing CAPA cases to the next stage. You can at most one default worker per CAPA worker group. If you set this option for a worker, then the **Default worker** option will automatically be turned off for all other workers (including for the admin in the **Group settings** FastTab). 

## Set up CAPA categories

CAPA categories allow you to group similar case types together. Organizing CAPA cases by category can help employees identify known solutions, such as knowledge articles, for when similar issues frequently occur. This information is also used by the *Trending analysis by category* feature so managers can review whether the frequency of specific issues is declining over time.

To set up your CAPA categories, follow these steps.

1. Go to **Inventory management** \> **Setup** \> **CAPA management** \> **CAPA categories**.
1. Use the buttons on the Action Pane to add and remove categories as needed. You can't delete categories that are assigned to active CAPA cases. For each category, make the following settings:
    - **CAPA category** – Enter the name of the CAPA category. The name must be unique.
    - **Description** – Enter a description of the CAPA category.
    - **CAPA subcategory type** – Select a subcategory for the CAPA category. It includes several predefined subcategories (*None*, *Customer*, *Vendor*, and *Product*). It also includes the *User defined* subcategory type, which lets users choose from a collection of custom subcategories when they create a CAPA case using this type of category. The next procedure describes how to set up your custom subcategories.

To set up CAPA subcategories for a categories with a *User defined* subcategory type, follow these steps.

1. Go to **Inventory management** \> **Setup** \> **CAPA management** \> **CAPA categories**.
1. Select the category you want to define subcategories for. It must have **CAPA subcategory type** set to *User defined*.
1. On the Action Pane, select **User defined CAPA subcategory**.
1. Use the buttons on the Action Pane to add and remove subcategories as needed. For each subcategory, make the following settings:
    - **CAPA subcategory** – Enter the name of the subcategory.
    - **Description** – Enter a short description of the subcategory.

## Set up CAPA resolutions

CAPA resolutions let users select a resolution reason when they resolve a CAPA case. You can use CAPA resolutions to identify and categorize typical reasons CAPA cases can be resolved. <!-- KFM: More to say? Examples? -->

To set up your CAPA resolutions, go to **Inventory management** \> **Setup** \> **CAPA management** \> **CAPA resolutions**. Then use the buttons in the Action Pane to create and delete resolutions as needed. For each resolution, enter a name and description.

## Set up CAPA source codes

CAPA source codes let users select a source for each CAPA case. You can use source codes to track the source of each case, such as *Internal audit*, *External audit*, *Ad-hoc testing*, and so on.

To set up your CAPA source codes, go to **Inventory management** \> **Setup** \> **CAPA management** \> **CAPA source codes**. Then use the buttons in the Action Pane to create and delete source codes as needed. For each source code, enter a name and description.

## Set up CAPA types

CAPA types let users select a type to categorize each CAPA case.  <!-- KFM: Introduce these. What are they for? Examples? -->

To set up your CAPA types, go to **Inventory management** \> **Setup** \> **CAPA management** \> **CAPA types**. Then use the buttons in the Action Pane to create and delete CAPA types as needed. For each CAPA type, enter a name and description.

## Set up Major/minor classification codes

CAPA types let users select a major/minor classification code for each CAPA case.  <!-- KFM: Introduce these. What are they for? Examples? -->

To set up your major/minor classification codes, go to **Inventory management** \> **Setup** \> **CAPA management** \> **Major/minor classification codes**. Then use the buttons in the Action Pane to create and delete classification codes as needed. For each code, enter a name and description.

## Set up CAPA root causes

CAPA root cause codes let users select the root cause of an issue when they resolve a CAPA case. <!-- KFM: More to say? Examples? -->

To set up your CAPA root cause codes, go to **Inventory management** \> **Setup** \> **CAPA management** \> **CAPA root causes**. Then use the buttons in the Action Pane to create and delete root causes as needed. For each root cause, enter a name and description.

## Set up CAPA processes

CAPA processes are hierarchical processes that let you manage and resolve CAPA cases. Each CAPA process comprises a series of sequential stages, each of which can include one or more automatically generated activities. When you create a CAPA case, you'll assign the CAPA process required to guide it to completion.

> [!TIP]
> To get started quickly, you can load a set of standard CAPA processes from a template provided with Supply Chain Management. You can use the standard processes as-is or modify them to meet your specific needs as described in the rest of this section. For instructions, go to [CAPA administration](quality-capa-admin.md).

### Manage and approve CAPA processes

To name, describe, and approve your CAPA processes, follow these steps.

1. Go to **Inventory management** \> **Setup** \> **CAPA management** \> **CAPA processes**.
1. The **CAPA processes** page opens, showing a list of existing CAPA processes. The following information is shown for the selected process:
    - **Name** – The name of the selected CAPA process. This is read-only for existing processes.
    - **Description** – A short description of the selected CAPA process.
    - **Approved** – Indicates whether the selected CAPA process is approved for use in managing CAPA cases. <!-- KFM: mention what role is needed to be able to change this. --> Only approved CAPA processes are available to users when they create and process a CAPA case. You can keep this set to *No* while developing a new process, and then change it to *Yes* when you're ready to start using it.

1. Use buttons on the Action Pane to add and remove processes.
    - To add a new process, select **New**.
    - To delete a selected process, select **Delete**.
    - To edit the name, description or approval status of a selected process, select **Edit**.

### Configure CAPA process details

To define the stages and activities that make up a CAPA process, follow these steps.

1. Go to **Inventory management** \> **Setup** \> **CAPA management** \> **CAPA processes**.
1. Select or create the CAPA process you want to work with.
1. On the Action Pane, open the **Process** tab and select **Details**.

    You now see a page where you can create or edit the structure of your selected process. The page has two panes. The left pane shows a hierarchical list of stages and activities that make up the process. The top level is the process itself. The second level are the stages, and each stage can include one or more activities nested below it. You can create sub-stages as deeper levels if you want to, but usually, you'll just have one level of stages. The right pane shows details about the selected stage or activity. Workers must complete the stages in order, from top to bottom, but all activities belonging to a stage can be done in order order or even simultaneously. Some activities can be set to mandatory, meaning they must be completed before the process can continue to the next stage.

    If you're creating a new process that should be similar to an existing process, then you can get started quickly by copying that process. To do so, open the **Process** tab on the Action Pane and select **Copy from**. Then select the process you want to copy.

1. Set up your top-level stages. To add a new stage at the bottom of the current stages list, select the top level heading (the process name) and on the Action Pane, select **New** \> **Create level**. (You can create a sub-stage for an existing stage by selecting the parent stage and selecting **New** \> **Create level**.) For each stage, enter the following information in the right pane:
    - **Name** – This is a read-only field. For a new stage, it takes it's value from the the text you enter in the **Purpose** field and can't be changed later.
    - **Activity number** – This is a read-only field. It's automatically generated. <!-- KFM: What is the link for? It seems like it's only relevant for active cases, so why is it active here? -->
    - **CAPA worker group** – Select or view the CAPA worker group that identifies the group of CAPA workers responsible for this activity. By default, this group is also assigned to the activities belonging to the stage, but you can override it for each stage if necessary.
    - **Responsible** – Select worker from the selected worker group who is responsible for this activity. If none is specified, the default worker assigned for the selected worker group is used. when the CAPA case is being processed.
    - **Notify group** – Choose who should be notified by email when the stage becomes active. Select *Yes* to notify the entire worker group. Select *No* to just notify the responsible worker. Select *Inherit* to inherit this setting from a parent stage in the hierarchy.
    - **Email status updates** – Choose whether to also send email to the responsible worker or group the stage is closed or reopened. Choose *Yes*, *No*, or *Inherit*.
    - **Print on report** – Choose wether to include information about this stage in the printed CAPA case report. Choose *Yes*, *No*, or *Inherit*.
    - **Check for required activities** – Select this check box to specify whether activities belonging to this stage and marked as mandatory must be completed before the stage can be closed.

1. Add activities to each stage. To add an activity at the bottom of the current list of activities for a stage, select the stage and on the Action Pane, select **New** \> **Create action**, **New** \> **Create appointment**, **New** \> **Create event**, or **New** \> **Create task**, depending on which type of activity it should be. The activity types all work in approximately the same way, though each has slightly different scheduling settings available for it. For each activity, enter the following information in the right pane:
    - The **Name**, **Purpose**, and **Activity number** fields all work the same way as they do for stages.
    - Use the **Required** field to mark an activity as mandatory. Mandatory activities must be completed before the parent stage can be closed, provided that the **Check for required activities** setting is set to *Yes* for the parent stage.
    - Use the scheduling fields (like **Start time** and **End time**) to set the start and end dates and times for the activity. These fields are used to calculate when the activity should be performed based on the start and end dates of the CAPA case. Scheduling field availability varies by activity type.
    - Set notification options as needed. These settings all work the same way as they do for stages and are set to inherit their settings from the parent stage by default.

1. Continue working until you've set up all the elements you need for your process. Then, on the Action Pane, select **Save**.

### View all cases that use a selected CAPA process

To see all CAPA cases that use a selected CAPA process, follow these steps.

1. Go to **Inventory management** \> **Setup** \> **CAPA management** \> **CAPA processes**.
1. Select or open the CAPA process you want to look for.
1. On the Action Pane, open the **Process** tab and select **All cases** or **All CAPA cases**. <!-- KFM: what is the difference? -->
