---
title: Get started with setting up Warehouse management module
description: This article shows how to work with built-in wizards and checklists that will help you set up and configure the Warehouse management module quickly and efficiently.
author: gfedorova
ms.author: gfedorova 
ms.reviewer: kmaybac
ms.search.form: WHSWarehouseInitiationWizard, WHSManagementInitiationWizard, WHSImplementationWorkspace, WHSImplementationTaskListPage
ms.service: dynamics-365
ms.topic: how-to
ms.date: 11/09/2022
ms.custom: bap-template
---

# Get started with setting up Warehouse management module

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../includes/preview-banner.md)]

This article shows how to work with built-in wizards and checklists that will help you set up and configure the Warehouse management module quickly and efficiently.

## Track the warehouse management configuration processes

Use the **Warehouse implementation tasks** workspace to track your Warehouse management configuration processes. The workspace can be used during a new implementation, after an upgrade, or after a migration.

This workspace lets you create, edit, and import checklists that you can use to identify important implementation tasks and track your progress while completing them. It lets you do the following actions:

- Track progress by viewing all current and closed configuration tasks.
- Select hyperlinks to quickly access the configuration page required for each step.
- Import a default configuration checklist that includes the tasks that must be completed to have warehouse up and running.

### Open the Warehouse implementation tasks workspace

To open the workspace, go to **Warehouse management \> Workspaces \> Warehouse implementation tasks**.

### Import the default configuration checklist

You use **Import default tasks** to import pre-configured Warehouse implementation tasks for you. You can use Add, Edit, Remove, Move up and Move down buttons to adjust the tasks based on your needs that are part of the warehouse management process.

<!--KFM: We need to provide more details about how to import the checklist. Don't we have a standard one that users can import? How can they get it? All I could get was an error message: "Entity Warehouse implementation tasks not found. Refresh entity list from Data import/export framework parameters form." I couldn't find the "Data import/export framework parameters" page--how do we get there?   -->

### Customize the task list

After importing a configuration checklist, you can customize it as needed my adding, remove, and rearranging the tasks. You could also create a fully customized task list by starting with a blank list. Use the following commands in the **Tasks and status** FastTab toolbar to customize the list:

- **Add task** – Create a new task. This opens the **Add task** dialog, where you must define the following:
    - **Task category** – Enter the type of task this is.
    - **Description** – Provide a detailed description of what the user should do to complete this task.
    - **Task link** – Select the page in Supply Chain Management where the user should go to complete this task.
- **Edit task** – Edit a selected task. This opens the **Edit task** dialog, where you can edit the **Description** and **Task link** for the selected task. Other settings are read-only for existing tasks. <!--KFM: What is the **Parent task name** field for? How do we use this? Why isn't this in the **Add task** dialog?. -->
- **Remove** – Delete all selected tasks. You will be prompted to confirm the operation.
- **Move up** – Move the selected task up in the sequence order.
- **Move down** – Move the selected task down in the sequence order.

### Work with the checklist

When your task list is ready, follow these steps to work through it:

1. Go to **Warehouse management \> Workspaces \> Warehouse implementation tasks**.
1. Expand the **Summary** FastTab to see an overview of how many tasks there are in total and what proportion of them have been marked as completed. Select the **Warehouse implementation tasks** tile to open the full task list. <!--KFM: What is this page for? Seems like a duplicate of the **Tasks and status** FastTab. Why would I go here? -->
1. Expand the **Tasks and status** FastTab to see the full list and mark tasks completed as you work. 

    Each tasks shows the following information:

    - **Sequence number** – Indicates the order in which you should complete each task. Start with the lowest number and work up from there.
    - **Completed** – Indicates whether a task has been completed. Mark this check box for each task as you complete them.
    - **Task category** – Tells what kind of task it is. Select this text to open the page in Supply Chain Management where you can make the settings needed to complete the task.
    - **Description** – Provides full details about what must be done to complete the task.
    - **Status** –  <!--KFM: Just duplicates the check box? -->
    - **Completed by** – Complete tasks show the name of the user who completed the task.
    - **Completed date** – Complete tasks shows the date on which the task was completed.

    Use the following fields and buttons in the Tasks and status FastTab toolbar to help you find your way around the list:

    - **Filter** – To quickly find a specific task in a long list, enter a value here and then choose the column in which to find that value.
    - **Hide completed tasks** or **Show completed tasks** – Choose whether to hide or show tasks that have already been completed. The button label toggles based on the current view.

    To see the full task list (including both completed and unfinished tasks), expand the Links FastTab and select the All tasks link. This is the same page that opens when you selectt the **Warehouse implementation tasks** tile on the **Summary** FastTab. <!--KFM: This page again!? Why?-->

