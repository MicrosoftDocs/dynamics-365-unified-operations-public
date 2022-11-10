---
title: Get started with setting up Warehouse management module
description: This article explains how to work with the built-in wizards and checklists that will help you set up and configure the Warehouse management module quickly and efficiently.
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

This article explains how to work with the built-in wizards and checklists that will help you set up and configure the Warehouse management module quickly and efficiently.

## Track the warehouse management configuration processes

Use the **Warehouse implementation tasks** workspace to track your Warehouse management configuration processes. The workspace can be used during a new implementation, after an upgrade, or after a migration.

This workspace lets you create, edit, and import checklists that you can use to identify important implementation tasks and track your progress while completing them. It lets you do the following actions:

- Track progress by viewing all current and closed configuration tasks.
- Select hyperlinks to quickly access the configuration page required for each step.
- Import a default configuration checklist that includes the tasks that must be completed to have warehouse up and running.

### Open the Warehouse implementation tasks workspace

To open the workspace, go to **Warehouse management \> Workspaces \> Warehouse implementation tasks**.

### Import the default configuration task list

Use **Import default tasks** to import pre-configured Warehouse implementation tasks.

> [!NOTE]
>  Import cannot be successfully completed if **Warehouse implementation tasks** data entity is not available in the environment. To manualy refresh entity list, go to  **Data management worspace \> Framework parameters \> Entity settings \> Refresh entity list**.

<!--KFM: We need to provide more details about how to import the checklist. Don't we have a standard one that users can import? How can they get it? All I could get was an error message: "Entity Warehouse implementation tasks not found. Refresh entity list from Data import/export framework parameters form." I couldn't find the "Data import/export framework parameters" page--how do we get there?   -->

### Customize the task list

After importing a task list, you can customize it as needed my adding, removing, and rearranging the tasks. You could also create a fully customized task list by starting with a blank list. Use the following commands in the **Tasks and status** FastTab toolbar to customize the list:

- **Add task** – Create a new task. This opens the **Add task** dialog, where you must define the following:
    - **Task category** – Enter the type of task this is.
    - **Description** – Provide a detailed description of what the user should do to complete this task.
    - **Task link** – Select the page in Supply Chain Management where the user should go to complete this task.
- **Edit task** – Edit a selected task. This opens the **Edit task** dialog, where you can edit the **Description** and **Task link** for the selected task. Other settings are read-only for existing tasks. <!--KFM: What is the **Parent task name** field for? How do we use this? Why isn't this in the **Add task** dialog?. --> <!--GFE: We will remove this field, so I do not want to mention it here-->
- **Remove** – Delete all selected tasks. You will be prompted to confirm the operation.
- **Move up** – Move the selected task up in the sequence order.
- **Move down** – Move the selected task down in the sequence order.

### Work with the task list

When your task list is ready, follow these steps to work through it:

1. Go to **Warehouse management \> Workspaces \> Warehouse implementation tasks**.
1. Expand the **Summary** FastTab to see an overview of how many tasks there are in total and what proportion of them have been marked as completed. Use the **Warehouse implementation tasks** tile to track the remaining task list. <!--KFM: What is this page for? Seems like a duplicate of the **Tasks and status** FastTab. Why would I go here? --> <!--GFE: Tile represents the remainging tasks. We might add additional tiles in other states, and each tile would open the filtered list of tasks. But for now we have 1 tile that opens up the remaining tasks-->
1. Expand the **Tasks and status** FastTab to see the full list and mark tasks completed as you work. 

    Each tasks shows the following information:

    - **Sequence number** – Indicates the order in which you should complete each task. Start with the lowest number and work up from there.
    - **Completed** – Indicates whether a task has been completed. Mark this check box for each task as you complete them.
    - **Task category** – Tells what kind of task it is. Select this text to open the page where you can make the settings needed to complete the task.
    - **Description** – Provides full details about what must be done to complete the task.
    - **Status** –  Complete tasks show the icon. <!--KFM: Just duplicates the check box? What values/icons might appear here? -->
    - **Completed by** – Complete tasks show the name of the user who completed the task.
    - **Completed date** – Complete tasks shows the date on which the task was completed.

    Use the following fields and buttons in the **Tasks and status** FastTab toolbar to help you find your way around the list:

    - **Filter** – To quickly find a specific task in a long list, enter a value here and then choose the column in which to find that value.
    - **Hide completed tasks** or **Show completed tasks** – Choose whether to hide or show tasks that have already been completed. The button label toggles based on whether completed tasks are currently shown.

    To see the full task list (including both completed and unfinished tasks), expand the Links FastTab and select the All tasks link. This is the same page that opens when you select the **Warehouse implementation tasks** tile on the **Summary** FastTab. <!--KFM: This page again!? Why?--> <!--Agree that most users will use eiher tile, or tasks section, but we tried to stick to other worspaces. If you check Financial period close workspace - they have the same pattern-->

