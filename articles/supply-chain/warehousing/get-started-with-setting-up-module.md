---
title: Get started with setting up Warehouse Management module
description: This article provides an overview that will help you configure Warehouse management module in a fast and efficient way.
author: gfedorova
ms.author: gfedorova 
ms.reviewer: kmaybac
ms.search.form: WHSWarehouseInitiationWizard, WHSManagementInitiationWizard
ms.service: dynamics-365
ms.topic: how-to
ms.date: 09/29/2022
ms.custom: bap-template
---

# Get started with setting up Warehouse Management module

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../includes/preview-banner.md)]

This article provides capabilities overview that will help you configure Warehouse management module in a fast and efficient way.

## Warehouse implementation tasks workspace

The Warehouse implementation tasks workspace lets you track warehouse management configuration processes. The workspace can be used during a new implementation, after an upgrade, or after a migration.

This workspace lets you maintain and track warehouse implementation checklists. It allows:
- Track the progress by viewing all current and closed configuration tasks.
- Quick access to the required configuration though hyperlinks..
- Import default configuration checklist with required list of tasks that need to be completed to have warehouse up and running. 

You can see all remaining tasks in the **Summary** section in addition to a completed vs remaining chart that helps you track and manage the amount of work remaining to implement warehousing module.

In the  **Tasks and status**  section, you can see the full task list and can be filtered so that it shows only the tasks that you're interested in. You can filter the task list in several ways. For example, you can filter by task category, descriptions. You can also select to show or hide completed tasks in the task list.

You use **Import default tasks** to import pre-configured Warehouse implementation tasks for you. You can use Add, Edit, Remove, Move up and Move down buttons to adjust the tasks based on your needs that are part of the warehouse management process.

The task name is a hyperlink to the page where the user must go to complete the work. You can set this hyperlink by using the  **Task link**  field when you edit or create a task.

The  **Completed by**  option will be automatically filled after the task is completed with the name of the worker who completed the task. When a task is marked as completed, the  **Completed date**  field is automatically updated to the current date and time.

To access the workspace, navigate to **Warehouse management \> Workspaces \> Warehouse implementation tasks**

## Warehouse management initiation wizard

The Warehouse management initiation wizard is used to complete mandatory warehouse pre-configuration with step-by-step guides.

For warehouse management initiation wizard, go to **Warehouse management \> Setup \> Wizards \> Warehouse management initiation wizard**.

On the **Welcome** page of the wizard, you will be able to see the wizard description.

The next page in the wizard is the **Initialize base data** page. It's used to define the names for the configuration. On this page, default recommendations are suggested with the possibility to override those values. Clearing out field values means that nothing will be created for the blanked fields. On the **Base data setup complete** page of the wizard, you will be able to see the summary of the future changes.

The wizard will automate the following processes:

| **Configuration** | **Action** | **Description** |
| --- | --- | --- |
| Location types | Create | Location types defined in the wizard will be automatically created. Created location types can be found here: **Warehouse management \> Setup \> Warehouse \> Location types**. |
| Location profiles | Create | Location profiles defined in the wizard will be automatically created. Created location profiles can be found here: **Warehouse management \> Setup \> Warehouse \> Location profiles**. |
| Location formats | Create | Location formats defined in the wizard will be automatically created. Created location formats can be found here: **Warehouse management \> Setup \> Warehouse \> Location formats**. If **Create one generic format instead of each profile** parameter is disabled, separate location formats are created for each location profile. If enabled, one location format is created for each location profile. |
| Inventory status | Create | Inventory status defined in the wizard will be automatically created. Created inventory status can be found here: **Warehouse management \> Setup \> Inventory \> Inventory statuses**. |
| Default work user and password | Create | Default worker and the password defined in the wizard will be automatically created. Default worker created can be found here: **Warehouse management \> Setup \> Worker**. **Note:** Your user must be associated with the employee record in order to successfully create work user. |
| Load posting methods | Regenerate | Load posting methods will be automatically regenerated. Regenerated methods can be found here: **Warehouse management \> Setup \> Load posting methods**. |
| Wave processing methods | Regenerate | Wave processing methods will be automatically regenerated. Regenerated methods can be found here: **Warehouse management \> Setup \> Waves \> Wave process methods**. |
| Warehouse management parameters | Set up | Warehouse management parameters will be initialized based on the created settings. Warehouse management parameters can be found here: **Warehouse management \> Setup \> Warehouse management parameters**. The following values will be set up automatically: <ul><li>User location profile</li><li>Location types</li><li>Default work user ID</li><li>Default inventory status </li></ul> |

## Warehouse initiation wizard

The Warehouse initiation wizard is used to complete warehouse purchase and sales processes with step-by-step guides.

For warehouse management initiation wizard, go to **Warehouse management \> Setup \> Wizards \> Warehouse initiation wizard**.

On the **Welcome** page of the wizard, you will be able to see the wizard description.

The next page in the wizard is the **Warehouse selection** page. On this page, select the warehouse that you will be setting up processes for. Only warehouses that have "Use warehouse management processes" parameter enabled, will be displayed.

The next page in the wizard is the **General warehouse setup** page. It's used to define the names for the configuration of the purchase and sales processes. On this page, default recommendations are suggested with the possibility to override those values. On the **Staging area setup** page of the wizard, define whether you need the staging area in the outbound processes. On the **Final shipping area setup** page of the wizard, define the names for the final shipping area configuration in the outbound processes. On the **Warehouse setup complete** page of the wizard, you will be able to see the summary of the future changes.

After this wizard execution, you will be able to successfully execute sales shipment and purchase receive basic processes. The wizard will automate the following:

| **Configuration** | **Action** | **Description** |
| --- | --- | --- |
| Locations | Create | Locations defined in the wizard will be automatically created. Created locations can be found here: **Warehouse management \> Setup \> Warehouse \> Locations**. |
| Directive codes | Create | Directive codes defined in the wizard will be automatically created. Created directive codes can be found here: **Warehouse management \> Setup \> Directive codes**. |
| Work classes | Create | Work classes defined in the wizard will be automatically created. Created work classes can be found here: **Warehouse management \> Setup \> Work \> Work classes**. |
| Location directives | Create | Location directives defined in the wizard will be automatically created. Created location directives can be found here: **Warehouse management \> Setup \> Location directives**. **Note** : Only location directives with work order types Sales orders and Purchase orders will be created. |
| Wave templates | Create | Wave templates defined in the wizard will be automatically created. Created wave templates can be found here: **Warehouse management \> Setup \> Waves \> Wave templates**. **Note** : Only wave templates with wave template type Shipping will be created. |
| Work templates | Create | Work templates defined in the wizard will be automatically created. Created work templates can be found here: **Warehouse management \> Setup \> Work \> Work template**. **Note** : Only location directives with work order types Sales orders and Purchase orders will be created. |


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