1. Continue working until all tasks are complete.

## Initiate the Warehouse management module

The **Warehouse management initiation wizard** provides a step-by-step guide that will help you make the most basic settings required by the Warehouse management module. 

The following table summarizes the configurations made by the wizard.

| Configuration | Action | Description |
| --- | --- | --- |
| Location types | Create | Location types are used as filtering options to control the different warehouse management processes. The wizard will create several location types using the names you specify. After running the wizard, you can add, remove, and/or edit these and other location types by going to **Warehouse management \> Setup \> Warehouse \> Location types**. |
| Location profiles | Create | <!-- KFM: What are these and how do we use them? --> The wizard will create several location profiles using the names you specify. <!--KFM: Where do the various options come from for each created profile? Seems like we only assign a name. --> After running the wizard, you can add, remove, and/or edit these and other location profiles by going to **Warehouse management \> Setup \> Warehouse \> Location profiles**. |
| Location formats | Create | Location formats are a naming system used to create unique and consistent names for the different location bin positions used within a warehouse. It can be useful to use separators as part of the location format to make it easier to identify components of the location such as the aisle number. The wizard will create an initial location format using the name you specify. You can tell the wizard to create separate location formats for each profile or to create one location format for each profile <!-- KFM: These options both seem the same(?) I think we should clarify. -->. After running the wizard, you can add, remove, and/or edit these and other location formats by going to **Warehouse management \> Setup \> Warehouse \> Location formats**. |
| Inventory status | Create | <!-- KFM: What are these and how do we use them? --> The wizard will create an initial inventory status value using the name you specify. After running the wizard, you can add, remove, and/or edit this and other inventory statuses by going to **Warehouse management \> Setup \> Inventory \> Inventory statuses**. |
| Default work user and password | Create | The wizard will create an initial work user using the user name and password you specify.  After running the wizard, you can add, remove, and/or edit this and other work users by going to **Warehouse management \> Setup \> Worker**. |
| Load posting methods | Regenerate | <!-- KFM: What are these and how do we use them? --> The wizard will generate or regenerate the load posting methods. After running the wizard, you can manually regenerate and/or edit the methods list by going to **Warehouse management \> Setup \> Load posting methods**. |
| Wave processing methods | Regenerate | <!-- KFM: What are these and how do we use them? --> The wizard will generate or regenerate the wave processing methods. After running the wizard, you can manually regenerate and/or edit the methods list by going to  **Warehouse management \> Setup \> Waves \> Wave process methods**. |
| Warehouse management parameters | Set up | The wizard will initialize several settings on the **Warehouse management parameters** page based on the settings you make while running the wizard. To open this page, go to **Warehouse management \> Setup \> Warehouse management parameters**. The following values will be set: <ul><li>**User location profile**</li><li>**Location types**</li><li>**Default work user ID**</li><li>**Default inventory status**</li></ul> |

Follow these steps to launch and complete the warehouse management initiation wizard:

1. Go to **Warehouse management \> Setup \> Wizards \> Warehouse management initiation wizard**.
1. The **Warehouse management initiation wizard** opens, showing the **Welcome** page, which summarizes what the wizard will do. When you're done reading the summary, select **Next** to continue.
1. The **Initialize base data** page opens. Use the settings here to establish initial values for the Warehouse management module. Default values are suggested, but you can edit any of them as needed. If you leave any field blank, then the wizard won't initialize that setting. Make the following settings: <!--KFM: We should summarize the purpose of each of the settings listed below. Which are location formats? Which are location types? Which also become assigned "defaults" on the parameters page? -->

    - **Receiving** – 
    - **Staging** – 
    - **Packing** – 
    - **Final shipping** – 
    - **Sorting** – 
    - **User** – 
    - **Create one generic format instead of each profile** – Set this option to *No* to create separate location formats for each location profile. Set this option to *Yes* to create one location format for each location profile. <!-- KFM: These options both seem the same(?) I think we should clarify. -->
    - **Location format** – 
    - **Default inventory status ID** – 
    - **Default work user ID** – 
    - **Default work user password** – 

1. Select **Next** to continue to the **Base data setup complete** page. This page summarizes the settings the wizard will make based on your input. 
1. Select **Finish** to apply the listed settings.
1. **Note:** Your user must be associated with an employee record to successfully create work user. <!--KFM: Describe how to do this here, or give a link. -->

## Warehouse initiation wizard