1. Continue working until all tasks are complete.

## Initiate the Warehouse management module

The **Warehouse management initiation wizard** provides a step-by-step guide that will help you make the most basic settings required by the Warehouse management module. Use this wizard for new legal entities where you need to configure warehouse management module from scratch. In general, this wizard will define main settings of Warehouse management parameters for you. <!--KFM: In what circumstances should we use this wizard? How does it relate to the other tools on this page? -->

The following table summarizes the configurations made by the wizard.

| Configuration | Action | Description |
| --- | --- | --- |
| Location types | Create | Location types are used as filtering options to control the different warehouse management processes. The wizard will create several location types using the names you specify. After running the wizard, you can add, remove, and/or edit these and other location types by going to **Warehouse management \> Setup \> Warehouse \> Location types**. |
| Location profiles | Create | Location profiles are used to control the behavior of locations in an advanced warehouse management enabled warehouse. <!-- KFM: What are these and how do we use them? --> The wizard will create several location profiles using the names you specify. <!--KFM: Where do the various options come from for each created profile? Seems like we only assign a name. --> <!--GFE We setup parameters for users that must be setup, otherwise they would get errors or wrong configurations--> After running the wizard, you can add, remove, and/or edit these and other location profiles by going to **Warehouse management \> Setup \> Warehouse \> Location profiles**. |
| Location formats | Create | Location formats are a naming system used to create unique and consistent names for the different location bin positions used within a warehouse. It can be useful to use separators as part of the location format to make it easier to identify components of the location such as the aisle number. The wizard will create an initial location format using the name you specify. You can tell the wizard to create separate location formats for each profile or to create one location format and use one format in each profile. <!-- KFM: These options both seem the same(?) I think we should clarify. --> <!--GFE You eigher create multiple formats: Recv, Stage, Baydoor etc and assign it to profile, so Profile Stage, would have format Stage, profile Baydoor would have format Baydoor, or it would create 1 format and then Profile Stage, Baydoor, would have format General for example.--> After running the wizard, you can add, remove, and/or edit these and other location formats by going to **Warehouse management \> Setup \> Warehouse \> Location formats**. |
| Inventory status | Create | Inventory statuses are used to categorize and keep track of inventory <!-- KFM: What are these and how do we use them? --> The wizard will create an initial inventory status value using the name you specify. After running the wizard, you can add, remove, and/or edit this and other inventory statuses by going to **Warehouse management \> Setup \> Inventory \> Inventory statuses**. |
| Default work user and password | Create | Default work user is used for automated work transactions. <!-- KFM: Explain what a "work user" is. -->  The wizard will create an initial work user using the user name and password you specify.  After running the wizard, you can add, remove, and/or edit this and other work users by going to **Warehouse management \> Setup \> Worker**. |
| Load posting methods | Regenerate | Load posting methods are used when the load is released to the warehouse from the load planning workbench. <!-- KFM: What are these and how do we use them? --> The wizard will generate or regenerate the load posting methods. After running the wizard, you can manually regenerate and/or edit the methods list by going to **Warehouse management \> Setup \> Load posting methods**. |
| Wave processing methods | Regenerate | Wave processing methods are used to perform the actions that are created by the wave template. <!-- KFM: What are these and how do we use them? --> The wizard will generate or regenerate the wave processing methods. After running the wizard, you can manually regenerate and/or edit the methods list by going to  **Warehouse management \> Setup \> Waves \> Wave process methods**. |
| Warehouse management parameters | Set up | The wizard will initialize several settings on the **Warehouse management parameters** page based on the settings you make while running the wizard. To open this page, go to **Warehouse management \> Setup \> Warehouse management parameters**. The following values will be set: <ul><li>**User location profile**</li><li>**Location types**</li><li>**Default work user ID**</li><li>**Default inventory status**</li></ul> |

Follow these steps to launch and complete the warehouse management initiation wizard:

