---
title: Set up CAPA case components
description: Learn how to set up the components needed to categorize and process corrective and preventive action (CAPA) cases.
author: johanhoffmann
ms.author: johanho
ms.reviewer: kamaybac
ms.search.form: QMSCAPAWorkerGroup, QMSCAPACategory, Hierarchy, HierarchyDetail, QMSCAPASourceCode, QMSCAPAResolution, QMSCAPAType, QMSCAPAClassificationCode, QMSCAPARootCause
ms.topic: how-to
ms.date: 04/25/2025
ms.custom: 
  - bap-template
---

# Set up CAPA case components

[!include [banner](../../includes/banner.md)]

Before you can start to create and work with corrective and preventive action (CAPA) cases, you must set up the components that are needed to categorize and process them.

## Set up CAPA worker groups

*CAPA worker groups* let you group users together for CAPA purposes. You can assign a CAPA worker group to each activity and stage in your CAPA process. The system uses worker groups to validate worker assignments. 

Each CAPA worker group can include a default worker. This worker is used if no specific worker is assigned.

When a CAPA case, CAPA process stage, or CAPA process activity that is assigned to a worker or worker group becomes active, the system sends the worker or worker group an email notification.

> [!TIP]
> To get started quickly, you can load a set of standard CAPA worker groups from a template that is provided with Microsoft Dynamics 365 Supply Chain Management. You can use the standard groups as-is or modify them to meet your specific needs, as described in the rest of this section. Learn more in [CAPA administration (preview)](capa-admin.md).

To set up CAPA worker groups, follow these steps.

