---
title: Get started with setting up the Warehouse management module
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

# Get started with setting up the Warehouse management module

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

Supply Chain Management includes a default task list, which is a good place to start when planning and executing your warehouse management setup. Follow these steps to import it into your **Warehouse implementation tasks** workspace.

1. Go to **Warehouse management \> Workspaces \> Warehouse implementation tasks**.
1. Expand the **Tasks and status** FastTab.
1. Select **Import default tasks** from the FastTab toolbar.
1. The default tasks should now load. If you instead see an error ("Entity Warehouse implementation tasks not found. Refresh entity list from Data import/export framework parameters form"), then do the following steps:
    1. Go to **System administration \> Workspaces \> Data management**.
    1. Select the **Framework parameters** tile.
    1. Open the **Entity settings** tab.
    1. Select **Refresh entity** list.
    1. The system adds a refresh entity job to your batch job list and will run it as soon as possible. You may need to allow several minutes for the task to complete (depending on how many other jobs you have in the queue).
    1. When the refresh job is complete, go back to the **Warehouse implementation tasks** page and select **Import default tasks** from **Tasks and status** FastTab toolbar again.

### Customize the task list

After importing a task list, you can customize it as needed my adding, removing, and rearranging the tasks. You could also create a fully customized task list by starting with a blank list. Use the following commands in the **Tasks and status** FastTab toolbar to customize the list:

- **Add task** – Create a new task. This opens the **Add task** dialog, where you must define the following:
  - **Task category** – Enter the type of task this is.
  - **Description** – Provide a detailed description of what the user should do to complete this task.
  - **Task link** – Select the page in Supply Chain Management where the user should go to complete this task.
- **Edit task** – Edit a selected task. This opens the **Edit task** dialog, where you can edit the **Description** and **Task link** for the selected task. Other settings are read-only for existing tasks.
- **Remove** – Delete all selected tasks. You will be prompted to confirm the operation.
- **Move up** – Move the selected task up in the sequence order.
- **Move down** – Move the selected task down in the sequence order.

### Work with the task list

When your task list is ready, follow these steps to work through it:

1. Go to **Warehouse management \> Workspaces \> Warehouse implementation tasks**.
1. Expand the **Summary** FastTab to see an overview of how many tasks there are in total and what proportion of them have been marked as completed.
1. Expand the **Tasks and status** FastTab to see the full list and mark tasks completed as you work.

    Each tasks shows the following information:

    - **Sequence number** – Indicates the order in which you should complete each task. Start with the lowest number and work up from there.
    - **Completed** – Indicates whether a task has been completed. Mark this check box for each task as you complete them.
    - **Task category** – Tells what kind of task it is. Select this text to open the page where you can make the settings needed to complete the task.
    - **Description** – Provides full details about what must be done to complete the task.
    - **Status** – Shows a check icon to indicate tasks that have been finished.
    - **Completed by** – Complete tasks show the name of the user who completed the task.
    - **Completed date** – Complete tasks show the date on which the task was completed.

    Use the following fields and buttons in the **Tasks and status** FastTab toolbar to help you find your way around the list:

    - **Filter** – To quickly find a specific task in a long list, enter a value here and then choose the column in which to find that value.
    - **Hide completed tasks** or **Show completed tasks** – Choose whether to hide or show tasks that have already been completed. The button label toggles based on whether completed tasks are currently shown.

    To see the full task list (including both completed and unfinished tasks), expand the Links FastTab and select the All tasks link. This is the same page that opens when you select the **Warehouse implementation tasks** tile on the **Summary** FastTab. The page provides the same information and works similarly to the **Task list** FastTab on the **Warehouse implementation tasks** page.

1. Continue working until all tasks are complete.

## Initiate the Warehouse management module

The **Warehouse management initiation wizard** provides a step-by-step guide that will help you make the most basic settings required by the Warehouse management module. Use this wizard for new legal entities where you need to configure warehouse management module from scratch. The wizard will define main settings of Warehouse management parameters for you. The default task list (described previously in this article) includes steps for setting up the prerequisites for this wizard and also includes a step that indicates when you should run it. We recommend you run this wizard as instructed in the default task list.

