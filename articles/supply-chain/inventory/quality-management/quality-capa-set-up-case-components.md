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

Before you can begin creating and working with CAPA cases, you must set up the components needed to categorize and process CAPA cases.

## Set up CAPA worker groups

CAPA worker groups let you group users together for CAPA purposes. You can assign a CAPA work group to each activity and stage in your CAPA process. The system uses them to validate worker assignments and can use them to set default workers when a specific worker isn't assigned.

> [!TIP]
> To get started quickly, you can load a set of standard CAPA worker groups from a template provided with Supply Chain Management. You can use the standard groups as-is or modify them to meet your specific needs as described in the rest of this section. For instructions, go to [CAPA administration](quality-capa-admin.md). <!-- KFM: Confirm this. -->

To set up your CAPA worker groups, follow these steps.

1. Go to **Inventory management** \> **Setup** \> **CAPA management** \> **CAPA worker groups**.
1. Use the buttons on the Action Pane to add and remove worker groups as needed. You can't delete worker groups that are assigned to CAPA case activities.
1. For your new or selected worker group, make the following settings in the header:

    - **CAPA worker group** – Enter a name for the worker group. Common examples include *Investigator*, *Implementer*, *Approver* and*Verifier*.
    - **Name** – Enter a short description of the worker group.

1. Use the settings on the **Group settings** FastTab to set up the group, including details related to whether all members of the group can change the stage of a CAPA case and whether the CAPA administrator should be an implied member and/or default worker for the group. Make the following settings:
    - **Allow any member to change stage** – Select this check box if all workers within this CAPA worker group are allowed to change the stage of the CAPA case. Clear this checkbox if you if you want to limit which workers within the group can advance the stage of the CAPA Case.
    - **Implied member of this worker group** – Select this check box if the CAPA administrator, assigned on the Inventory management parameters, should be an implied member of this CAPA worker group. Alternatively, the CAPA administrator can be assigned to the CAPA worker group but if the CAPA administrator is changed, this will require more maintenance. <!-- KFM: This setting seemed to be ignored during the original bug bash with Traci. Does it work? -->
    - **Default worker** – Select this check box if the CAPA administrator should be the default worker for this CAPA worker group. <!-- KFM: This setting seemed to be ignored during the original bug bash with Traci. Does it work? -->

1. Use the **Worker assignments** FastTab to add and remove workers in the group.
    - Too add a worker, use the **New** button the **Overview** tab or go to the **Assign** tab and use the right arrow button move workers into the **Selected workers** list.
    - To remove a worker, use the **Delete** button on the **Overview** tab or go to the **Assign** tab and use the left arrow button move workers out of the **Selected workers** list.

1. Set the following options for each worker in the group:
    - **Allowed** – If the the **Allow any member to change stage** checkbox is cleared on the **Group settings** FastTab, then select the **Allowed** checkbox for each worker that should be allowed to advance CAPA cases to the next stage. If the **Allow any member to change stage** checkbox is selected, then the **Allowed** checkbox on the **Worker assignments** FastTab has no effect.
    - **Default worker** – If the the **Default worker** checkbox is cleared on the **Group settings** FastTab, then select this check box for the worker that should be the default worker for this CAPA worker group. The default worker is used when creating a CAPA case and when advancing CAPA cases to the next stage.

## Set up CAPA categories

CAPA categories allow you to group similar case types together. Organizing CAPA cases by category can help employees identify known solutions, such as knowledge articles, for when similar issues frequently occur. This information is also used by the *Trending analysis by category* feature so employees can review whether the frequency of specific issues is declining over time.

To set up your CAPA categories, follow these steps.

1. Go to **Inventory management** \> **Setup** \> **CAPA management** \> **CAPA categories**.
1. Use the buttons on the Action Pane to add and remove categories as needed. You can't delete categories that are assigned to active CAPA cases. For each category, make the following settings:
    - **CAPA category** – Enter the name of the CAPA category. Typical general category groupings include *Product*, *Vendor*, and *Customer*. Typical detailed category groupings include *Bulk production*, *Production labeling*, *Packaging production*, and *Production resource*.
    - **Description** – Enter a description of the CAPA category.
    - **CAPA subcategory type** – Select the subcategory for the CAPA category. It includes several predefined subcategories (*None*, *Customer*, *Vendor*, and *Product*). It also includes the *User defined* subcategory type, which lets you choose from a collection of custom subcategory types that you've created for your company. The next procedure describes how to set up your custom subcategory types.

To set up your user-defined CAPA subcategory types, follow these steps.

1. Go to **Inventory management** \> **Setup** \> **CAPA management** \> **CAPA categories**.
1. <!-- KFM: select a category? -->On the Action Pane, select **User defined CAPA subcategory.**
1. Use the buttons on the Action Pane to add and remove subcategories as needed. For each subcategory, make the following settings:
    - **CAPA subcategory** – Enter the name of the subcategory.
    - **Description** – Enter a short description of the subcategory.

## Set up CAPA resolutions

<!-- KFM: Not included in vendor docs. Explain the purpose of these, possibly with example values. -->

## Set up CAPA source codes

CAPA source codes let you categorize the source of a CAPA case. You can use source codes to track the source of a CAPA case, such as *Internal audit*, *External audit*, *Ad-hoc testing*, and so on.