1. Go to **Inventory management** \> **Setup** \> **CAPA management** \> **CAPA worker groups**.
1. Use the buttons on the Action Pane to add new worker groups or edit existing ones as required. (You can also delete existing groups, but only if they aren't assigned to CAPA case activities.)
1. On the header of the new or selected worker group, set the following fields:

    - **CAPA worker group** – Enter a name for the worker group. Typical examples include *Investigator*, *Implementer*, *Approver*, and *Verifier*.
    - **Name** – Enter a short description of the worker group.

1. On the **Group settings** FastTab, set the following fields to set up details of the group. These details include whether all members of the group can change the stage of a CAPA case, and whether the CAPA administrator should be an implied member and/or default worker for the group.

    - **Allow any member to change stage** – Select this checkbox if all workers in the CAPA worker group are allowed to change the stage of CAPA cases that are assigned to the group. Clear this checkbox if you want to limit which workers in the group can move CAPA cases to the next stage.
    - **Implied member of this worker group** – Select this checkbox if the CAPA administrator who is assigned on the **Inventory management** parameters page should be an implied member of the CAPA worker group. Alternatively, the CAPA administrator can be assigned directly to the CAPA worker group. However, if the CAPA administrator is changed, extra maintenance is required.
    - **Default worker** – Select this checkbox if the CAPA administrator should be the default worker for this CAPA worker group.

1. On the **Worker assignments** FastTab, add or remove workers in the group.

    - To add a worker, use the **New** button on the **Overview** tab. Alternatively, on the **Assign** tab, use the right arrow button to move workers into the **Selected workers** list.
    - To remove a worker, use the **Delete** button on the **Overview** tab. Alternatively, on the **Assign** tab, use the left arrow button to move workers out of the **Selected workers** list.

1. On the **Overview** tab of the **Worker assignments** FastTab, set the following fields for each worker in the group:

    - **Allowed** – If the **Allow any member to change stage** checkbox is cleared on the **Group settings** FastTab, select this checkbox for each worker that should be allowed to move CAPA cases to the next stage. If the **Allow any member to change stage** checkbox is selected, this checkbox is unavailable.
    - **Default worker** – If the **Default worker** checkbox is cleared on the **Group settings** FastTab, select this checkbox for the worker who should be the default worker for the CAPA worker group. The default worker is used when CAPA cases are created and moved to the next stage. Each CAPA worker group can have a maximum of one default worker. Therefore, if you select this checkbox for a worker, it's automatically cleared for all other workers, including the administrator who is assigned on the **Group settings** FastTab.

## Set up CAPA categories

*CAPA categories* let you group similar case types together. By organizing CAPA cases into categories, you help employees identify known solutions, such as knowledge articles, when similar issues frequently occur. This information is also used by the *Trending analysis by category* feature. Therefore, managers can review whether the frequency of specific issues is declining over time.

To set up CAPA categories, follow these steps.

1. Go to **Inventory management** \> **Setup** \> **CAPA management** \> **CAPA categories**.
1. Use the buttons on the Action Pane to add new CAPA categories as required. (You can also delete existing categories, but only if they aren't assigned to active CAPA cases.)
1. For each new CAPA category, set the following fields:

    - **CAPA category** – Enter the name of the CAPA category. The name must be unique.
    - **Description** – Enter a description of the CAPA category.
    - **CAPA subcategory type** – Select a subcategory for the CAPA category. The list includes several predefined subcategories (*None*, *Customer*, *Vendor*, and *Product*). It also includes the *User defined* subcategory type. If you select this subcategory type, users can select from a set of custom subcategories when they create a CAPA case that uses this CAPA category. The next procedure explains how to set up custom CAPA subcategories.

To set up custom CAPA subcategories for a category that uses the *User defined* subcategory type, follow these steps.

1. Go to **Inventory management** \> **Setup** \> **CAPA management** \> **CAPA categories**.
1. Select the category that you want to define subcategories for. The selected category must have the **CAPA subcategory type** field set to *User defined*.
1. On the Action Pane, select **User defined CAPA subcategory**.
1. Use the buttons on the Action Pane to add new subcategories as required. (You can also delete existing subcategories.) 
1. For each subcategory, set the following fields:

    - **CAPA subcategory** – Enter the name of the subcategory.
    - **Description** – Enter a short description of the subcategory.

## Set up CAPA processes

*CAPA processes* are hierarchical processes that let you manage and resolve CAPA cases. Each CAPA process consists of a series of sequential stages. Each stage can include one or more automatically generated activities. When you create a CAPA case, you assign the CAPA process that is required to guide it to completion.

> [!TIP]
> To get started quickly, you can load a set of standard CAPA processes from a template that is provided with Supply Chain Management. You can use the standard processes as-is or modify them to meet your specific needs, as described in the rest of this section. Learn more in [CAPA administration (preview)](capa-admin.md).

### Manage and approve CAPA processes

To name, describe, and approve CAPA processes, follow these steps.

1. Go to **Inventory management** \> **Setup** \> **CAPA management** \> **CAPA processes**.

    The **CAPA processes** page shows a list of existing CAPA processes. For each selected process, the following information is shown:

    - **Name** – The name of the CAPA process. For existing processes, this field is read-only.
    - **Description** – A short description of the CAPA process.
    - **Approved** – A value that indicates whether the CAPA process is approved for use in CAPA case management. Only approved CAPA processes are available to users when they create and process a CAPA case. You can leave this option set to *No* while you develop a new process, and then set it to *Yes* when you're ready to start to use it.

1. Use the buttons on the Action Pane to add new CAPA processes or edit existing ones. (You can also delete existing processes.)

    - To add a new process, select **New**.
    - To edit the name, description, or approval status of a selected process, select **Edit**.
    - To delete a selected process, select **Delete**.

### Configure CAPA process details

To define the stages and activities that make up a CAPA process, follow these steps.

1. Go to **Inventory management** \> **Setup** \> **CAPA management** \> **CAPA processes**.
1. Select or create the CAPA process that you want to work with.
1. On the Action Pane, on the **Process** tab, select **Details**.

    You can use the page that appears to create or edit the structure of the new or selected process. The page has two panes.

    - The left pane shows a hierarchical list of stages and activities that make up the process. The top level is for the process itself. The second level is for the stages. One or more activities can then be nested below each stage. Usually, one level of stages is enough. However, you can create deeper levels for substages as you require. 
    - The right pane shows details about the selected stage or activity. Workers must complete the stages in order, from top to bottom. However, the activities that belong to a stage can be done in any order or simultaneously. Activities can be set as mandatory. In this case, they must be completed before the process can move to the next stage.

    > [!TIP]
    > If you want to create a new process that is similar to an existing process, you can get started quickly by copying the existing process. On the Action Pane, on the **Process** tab, select **Copy from**. Then select the process that you want to copy.

1. Set up the top-level stages. To add a new stage at the bottom of the current stage list, select the top-level heading (the process name), and then, on the Action Pane, select **New** \> **Create level**. (To create a substage for an existing stage, select the parent stage, and then select **New** \> **Create level**.) 
1. For each new stage, review or enter the following information in the right pane:

    - **Name** – This field is read-only. For a new stage, its value comes from the value that you enter in the **Purpose** field. It can't be changed later.
    - **Activity number** – This field is read-only. The value is automatically generated.
    - **CAPA worker group** – Select or view the CAPA worker group that represents the group of CAPA workers who are responsible for the activity. By default, this group is also assigned to the activities that belong to the stage. However, you can override the group for each stage as required.
    - **Responsible** – Select the worker from the selected CAPA worker group who is responsible for the activity. If you don't select a worker, the designated default worker for the worker group is used when a CAPA case is processed.
    - **Notify group** – Specify who should be notified by email when this stage becomes active. Select *Yes* to notify the whole worker group. Select *No* to notify only the responsible worker. Select *Inherit* to inherit the setting from the parent stage in the hierarchy.
    - **Email status updates** – Specify whether email should be sent to the responsible worker or worker group when this stage is closed or reopened. The available values are *Yes*, *No*, and *Inherit*.
    - **Print on report** – Select whether information about this stage should be included on the printed CAPA case report. The available values are *Yes*, *No*, and *Inherit*.
    - **Check for required activities** – Select this checkbox if activities that belong to this stage and that are marked as mandatory must be completed before the stage can be closed.

1. Add activities to each stage. To add a new activity at the bottom of the current activity list for a stage, select the stage, and then, on the Action Pane, select **New** \> **Create action**, **New** \> **Create appointment**, **New** \> **Create event**, or **New** \> **Create task**, depending on the type of activity that you want. All the activity types work in nearly the same way, but slightly different scheduling settings are available for each. 
1. For each new activity, enter the following information in the right pane:

    - The **Name**, **Purpose**, and **Activity number** fields work the same way that they work for stages.
    - Use the **Required** field to mark an activity as mandatory. If the **Check for required activities** field is set to *Yes* for the parent stage, mandatory activities must be completed before the parent stage can be closed.
    - Use the scheduling fields (such as **Start time** and **End time**) to set the start and end dates and times for the activity. These fields are used to calculate when the activity should be performed relative to the day when the activity is created. The availability of scheduling fields varies by activity type.
    - Set the notification options as required. All these settings work the same way that they work for stages. By default, they are set to inherit their setting from the parent stage.

1. Continue to work until you finish setting up all the elements that you need for your process. Then, on the Action Pane, select **Save**.

### View all cases that use a selected CAPA process

To view all CAPA cases that use a selected CAPA process, follow these steps.

1. Go to **Inventory management** \> **Setup** \> **CAPA management** \> **CAPA processes**.
1. Select or open the CAPA process that you want to view cases for.
1. On the Action Pane, on the **Process** tab, select **All cases** or **All CAPA cases**.

## Set up CAPA resolution types

*CAPA resolution types* let users select a resolution reason when they resolve a CAPA case. You can use CAPA resolution types to identify and categorize typical reasons why CAPA cases can be resolved.

To set up CAPA resolution types, follow these steps.

1. Go to **Inventory management** \> **Setup** \> **CAPA management** \> **CAPA resolution types**.
1. Use the buttons on the Action Pane to create new CAPA resolution types as required. (You can also delete existing resolution types.)
1. For each new CAPA resolution type, enter a name and a description.

## Set up CAPA sources

*CAPA sources* let users select a source for each CAPA case. You can use CAPA sources to track the source of each case, such as *Internal audit*, *External audit*, or *Ad-hoc testing*.

To set up CAPA sources, follow these steps.

1. Go to **Inventory management** \> **Setup** \> **CAPA management** \> **CAPA sources**.
1. Use the buttons on the Action Pane to create new CAPA sources as required. (You can also delete existing sources.)
1. For each new CAPA source, enter a name and a description.

## Set up CAPA types

*CAPA types* let users select a type to categorize each CAPA case.

To set up CAPA types, follow these steps.

1. Go to **Inventory management** \> **Setup** \> **CAPA management** \> **CAPA types**.
1. Use the buttons on the Action Pane to create new CAPA types as required. (You can also delete existing types.)
1. For each new CAPA type, enter a name and a description.

## Set up major/minor classification codes

CAPA types let users select a *major/minor classification code* for each CAPA case.

To set up major/minor classification codes, follow these steps.

1. Go to **Inventory management** \> **Setup** \> **CAPA management** \> **Major/minor classification codes**.
1. Use the buttons on the Action Pane to create new major/minor classification codes as required. (You can also delete existing classification codes.)
1. For each new CAPA classification code, enter a name and a description.

## Set up CAPA root causes

*CAPA root cause codes* let users select the root cause of an issue when they resolve a CAPA case.

To set up CAPA root cause codes, follow these steps.

1. Go to **Inventory management** \> **Setup** \> **CAPA management** \> **CAPA root causes**.
1. Use the buttons on the Action Pane to create new CAPA root causes as required. (You can also delete existing root causes).
1. For each new CAPA root cause, enter a name and a description.