1. Go to **Warehouse management \> Setup \> Wizards \> Warehouse management initiation wizard**.
1. The **Warehouse management initiation wizard** opens, showing the **Welcome** page, which summarizes what the wizard will do. When you're done reading the summary, select **Next** to continue.
1. The **Initialize base data** page opens. Use the settings here to establish initial values for the Warehouse management module. Default values are suggested, but you can edit any of them as needed. If you leave any field blank, then the wizard won't initialize that setting. Make the following settings: <!--KFM: We should summarize the purpose of each of the settings listed below. Which are location formats? Which are location types? Which also become assigned "defaults" on the parameters page? -->

    - **Receiving** – Define the name for receiving location type and location profile. This value will then be set in the warehouse management parameters.   
    - **Staging** – Define the name for staging location type and location profile. This value will then be set in the warehouse management parameters. 
    - **Packing** – Define the name for packing location type and location profile. This value will then be set in the warehouse management parameters. 
    - **Final shipping** – Define the name for final shipping location type and location profile. This value will then be set in the warehouse management parameters. 
    - **Sorting** – Define the name for sorting location type and location profile. This value will then be set in the warehouse management parameters. 
    - **User** – Define the name for user location type and location profile. This value will then be set in the warehouse management parameters. 
    - **Create one generic format instead of each profile** – Set this option to *No* to create separate location formats for each location profile. Set this option to *Yes* to create one location format for all location profiles. If this parameter is set to *No*, the wizard will create location formats with the names defined in the *Receiving*, *Staging*, *Packing*, *Final shipping*, *User* fields. If this parameter is set to *Yes*, the wizard will create one location format with the name defined below.  <!-- KFM: These options both seem the same(?) I think we should clarify. -->
    - **Location format** – Define the name for location format. 
    - **Default inventory status ID** – Define the name for default inventory status. This value will then be set in the warehouse management parameters. 
    - **Default work user ID** – Define the name for default work user. This value will then be set in the warehouse management parameters. 
    - **Default work user password** – Define the password for default work user.

1. Select **Next** to continue to the **Base data setup complete** page. This page summarizes the settings the wizard will make based on your input. 
1. Select **Finish** to apply the listed settings.

> [!NOTE]
>  Your work user must be associated with an employee record to successfully create work user. <!--KFM: Describe how to do this here, or give a link. -->
> - Go to **System administration \> Users \> Users**. 
> - Find the user ID that needs an associated person. 
> - Select the hyperlink **User ID**. 
> - In the **Person** field, select an employee. 

## Warehouse initiation wizard

The **Warehouse initiation wizard** provides a step-by-step guide that will help you set one or more individual warehouses. After completing this wizard, settings will be in place that will allow you to successfully ship sales and receive purchases. Use this wizard for new legal entities or new warehouses where you need to configure basic inbound and outbound flows. <!--KFM: Describe how to do this here, or give a link. -->
 <!--KFM: In what circumstances should we use this wizard? How does it relate to the other tools on this page? -->

> [!NOTE]
>  Before executing this wizard, make sure that **Warehouse management parameters** are configured either manually or with help of **Warehouse management initiation wizard** described above.  

The following table summarizes the configurations made by the wizard.

| Configuration | Action | Description |
| --- | --- | --- |
| Locations | Create | Locations are used to determine where items are stored and where items are picked from and put to in warehouse.<!-- KFM: What are these and how do we use them? --> The wizard will create several locations using the names you specify. After running the wizard, you can add, remove, and/or edit these and other locations by going to **Warehouse management \> Setup \> Warehouse \> Locations**. |
| Directive codes | Create | Directive codes are used as a link between the work templates and the location directives. <!-- KFM: What are these and how do we use them? --> The wizard will create several directive codes using the names you specify. After running the wizard, you can add, remove, and/or edit these and other directive codes by going to **Warehouse management \> Setup \> Directive codes**. |
| Work classes | Create | Work classes are used to direct and/or limit the type of work order lines that a warehouse worker can process on a mobile device. <!-- KFM: What are these and how do we use them? --> The wizard will create several work classes using the names you specify. After running the wizard, you can add, remove, and/or edit these and other work classes by going to **Warehouse management \> Setup \> Work \> Work classes**. |
| Location directives | Create | Location directive are used identify pick and put locations for inventory movement. <!-- KFM: What are these and how do we use them? --> The wizard will create several location directives using the names you specify. Only location directives with a work order type of *Sales orders* or *Purchase orders* will be created. After running the wizard, you can add, remove, and/or edit these and other location directives by going to **Warehouse management \> Setup \> Location directives**. For more information, see [Work with location directives](create-location-directive.md)|
| Wave templates | Create | Wave templates are used to define the wave execution process and setup criteria for when waves are created, executed, and released. <!-- KFM: What are these and how do we use them? --> The wizard will create several wave templates using the names you specify. Only wave templates with wave template type *Shipping* will be created. After running the wizard, you can add, remove, and/or edit these and other wave templates by going to **Warehouse management \> Setup \> Waves \> Wave templates**. |
| Work templates | Create | Work templates are used to  create work at various points in the system. <!-- KFM: What are these and how do we use them? --> The wizard will create several work templates using the names you specify. Only work templates with a work order type of *Sales orders* or *Purchase orders* will be created. After running the wizard, you can add, remove, and/or edit these and other work templates by going to **Warehouse management \> Setup \> Work \> Work templates**. |