The following table summarizes the configurations made by the wizard.

| Configuration | Action | Description |
| --- | --- | --- |
| Location types | Create | Location types are used as filtering options to control the different warehouse management processes. The wizard will create several location types using the names you specify. After running the wizard, you can add, remove, and/or edit these and other location types by going to **Warehouse management \> Setup \> Warehouse \> Location types**. |
| Location profiles | Create | Location profiles are used to control the behavior of locations in an advanced warehouse management enabled warehouse. The wizard will create several location profiles using the names you specify. Each created profile will have a collection of default settings that you may want to customize after completing the wizard. After running the wizard, you can add, remove, and/or edit these and other location profiles by going to **Warehouse management \> Setup \> Warehouse \> Location profiles**. |
| Location formats | Create | Location formats are a naming system used to create unique and consistent names for the different location bin positions used within a warehouse. It can be useful to use separators as part of the location format to make it easier to identify components of the location such as the aisle number. You can set the wizard to create a separate format for each location profile it creates, or create a single format to be shared by all the created profiles. After running the wizard, you can add, remove, and/or edit these and other location formats by going to **Warehouse management \> Setup \> Warehouse \> Location formats**. |
| Inventory status | Create | Inventory statuses are used to categorize and keep track of inventory. The wizard will create an initial inventory status value using the name you specify. After running the wizard, you can add, remove, and/or edit this and other inventory statuses by going to **Warehouse management \> Setup \> Inventory \> Inventory statuses**. |
| Default work user and password | Create | Default work user is used for automated work transactions. The wizard will create an initial work user using the user name and password you specify.  After running the wizard, you can add, remove, and/or edit this and other work users by going to **Warehouse management \> Setup \> Worker**. |
| Load posting methods | Regenerate | Load posting methods are used when a load is released to the warehouse from the load planning workbench. The wizard will generate or regenerate the load posting methods. After running the wizard, you can manually regenerate and/or edit the methods list by going to **Warehouse management \> Setup \> Load posting methods**. |
| Wave processing methods | Regenerate | Wave processing methods are used to perform the actions that are created by a wave template. The wizard will generate or regenerate the wave processing methods. After running the wizard, you can manually regenerate and/or edit the methods list by going to  **Warehouse management \> Setup \> Waves \> Wave process methods**. |
| Warehouse management parameters | Set up | The wizard will initialize several settings on the **Warehouse management parameters** page based on the settings you make while running the wizard. To open this page, go to **Warehouse management \> Setup \> Warehouse management parameters**. The following values will be set: <ul><li>**User location profile**</li><li>**Location types**</li><li>**Default work user ID**</li><li>**Default inventory status**</li></ul> |

Follow these steps to launch and complete the warehouse management initiation wizard:

1. Before launching the wizard, make sure the following prerequisite is in place (it should be if you are running this wizard when instructed to in the default task list described previously in this article):
    - The user account you are using to sign in to Supply Chain Management must be associated with a person record (person records are used by the Human resources module to manage employees). You can set this up by going to **System administration \> Users \> Users**, opening your user account in the list, and linking it to the right person record using the **Person** field. The wizard will add this person as a warehouse worker (on the **Warehouse management \> Setup \> Worker** page) and add the default work user ID you specify in the wizard to that warehouse worker record (see also [Mobile device user accounts](mobile-device-work-users.md)). The system uses the default work user ID when executing some automated processes.
