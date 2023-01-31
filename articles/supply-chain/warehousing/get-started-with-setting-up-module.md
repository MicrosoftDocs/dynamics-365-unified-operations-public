---
title: Get started with setting up the Warehouse management module
description: This article explains how to work with the built-in wizards and checklists that will help you quickly and efficiently set up and configure the Warehouse management module.
author: GalynaFedorova
ms.author: gfedorova 
ms.reviewer: kmaybac
ms.search.form: WHSWarehouseInitiationWizard, WHSManagementInitiationWizard, WHSImplementationWorkspace, WHSImplementationTaskListPage
ms.topic: how-to
ms.date: 11/09/2022
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Get started with setting up the Warehouse management module

[!include [banner](../includes/banner.md)]

This article explains how to work with the built-in wizards and checklists that will help you quickly and efficiently set up and configure the **Warehouse management** module.

## Track the Warehouse management configuration processes

Use the **Warehouse implementation tasks** workspace to track your Warehouse management configuration processes. The workspace can be used during a new implementation, after an upgrade, or after a migration.

The workspace lets you create, edit, and import checklists that you can use to identify important implementation tasks and track your progress while you complete them. It lets you perform the following actions:

- Track progress by viewing all current and closed configuration tasks.
- Select hyperlinks to quickly access the configuration page that's required for each step.
- Import a default configuration checklist that includes the tasks that you must complete to get a warehouse up and running.

### Open the Warehouse implementation tasks workspace

To open the workspace, go to **Warehouse management \> Workspaces \> Warehouse implementation tasks**.

### Import the default configuration task list

Microsoft Dynamics 365 Supply Chain Management includes a default task list. This task list is a good place to start when you're planning and implementing your Warehouse management setup. Follow these steps to import it into the **Warehouse implementation tasks** workspace.

1. In the **Warehouse implementation tasks** workspace, on the **Tasks and status** FastTab, select **Import default tasks** on the toolbar.

    The default tasks should be loaded. However, you might receive the following error instead: "Entity Warehouse implementation tasks not found. Refresh entity list from Data import/export framework parameters form." In that case, follow these steps:

    1. Go to **System administration \> Workspaces \> Data management**.
    1. Select the **Framework parameters** tile.
    1. On the **Entity settings** tab, select **Refresh entity list**.

        The system adds a refresh entity job to your batch job queue and will run it as soon as it can. You might have to wait several minutes for the task to be completed, depending on the number of other jobs in the queue.

    1. When the refresh entity job is completed, return to the **Warehouse implementation tasks** page, and select **Import default tasks** again on the toolbar of the **Tasks and status** FastTab.

### Customize the task list

After you import a task list, you can customize it as you require by adding, removing, and rearranging the tasks. You can also create a fully customized task list by starting from scratch. Use the following buttons on the toolbar of the **Tasks and status** FastTab in the **Warehouse implementation tasks** workspace to customize the list:

- **Add task** – Create a new task. This button opens the **Add task** dialog box, where you must set the following fields:

    - **Task category** – Enter the type of task.
    - **Description** – Enter a detailed description of what the user should do to complete the task.
    - **Task link** – Select the page in Supply Chain Management where the user should go to complete the task.

- **Edit task** – Edit a selected task. This button opens the **Edit task** dialog box, where you can edit the **Description** and **Task link** fields for the task. Other settings are read-only for existing tasks.
- **Remove** – Delete all selected tasks. You will be prompted to confirm the operation.
- **Move up** – Move a selected task up in the sequence order.
- **Move down** – Move a selected task down in the sequence order.

### Work with the task list

When your task list is ready, follow these steps to work through it.

1. In the **Warehouse implementation tasks** workspace, select the **Summary** FastTab for an overview of the total number of tasks and the proportion of them that have been marked as completed.
1. Select the **Tasks and status** FastTab to view the full list and mark tasks as completed while you work.

    For each task, the following information is shown:

    - **Sequence number** – The order that you should complete the task in. Start with the task that has the lowest number, and work upward.
    - **Completed** – Select this checkbox for each task as you complete it.
    - **Task category** – The type of task. Select the text to open a page where you can configure the settings that are required to complete the task.
    - **Description** – Full details about what must be done to complete the task.
    - **Status** – A check mark indicates that the task has been completed.
    - **Completed by** – If the task has been completed, the name of the user who completed it.
    - **Completed date** – If the task has been completed, the date when it was completed.

    Use the following fields and buttons on the toolbar of the **Tasks and status** FastTab to find your way around the task list:

    - **Filter** – To quickly find a specific task in a long list, enter a value here, and then select the column where that value should be found.
    - **Hide completed tasks** or **Show completed tasks** – Select whether to hide or show tasks that have already been completed. The button label changes, depending on whether completed tasks are currently shown or hidden.

    To view the full task list (including both completed and non-completed tasks), on the **Links** FastTab, select the **All tasks** link. The page that appears is the same page that appears when you select the **Warehouse implementation tasks** tile on the **Summary** FastTab. It provides the same information as, and works like, the **Task list** FastTab on the **Warehouse implementation tasks** page.