Follow these steps to launch and complete the warehouse initiation wizard:

1. Go to **Warehouse management \> Setup \> Wizards \> Warehouse initiation wizard**.
1. The **Warehouse initiation wizard** opens, showing the **Welcome** page, which summarizes what the wizard will do. When you're done reading the summary, select **Next** to continue.
1. The **Warehouses selection** page opens. This page lists the warehouses currently available in the system for the currently selected legal entity. Only warehouses that have **Use warehouse management processes** set to *Yes* are listed. <!--KFM: Will anything be listed here for a brand new installation? If not, should we add a step to first create one or more warehouses (or a section, or maybe just a link) ? --> <!--GFE We have Warehouse creation as a step in our default tasks of the workspace. Before they execute the wizard, ideally they should have warehouse created already.--> Select the check box for each warehouse that you want to set up using the wizard.
1. Select **Next** to continue to the **General warehouse setup** page. Use the settings here to define names for purchase and sales processes. Default values are suggested, but you can edit any of them as needed. Make the following settings: <!--KFM: We should summarize the purpose of each of the settings listed below -->

    - **Purchase work class** – Define the name for work class of receiving process. This value then will be used in the work template. 
    - **Purchase work template** – Define the name for work template of receiving process.  
    - **Sales work template** – Define the name for work template of shipping process.
    - **Shipping wave template** – Define the name for wave template of shipping process.
    - **Sales pick location directive** – Define the name for pick location directive of shipping process. 
    - **Purchase put location directive** – Define the name for put location directive of receiving process. 

1. Select **Next** to continue to the **Staging area setup** page. Use the settings here to define whether you will use a staging area in your outbound processes and, if so, set up this feature. You might need to use it if you pick your items and then place them in a staging location where all lines of the order will be held. In this area items can be packed, relabeled, or loaded onto a delivery truck, and then sent out the door.<!--KFM: Maybe briefly tell what a staging area is and why the user might want one. --> Default values are suggested, but you can edit any of them as needed. Make the following settings: <!--KFM: We should summarize the purpose of each of the settings listed below. -->

    - **Use staging area** – Select this check box if you will use a staging area. If you clear this check box, no staging area will be set up and all of the other settings on this page will be disabled.
    - **Location** – Define the name for staging location.
    - **Directive code** – Define the name for directive code of shipping process. This value then will be used in the shipping work template and location directive to link them together. 
    - **Sales work class** – Define the name for wor class of shipping process.  This value then will be used in the work template. 
    - **Sales put location directive** – Define the name for put location directive of shipping process. 

1. Select **Next** to continue to the **Final shipping area setup** page. Use the settings here to define the names for the final shipping area in the outbound processes. Default values are suggested, but you can edit any of them as needed. Make the following settings: <!--KFM: We should summarize the purpose of each of the settings listed below -->

    - **Location** – Define the name for final shipping location
    - **Directive code** – Define the name for directive code of shipping process. This value then will be used in the shipping work template and location directive to link them together.
    - **Sales work class** – Define the name for wor class of shipping process.  This value then will be used in the work template. 
    - **Sales put location directive** – Define the name for put location directive of shipping process.

1. Select **Next** to continue to the **Warehouse setup complete** page, which summarizes the actions the wizard will take. Review the summary and, if it looks right, select **Finish** to apply the settings and close the wizard.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