1. Go to **Warehouse management \> Setup \> Wizards \> Warehouse management initiation wizard**.
1. The **Warehouse management initiation wizard** opens, showing the **Welcome** page, which summarizes what the wizard will do. When you're done reading the summary, select **Next** to continue.
1. The **Initialize base data** page opens. Use the settings here to establish initial values for the Warehouse management module. Default values are suggested, but you can edit any of them as needed. If you leave any field blank, then the wizard won't initialize that setting. Make the following settings:

    - **Receiving** – Define the name for the receiving location type and location profile.
    - **Staging** – Define the name for the staging location type and location profile. The specified staging location type will also be identified as such on the **Warehouse management parameters** page.
    - **Packing** – Define the name for the packing location type and location profile. The specified packing location type will also be identified as such on the **Warehouse management parameters** page.
    - **Final shipping** – Define the name for the final shipping location type and location profile. The specified final shipping location type will also be identified as such on the **Warehouse management parameters** page.
    - **Sorting** – Define the name for the sorting location type and location profile. The specified sorting location type will also be identified as such on the **Warehouse management parameters** page.
    - **User** – Define the name for the user location type and location profile. The specified user location profile will also be identified as such on the **Warehouse management parameters** page.
    - **Create one generic format instead of each profile** – Set this option to *No* to create separate location formats for each location profile (each format will be named based on the values you specified in the **Receiving**, **Staging**, **Packing**, **Final shipping**, **Sorting**, and **User** fields ). Set this option to *Yes* to create just one location format (using the name you specify in the **Location format** field), which will apply to all the created location profiles.
    - **Location format** – If **Create one generic format instead of each profile** is set to *Yes*, then enter the name for the shared location format.
    - **Default inventory status ID** – Define the name for the default inventory status. The specified default inventory status ID will also be identified as such on the **Warehouse management parameters** page.
    - **Default work user ID** – Define the name for the default work user. The specified default user ID will also be identified as such on the **Warehouse management parameters** page.
    - **Default work user password** – Define the password for default work user.

1. Select **Next** to continue to the **Base data setup complete** page. This page summarizes the settings the wizard will make based on your input.
1. Select **Finish** to apply the listed settings.

## Warehouse initiation wizard

The **Warehouse initiation wizard** provides a step-by-step guide that will help you set one or more individual warehouses. After completing this wizard, settings will be in place that will allow you to successfully ship sales and receive purchases. Use this wizard for new legal entities or new warehouses where you need to configure basic inbound and outbound flows. The default task list (described previously in this article) includes steps for setting up the prerequisites for this wizard and also includes a step that indicates when you should run it. We recommend you run this wizard as instructed in the default task list.

The following table summarizes the configurations made by the wizard.

| Configuration | Action | Description |
| --- | --- | --- |
| Locations | Create | Locations are used to determine where items are stored and where items are picked from and put to in warehouse. The wizard will create several locations using the names you specify and associated each of them with the warehouses you select at the start of the wizard. After running the wizard, you can add, remove, and/or edit these and other locations by going to **Warehouse management \> Setup \> Warehouse \> Locations**. |
| Directive codes | Create | Directive codes are used as a link between the work templates and the location directives. The wizard will create several directive codes using the names you specify. After running the wizard, you can add, remove, and/or edit these and other directive codes by going to **Warehouse management \> Setup \> Directive codes**. |
| Work classes | Create | Work classes are used to direct and/or limit the type of work order lines that a warehouse worker can process on a mobile device. The wizard will create several work classes using the names you specify. After running the wizard, you can add, remove, and/or edit these and other work classes by going to **Warehouse management \> Setup \> Work \> Work classes**. |
| Location directives | Create | Location directive are used identify pick and put locations for inventory movement. The wizard will create several location directives using names based on the names you specify. Each created location directive name will be prefixed with the name of one of the warehouses you selected at the start of the wizard. Only location directives with a work order type of *Sales orders* or *Purchase orders* will be created. After running the wizard, you can add, remove, and/or edit these and other location directives by going to **Warehouse management \> Setup \> Location directives**. For more information, see [Work with location directives](create-location-directive.md)|
| Wave templates | Create | Wave templates are used to define the wave execution process and setup criteria for when waves are created, executed, and released. The wizard will create several wave templates using names based on the names you specify. Each created wave template name will be prefixed with the name of the warehouse(s) you selected at the start of the wizard, and will also be associated with the named warehouse in the template's settings. Only wave templates with wave template type *Shipping* will be created. After running the wizard, you can add, remove, and/or edit these and other wave templates by going to **Warehouse management \> Setup \> Waves \> Wave templates**. |
| Work templates | Create | Work templates are used to  create warehouse work at various points in the system. The wizard will create several work templates using using names based on the names you specify. Each created work template name will be prefixed with the name of one of the warehouses you selected at the start of the wizard. Only work templates with a work order type of *Sales orders* or *Purchase orders* will be created. After running the wizard, you can add, remove, and/or edit these and other work templates by going to **Warehouse management \> Setup \> Work \> Work templates**. |