1. Continue to work until all tasks are completed.

## Warehouse management initiation wizard

The **Warehouse management initiation** wizard provides a step-by-step guide that will help you configure the most basic settings that the **Warehouse management** module requires. Use this wizard for new legal entities where you must configure the **Warehouse management** module from scratch. The wizard will define the main settings of Warehouse management parameters for you. The default task list that was described earlier in this article includes steps for setting up the prerequisites for this wizard. It also includes a step that indicates when you should run this wizard. We recommend that you run the wizard when you're instructed to do so in the default task list.

The following table summarizes the configurations that the wizard does.

| Configuration | Action | Description |
| --- | --- | --- |
| Location types | Create | <p>Location types are used as filtering options to control the different warehouse management processes. The wizard will create several location types and use the names that you specify.</p><p>After you complete the wizard, you can add, remove, and/or edit these and other location types by going to **Warehouse management \> Setup \> Warehouse \> Location types**.</p> |
| Location profiles | Create | <p>Location profiles are used to control the behavior of locations in a warehouse that's enabled for advanced warehouse management. The wizard will create several location profiles and use the names that you specify. Each profile will have a collection of default settings that you might want to customize after you complete the wizard.</p><p>After you complete the wizard, you can add, remove, and/or edit these and other location profiles by going to **Warehouse management \> Setup \> Warehouse \> Location profiles**.</p> |
| Location formats | Create | <p>Location formats are a naming system that's used to create unique and consistent names for the different location bin positions that are used in a warehouse. To make the components of the location, such as the aisle number, easier to identify, you might want to include separators as part of the location format.</p><p>You can set the wizard to create a separate format for each location profile that it creates. Alternatively, the wizard can create a single format that will be shared by all the profiles that it creates.</p><p>After you complete the wizard, you can add, remove, and/or edit these and other location formats by going to **Warehouse management \> Setup \> Warehouse \> Location formats**.</p> |
| Inventory status | Create | <p>Inventory statuses are used to categorize and keep track of inventory. The wizard will create an initial inventory status value and use the name that you specify.</p><p>After you complete the wizard, you can add, remove, and/or edit this and other inventory statuses by going to **Warehouse management \> Setup \> Inventory \> Inventory statuses**.</p> |
| Default work user and password | Create | <p>The default work user is used for automated work transactions. The wizard will create an initial work user and use the user name and password that you specify.</p><p>After you complete the wizard, you can add, remove, and/or edit this and other work users by going to **Warehouse management \> Setup \> Worker**.</p> |
| Load posting methods | Regenerate | <p>Load posting methods are used when a load is released to the warehouse from the load planning workbench. The wizard will generate or regenerate the load posting methods.</p><p>After you complete the wizard, you can manually regenerate and/or edit the method list by going to **Warehouse management \> Setup \> Load posting methods**.</p> |
| Wave processing methods | Regenerate | <p>Wave processing methods are used to perform the actions that are created by a wave template. The wizard will generate or regenerate the wave processing methods.</p><p>After you complete the wizard, you can manually regenerate and/or edit the method list by going to **Warehouse management \> Setup \> Waves \> Wave process methods**.</p> |
| Warehouse management parameters | Set up | <p>Based on settings that you specify while you run the wizard, the wizard will initialize several settings on the **Warehouse management parameters** page (**Warehouse management \> Setup \> Warehouse management parameters**). The following values will be set:</p><ul><li>User location profile</li><li>Location types</li><li>Default work user ID</li><li>Default inventory status</li></ul> |

Follow these steps to open and complete the **Warehouse management initiation** wizard.

