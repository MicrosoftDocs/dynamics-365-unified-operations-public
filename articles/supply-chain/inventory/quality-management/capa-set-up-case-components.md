---
title: Set up CAPA case components
description: Before you can begin creating and working with CAPA cases, you must set up the components needed to categorize and process CAPA cases.
author: johanhoffmann
ms.author: johanho
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 11/25/2024
ms.custom: 
  - bap-template
---

# Set up CAPA case components

[!include [banner](../../includes/banner.md)]

Before you can begin creating and working with CAPA cases, you must set up the components needed to categorize and process CAPA cases.

## Set up CAPA categories

CAPA categories allow you to group similar case types together. Organizing CAPA cases by category can help employees identify known solutions, such as knowledge articles, for when similar issues frequently occur. This information is also used by the *Trending analysis by category* feature so employees can review whether the frequency of specific issues is declining over time.

To set up your CAPA categories, follow these steps.

1. Go to **Inventory management** \> **Setup** \> **CAPA management** \> **CAPA categories**.
1. Use the buttons on the Action Pane to add and remove categories as needed. You can't delete categories that are assigned to active CAPA cases. For each category, make the following settings:
    - **CAPA category** – Enter the name of the CAPA category. General category groupings are Product related, Vendor related, Customer related. Detailed category groupings: Bulk production related, Production labeling related, Packaging production related; Production resource related.
    - **Description** – Enter a description of the CAPA category.
    - **CAPA subcategory type** – Select the subcategory for the CAPA category. The *User defined* subcategory type lets you choose from a collection of custom subcategory types that you've created for your company. See the next procedure for details about how to set up your custom subcategory types.

To set up your user-defined CAPA subcategory types, follow these steps.

1. Go to **Inventory management** \> **Setup** \> **CAPA management** \> **CAPA categories**.
1. On the Action Pane, select **User defined CAPA subcategory.**
1. Use the buttons on the Action Pane to add and remove subcategories as needed. For each subcategory, make the following settings:
    - **CAPA subcategory** – Enter the name of the subcategory.
    - **Description** – Enter a short description of the subcategory.

## Set up CAPA worker groups

CAPA worker groups let you group users together for CAPA purposes. You can assign a CAPA work group to each activity and stage in your CAPA process. The system uses them to validate worker assignments and can use them to set default workers when a specific worker isn't assigned.

To set up your CAPA worker groups, follow these steps.

1. Go to **Inventory management** \> **Setup** \> **CAPA management** \> **CAPA worker groups**.
1. Use the buttons on the Action Pane to add and remove worker groups as needed. You can't delete worker groups that are assigned to CAPA case activities.
1. For your new or selected worker group, make the following settings in the header:

    - **CAPA worker group** – Enter a name for the worker group. Common examples include *Investigator*, *Implementer*, *Approver* and*Verifier*.
    - **Name** – Enter a short description of the worker group.

1. Use the settings on the **Group settings** FastTab to set up the group, including details related to whether all members of the group can change the stage of a CAPA case and whether the CAPA administrator should be an implied member and/or default worker for the group. Make the following settings:
    - **Allow any member to change stage** – Select this check box if all workers within this CAPA worker group are allowed to change the stage of the CAPA case.
    - **Implied member of this worker group** – Select this check box if the CAPA administrator, assigned on the Inventory management parameters, should be an implied member of this CAPA worker group. Alternatively, the CAPA administrator can be assigned to the CAPA worker group but if the CAPA administrator is changed, this will require more maintenance.
    - **Default worker** – Select this check box if the CAPA administrator should be the default worker for this CAPA worker group.

1. Use the settings on the **Worker assignments** FastTab to assign workers to the group.

Workers can be assigned to a CAPA worker group by either using the Worker assignments FastTab by using the New button or by changing to the Assign tab and using the arrows to assign workers.

You can delete workers from the CAPA worker group by using the Delete button on the Overview tab or by using the right arrow on the Assign tab. Workers are set up through the Human Resources menu. Workers are associated to a given User Id through the Relations action.

Once a worker is assigned to the CAPA worker group, select the Allowed checkbox if this worker can advance the CAPA Case to the next stage.

If the **Allow any member to change stage** checkbox is selected, then the Allowed checkbox on the Worker assignment is not used. You only need to specify this checkbox if you want to limit which workers within the group can advance the stage of the CAPA Case.

If the CAPA administrator is not the default worker of the worker group, you can select which worker is the default worker for this CAPA worker group. The default worker is used when creating a CAPA case or when CAPA cases are advancing stages.

## CAPA processes

After you set up the CAPA worker groups, you can set up the hierarchical processes you plan to use for managing and resolving CAPA cases. When a CAPA case is created, a CAPA process can be assigned. This will guide the case through the assigned process so that activities can be automatically generated as the CAPA Case advances through the stages. You set up CAPA processes in the **CAPA processes** form.