Follow these steps to launch and complete the warehouse initiation wizard:

1. Before launching the wizard, make sure the following prerequisites are in place (they should be if you are running this wizard when instructed to in the default task list described previously in this article):
    - Your basic configuration must be set up on the **Warehouse management parameters** page. You could do this by running the **Warehouse management initiation wizard**, as described in the previous section, or you could do it manually by going to **Warehouse management \> Setup \> Warehouse management parameters**.
    - The warehouses that you want to set up using this wizard must already exist as records in the system, and each must have **Use warehouse management processes** set to *Yes*. Each warehouse must also be assigned to a site that exists as a record in the system. You can create sites by going to **Warehouse management \> Setup \> Warehouse \> Sites**. You can create warehouses and make this setting for each of them by going to **Warehouse management \> Setup \> Warehouse \> Warehouses**.
1. Go to **Warehouse management \> Setup \> Wizards \> Warehouse initiation wizard**.
1. The **Warehouse initiation wizard** opens, showing the **Welcome** page, which summarizes what the wizard will do. When you're done reading the summary, select **Next** to continue.
1. The **Warehouses selection** page opens. This page lists the warehouses currently available in the system for the currently selected legal entity. Only warehouses that have **Use warehouse management processes** set to *Yes* are listed. Select the check box for each warehouse that you want to set up using the wizard.
1. Select **Next** to continue to the **General warehouse setup** page. Use the settings here to define names for purchase and sales processes. Default values are suggested, but you can edit any of them as needed. Make the following settings:

    - **Purchase work class** – Define the name of the work class for the receiving process. This value will be used in the work template.
    - **Purchase work template** – Define the name of the work template for the receiving process.  
    - **Sales work template** – Define the name of the work template for the shipping process.
    - **Shipping wave template** – Define the name of the wave template for the shipping process.
    - **Sales pick location directive** – Define the name of the pick location directive for the shipping process.
    - **Purchase put location directive** – Define the name of the put location directive for the receiving process.

1. Select **Next** to continue to the **Staging area setup** page. Use the settings here to define whether you will use a staging area in your outbound processes and, if so, set up this feature. You might need to use it if you pick your items and then place them in a staging location where all lines of a order are held. In this area, items can be packed, relabeled, or loaded onto a delivery truck, and then sent out the door. Default values are suggested, but you can edit any of them as needed. Make the following settings:

    - **Use staging area** – Select this check box if you will use a staging area. If you clear this check box, no staging area will be set up and all of the other settings on this page will be disabled.
    - **Location** – Define the name of the staging location.
    - **Directive code** – Define the name of the directive code for the shipping process. This value will be used in the shipping work template and location directive to link them together.
    - **Sales work class** – Define the name of the work class for the shipping process. This value will be used in the work template.
    - **Sales put location directive** – Define the name of the put location directive for the shipping process.

1. Select **Next** to continue to the **Final shipping area setup** page. Use the settings here to define the names for the final shipping area in the outbound processes. Default values are suggested, but you can edit any of them as needed. Make the following settings:

    - **Location** – Define the name of final shipping location
    - **Directive code** – Define the name of the directive code for the shipping process. This value will be used in the shipping work template and location directive to link them together.
    - **Sales work class** – Define the name of the work class for the shipping process. This value will be used in the work template.
    - **Sales put location directive** – Define the name of the put location directive for the shipping process.

1. Select **Next** to continue to the **Warehouse setup complete** page, which summarizes the actions the wizard will take. Review the summary and, if it looks right, select **Finish** to apply the settings and close the wizard.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