1. Before you open the wizard, make sure that the following prerequisite is in place. (It should be in place if you run the wizard when you're instructed to do so in the default task list that was described earlier in this article.)

    - The user account that you're using to sign in to Supply Chain Management must be associated with a person record. (Person records are used by the **Human resources** module to manage employees.) To set up this association, go to **System administration \> Users \> Users**, open your user account in the list, and use the **Person** field to link the account to the correct person record. The wizard will add this person as a warehouse worker on the **Worker** page (**Warehouse management \> Setup \> Worker**). It will also add the default work user ID that you specify in the wizard to the warehouse worker record. (For more information, see [Mobile device user accounts](mobile-device-work-users.md).) The system uses the default work user ID when it runs some automated processes.

1. Go to **Warehouse management \> Setup \> Wizards \> Warehouse management initiation wizard**.
1. The first page of the **Warehouse management initiation** wizard is the **Welcome** page. It summarizes what the wizard will do. When you've finished reading the summary, select **Next** to continue.
1. On the **Initialize base data** page, use the following fields to define initial settings for the **Warehouse management** module. Default values are suggested, but you can edit them as you require. If you leave any field blank, the wizard won't initialize the setting.

    - **Receiving** – Specify the name of the receiving location type and location profile.
    - **Staging** – Specify the name of the staging location type and location profile. The specified staging location type will also be identified on the **Warehouse management parameters** page.
    - **Packing** – Specify the name of the packing location type and location profile. The specified packing location type will also be identified on the **Warehouse management parameters** page.
    - **Final shipping** – Specify the name of the final shipping location type and location profile. The specified final shipping location type will also be identified on the **Warehouse management parameters** page.
    - **Sorting** – Specify the name of the sorting location type and location profile. The specified sorting location type will also be identified on the **Warehouse management parameters** page.
    - **User** – Specify the name of the user location type and location profile. The specified user location profile will also be identified on the **Warehouse management parameters** page.
    - **Create one generic format instead of each profile** – Set this option to *No* to create a separate location format for each location profile. The name of each format will be based on the values that you specify in the **Receiving**, **Staging**, **Packing**, **Final shipping**, **Sorting**, and **User** fields. Set this option to *Yes* to create one location format that will apply to all the location profiles that are created. This format will use the name that you specify in the **Location format** field.
    - **Location format** – If the **Create one generic format instead of each profile** option is set to *Yes*, specify the name of the shared location format.
    - **Default inventory status ID** – Specify the name of the default inventory status. The specified default inventory status ID will also be identified on the **Warehouse management parameters** page.
    - **Default work user ID** – Specify the name of the default work user. The specified default user ID will also be identified on the **Warehouse management parameters** page.
    - **Default work user password** – Specify the password of the default work user.

1. Select **Next** to continue.
1. The **Base data setup complete** page summarizes the settings that the wizard will apply, based on your input. Review the summary, and if everything looks correct, select **Finish** to apply the settings and close the wizard.

## Warehouse initiation wizard

The **Warehouse initiation wizard** provides a step-by-step guide that will help you set up one or more individual warehouses. After you complete this wizard, settings will be in place that will let you ship sales and receive purchases. Use this wizard for new legal entities or new warehouses where you must configure basic inbound and outbound flows. The default task list that was described earlier in this article includes steps for setting up the prerequisites for this wizard. It also includes a step that indicates when you should run this wizard. We recommend that you run the wizard when you're instructed to do so in the default task list.

The following table summarizes the configurations that the wizard does.

| Configuration | Action | Description |
| --- | --- | --- |
| Locations | Create | <p>Locations are used to determine where items are stored, picked from, and put to in the warehouse. The wizard will create several locations and use the names that you specify. It will associate each location with the warehouses that you select at the beginning of the wizard.</p><p>After you complete the wizard, you can add, remove, and/or edit these and other locations by going to **Warehouse management \> Setup \> Warehouse \> Locations**.</p> |
| Directive codes | Create | <p>Directive codes are used as a link between the work templates and the location directives. The wizard will create several directive codes and use the names that you specify.</p><p>After you complete the wizard, you can add, remove, and/or edit these and other directive codes by going to **Warehouse management \> Setup \> Directive codes**.</p> |
| Work classes | Create | <p>Work classes are used to direct and/or limit the type of work order lines that a warehouse worker can process on a mobile device. The wizard will create several work classes and use the names that you specify.</p><p>After you complete the wizard, you can add, remove, and/or edit these and other work classes by going to **Warehouse management \> Setup \> Work \> Work classes**.</p> |
| Location directives | Create | <p>Location directives are used to identify pick and put locations for inventory movement. The wizard will create several location directives and name them based on the names that you specify. The name of each location directive that's created will be prefixed with the name of one of the warehouses that you select at the beginning of the wizard. Only location directives that have a work order type of *Sales orders* or *Purchase orders* will be created.</p><p>After you complete the wizard, you can add, remove, and/or edit these and other location directives by going to **Warehouse management \> Setup \> Location directives**.</p><p>For more information, see [Work with location directives](create-location-directive.md).</p> |
| Wave templates | Create | <p>Wave templates are used to define the wave execution process and setup criteria for when waves are created, run, and released. The wizard will create several wave templates and name them based on the names that you specify. The name of each wave template that's created will be prefixed with the name of the warehouses that you select at the beginning of the wizard. Each wave template will also be associated with the named warehouse in the template's settings. Only wave templates that have a wave template type of *Shipping* will be created.</p><p>After you complete the wizard, you can add, remove, and/or edit these and other wave templates by going to **Warehouse management \> Setup \> Waves \> Wave templates**.</p> |
| Work templates | Create | <p>Work templates are used to create warehouse work at various points in the system. The wizard will create several work templates and name them based on the names that you specify. The name of each work template name that's created will be prefixed with the name of one of the warehouses that you select at the beginning of the wizard. Only work templates that have a work order type of *Sales orders* or *Purchase orders* will be created.</p><p>After you complete the wizard, you can add, remove, and/or edit these and other work templates by going to **Warehouse management \> Setup \> Work \> Work templates**.</p> |

Follow these steps to open and complete the **Warehouse initiation** wizard.

1. Before you open the wizard, make sure that the following prerequisites are in place. (They should be in place if you run the wizard when you're instructed to do so in the default task list that was described earlier in this article.)

    - Your basic configuration must be set up on the **Warehouse management parameters** page. You can complete this configuration by running the **Warehouse management initiation** wizard as described in the previous section. Alternatively, you can complete it manually by going to **Warehouse management \> Setup \> Warehouse management parameters**.
    - Each warehouse that you want to set up by using this wizard must already exist as a record in the system, and the **Use warehouse management processes** option must be set to *Yes* for it. You can create warehouses and set the **Use warehouse management processes** option for each of them by going to **Warehouse management \> Setup \> Warehouse \> Warehouses**. Each warehouse must also be assigned to a site that exists as a record in the system. You can create sites by going to **Warehouse management \> Setup \> Warehouse \> Sites**.

1. Go to **Warehouse management \> Setup \> Wizards \> Warehouse initiation wizard**.
1. The first page of the **Warehouse initiation** wizard is the **Welcome** page. It summarizes what the wizard will do. When you've finished reading the summary, select **Next** to continue.
1. The **Warehouses selection** page lists the warehouses that are currently available in the system for the currently selected legal entity. Only warehouses where the **Use warehouse management processes** option is set to *Yes* are listed. Select the checkbox for each warehouse that you want to set up by using the wizard.
1. Select **Next** to continue.
1. On the **General warehouse setup** page, use the following fields to define names for purchase and sales processes. Default values are suggested, but you can edit them as you require.

    - **Purchase work class** – Specify the name of the work class for the receiving process. This value will be used in the work template.
    - **Purchase work template** – Specify the name of the work template for the receiving process.
    - **Sales work template** – Specify the name of the work template for the shipping process.
    - **Shipping wave template** – Specify the name of the wave template for the shipping process.
    - **Sales pick location directive** – Specify the name of the pick location directive for the shipping process.
    - **Purchase put location directive** – Specify the name of the put location directive for the receiving process.

1. Select **Next** to continue.
1. On the **Staging area setup** page, use the following fields to specify whether you will use a staging area in your outbound processes and, if you will, to set up the feature. You might have to use the feature if you pick your items and then put them in a staging location where all lines of an order are held. In the staging area, items can be packed, relabeled, or loaded onto a delivery truck, and then sent out the door. Default values are suggested, but you can edit them as you require.

    - **Use staging area** – Select this checkbox if you will use a staging area. If you clear this checkbox, no staging area will be set up, and all the other fields on the page will be unavailable.
    - **Location** – Specify the name of the staging location.
    - **Directive code** – Specify the name of the directive code for the shipping process. This value will be used in the shipping work template and location directive to link them together.
    - **Sales work class** – Specify the name of the work class for the shipping process. This value will be used in the work template.
    - **Sales put location directive** – Specify the name of the put location directive for the shipping process.

1. Select **Next** to continue.
1. On the **Final shipping area setup** page, use the following fields to define names for the final shipping area in the outbound processes. Default values are suggested, but you can edit them as you require.

    - **Location** – Specify the name of the final shipping location.
    - **Directive code** – Specify the name of the directive code for the shipping process. This value will be used in the shipping work template and location directive to link them together.
    - **Sales work class** – Specify the name of the work class for the shipping process. This value will be used in the work template.
    - **Sales put location directive** – Specify the name of the put location directive for the shipping process.

1. Select **Next** to continue.
1. The **Warehouse setup complete** page summarizes the actions the wizard will take. Review the summary, and if everything looks correct, select **Finish** to apply the settings and close the wizard.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