To set up your CAPA source codes, go to **Inventory management** \> **Setup** \> **CAPA management** \> **CAPA source codes**. Then use the buttons in the Action Pane to create and delete source codes as needed. For each source code, make the following settings:

- **CAPA source code name** – Enter the name of the source code.
- **CAPA source code Description** – Enter a short description of the source code.

<!-- KFM: check the above labels. -->

## Set up CAPA types

<!-- KFM: Not included in vendor docs. Explain the purpose of these, possibly with example values. -->

## Set up Major/Minor classification codes

<!-- KFM: Not included in vendor docs. Explain the purpose of these, possibly with example values. -->

## Set up CAPA root cause codes

<!-- KFM: Not included in vendor docs. Explain the purpose of these, possibly with example values. -->

## CAPA processes

CAPA processes are hierarchical processes that let you manage and resolve CAPA cases. Each CAPA process comprises a series of stages, each of which can include one or more automatically generated activities. When you create CAPA case, you'll assign a CAPA process required to guide it to completion.

> [!TIP]
> To get started quickly, you can load a set of standard CAPA processes from a template provided with Supply Chain Management. You can use the standard processes as-is or modify them to meet your specific needs as described in the rest of this section. For instructions, go to [CAPA administration](quality-capa-admin.md).

### Manage and approve CAPA processes

To set up and manage your CAPA processes (regardless of whether you started by loading the template), follow these steps.

1. Go to **Inventory management** \> **Setup** \> **CAPA management** \> **CAPA processes**.
1. The **CAPA processes** page opens, showing a list of existing CAPA processes. The following information is shown for the selected process:
    - **Name** – The name of the selected CAPA process. This is read-only for existing processes.
    - **Description** – A short description of the selected CAPA process.
    - **Approved** – Indicates whether the selected CAPA process is approved for use in managing CAPA cases. <!-- KFM: mention what role is needed to be able to change this. --> Only approved CAPA processes are available to users when they create and process a CAPA case.

1. Use buttons on the Action Pane to add and remove processes.
    - To add a new process, select **New**.
    - To delete a selected process, select **Delete**.
    - To edit the name, description or approval status of a selected process, select **Edit**.
    - To view and edit the details of an existing process, select it from the list and, on the Action Pane, open the **Process** tab and select **Details**.

### Configure CAPA process details

When you create a new CAPA process or open the details of an existing one, as described in the previous procedure, you'll see a page with two panes. The left pane shows a hierarchical list of stages and activities that make up the process. Stages are at the top level, and each stage can include one or more activities nested below it. The right pane shows details about the selected stage or activity.

#### FastTabs

- **General** – Set up and view general information about the CAPA process and activity. The information includes the purpose of the activity, start and end dates and time for performing the activity, and CAPA worker group and worker responsible for the activity.
- **Exit criteria** – Set up and view the exit criteria for the selected CAPA process. Activities identified as required must be completed before you can exit the process.

#### Buttons

- **New** – Create a new CAPA process.
- **Delete** – Delete a CAPA process.
- **Save as** – Save the current process to a new name.
- **Functions** – Save the current process or copy an existing CAPA process to a template.
- **Inquiry** – Open the **All CAPA cases** form to view all CAPA cases using the selected CAPA Process for your company.
- **Actions (From the Hierarchy)** – From the hierarchy directly or by using the Actions button, levels and activities can be added to the tree. Options include: Create level, Create action, Create appointment, Create event, Create task, Delete, Details. There are four types of activities used by CAPA cases: Action, Appointment, Event and Task.

#### Fields

- **Name** – Enter or view the name for the CAPA process.
- **Description** – Enter or view a brief description of the CAPA process.
- **Approved** – Select this check box if the CAPA process is approved for use in managing CAPA cases.
- **Name** – View the stage/activity name.
- **Activity number** – View the activity number that is assigned to the activity associated with the process. This number is generated automatically.
- **Purpose** – Enter or view the name or description for the purpose of the activity.
- **Calculated start in (days)** – Enter or view the number of days from the start date of a CAPA case on which the activity should begin.
- **Calculated end in (days)** – Enter or view the number of days from the end date of a CAPA case on which the activity should end.
- **Start time** – Enter or view the start time for the activity.
- **End time** – Enter or view the end time for the activity.
- **Notes** – Enter or view free-form notes about the specific CAPA case activity.
- **CAPA worker group** – Select or view the CAPA worker group that identifies the group of CAPA workers responsible for this activity. When you enter a CAPA worker group for the Stage it will default to the activities within that stage unless indicated otherwise on the Activity.
- **Responsible** – Select or view the identifier for the worker who is responsible for this activity. If one is not specified, the default from the CAPA worker group will be used when the CAPA case is being processed. If entered, the worker selected is validated based on the CAPA worker group assigned. IF the CAPA administration is an implied member of the group, then the CAPA administrator can be manually entered as the responsible worker if desired.
- **Notify group** – Enter or view if the entire CAPA worker group should be notified when stages are advanced. Select Yes, if the group should be notified. Select No, if just the responsible should be notified. Select Inherit, if this determination has been decided at a higher level in the hierarchy. This is used for email notifications when the stage is advanced. This field on the CAPA worker group of the stage being advanced to is the determining factor.
- **Check for required activities** – Select this check box to specify that certain activities in this CAPA process must be completed before the process can be closed.