The **Warehouse initiation wizard** provides a step-by-step guide that will help you set one or more individual warehouses. After completing this wizard, settings will be in place that will allow you to successfully ship sales and receive purchases.

The following table summarizes the configurations made by the wizard.

| Configuration | Action | Description |
| --- | --- | --- |
| Locations | Create | <!-- KFM: What are these and how do we use them? --> The wizard will create several locations using the names you specify. After running the wizard, you can add, remove, and/or edit these and other locations by going to **Warehouse management \> Setup \> Warehouse \> Locations**. |
| Directive codes | Create | <!-- KFM: What are these and how do we use them? --> The wizard will create several directive codes using the names you specify. After running the wizard, you can add, remove, and/or edit these and other directive codes by going to **Warehouse management \> Setup \> Directive codes**. |
| Work classes | Create | <!-- KFM: What are these and how do we use them? --> The wizard will create several work classes using the names you specify. After running the wizard, you can add, remove, and/or edit these and other work classes by going to **Warehouse management \> Setup \> Work \> Work classes**. |
| Location directives | Create | <!-- KFM: What are these and how do we use them? --> The wizard will create several location directives using the names you specify. Only location directives with a work order type of *Sales orders* or *Purchase orders* will be created. After running the wizard, you can add, remove, and/or edit these and other location directives by going to **Warehouse management \> Setup \> Location directives**. |
| Wave templates | Create | <!-- KFM: What are these and how do we use them? --> The wizard will create several wave templates using the names you specify. Only wave templates with wave template type *Shipping* will be created. After running the wizard, you can add, remove, and/or edit these and other wave templates by going to **Warehouse management \> Setup \> Waves \> Wave templates**. |
| Work templates | Create | <!-- KFM: What are these and how do we use them? --> The wizard will create several work templates using the names you specify. Only work templates with a work order type of *Sales orders* or *Purchase orders* will be created. After running the wizard, you can add, remove, and/or edit these and other work templates by going to **Warehouse management \> Setup \> Work \> Work templates**. |
| Location types | Create | <!-- KFM: What are these and how do we use them? --> The wizard will create several location types using the names you specify. After running the wizard, you can add, remove, and/or edit these and other location types by going to **Warehouse management \> Setup \> Warehouse \> Location types**. |

Follow these steps to launch and complete the warehouse initiation wizard:

1. Go to **Warehouse management \> Setup \> Wizards \> Warehouse initiation wizard**.
1. The **Warehouse initiation wizard** opens, showing the **Welcome** page, which summarizes what the wizard will do. When you're done reading the summary, select **Next** to continue.
1. The **Warehouses selection** page opens. This page lists the warehouses currently available in the system for the currently selected legal entity. Only warehouses that have **Use warehouse management processes** set to *Yes* are listed. <!--KFM: Will anything be listed here for a brand new installation? If not, should we add a step to first create one or more warehouses (or a section, or maybe just a link) ? --> Select the check box for each warehouse that you want to set up using the wizard.
1. Select **Next** to continue to the **General warehouse setup** page. Use the settings here to define names for purchase and sales processes. Default values are suggested, but you can edit any of them as needed. Make the following settings: <!--KFM: We should summarize the purpose of each of the settings listed below -->

    - **Purchase work class** – 
    - **Purchase work template** – 
    - **Sales work template** – 
    - **Shipping wave template** – 
    - **Sales pick location directive** – 
    - **Purchase put location directive** – 

1. Select **Next** to continue to the **Staging area setup** page. Use the settings here to define whether you will use a staging area in your outbound processes and, if so, set up this feature.<!--KFM: Maybe briefly tell what a staging area is and why the user might want one. --> Default values are suggested, but you can edit any of them as needed. Make the following settings: <!--KFM: We should summarize the purpose of each of the settings listed below. -->

    - **Use staging area** – Select this check box if you will use a staging area. If you clear this check box, no staging area will be set up and all of the other settings on this page will be disabled.
    - **Location** – 
    - **Directive code** – 
    - **Sales work class** – 
    - **Sales put location directive** – 

1. Select **Next** to continue to the **Final shipping area setup** page. Use the settings here to define the names for the final shipping area in the outbound processes. Default values are suggested, but you can edit any of them as needed. Make the following settings: <!--KFM: We should summarize the purpose of each of the settings listed below -->

    - **Location** – 
    - **Directive code** – 
    - **Sales work class** – 
    - **Sales put location directive** – 

1. Select **Next** to continue to the **Warehouse setup complete** page, which summarizes the actions the wizard will take. Review the summary and, if it looks right, select **Finish** to apply the settings and close the wizard.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
