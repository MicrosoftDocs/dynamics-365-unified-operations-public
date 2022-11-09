---
title: Get started with setting up Warehouse management module
description: This article provides an overview of features that will help you set up and configure the Warehouse management module quickly and efficiently.
author: gfedorova
ms.author: gfedorova 
ms.reviewer: kmaybac
ms.search.form: WHSWarehouseInitiationWizard, WHSManagementInitiationWizard
ms.service: dynamics-365
ms.topic: how-to
ms.date: 11/09/2022
ms.custom: bap-template
---

# Get started with setting up Warehouse management module

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../includes/preview-banner.md)]

This article provides an overview of features that will help you set up and configure the Warehouse management module quickly and efficiently.

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

<!--KFM: Explain the toolbar buttons and describe the creation dialog box. -->

### Work with the task list

You can see all remaining tasks in the **Summary** section in addition to a completed vs remaining chart that helps you track and manage the amount of work remaining to implement warehousing module.

In the **Tasks and status** section, you can see the full task list and can be filtered so that it shows only the tasks that you're interested in. You can filter the task list in several ways. For example, you can filter by task category, descriptions. You can also select to show or hide completed tasks in the task list.

The task name is a hyperlink to the page where the user must go to complete the work. You can set this hyperlink by using the **Task link** field when you edit or create a task.

The **Completed by** option will be automatically filled after the task is completed with the name of the worker who completed the task. When a task is marked as completed, the **Completed date** field is automatically updated to the current date and time.

## Initiate the Warehouse management module

The **Warehouse management initiation wizard** provides a step-by-step guide that will help you make the most basic settings required by the Warehouse management module. 

The following table summarizes the configurations made by the wizard.

| Configuration | Action | Description |
| --- | --- | --- |
| Location types | Create | Location types are used as filtering options to control the different warehouse management processes. The wizard will create several location types using the names you specify. After running the wizard, you can add, remove, and/or edit these and other location types by going to **Warehouse management \> Setup \> Warehouse \> Location types**. |
| Location profiles | Create | The wizard will create several location profiles using the names you specify. <!--KFM: Where do the various options come from for each created profile? --> After running the wizard, you can add, remove, and/or edit these and other location profiles by going to **Warehouse management \> Setup \> Warehouse \> Location profiles**. |
| Location formats | Create | Location formats are a naming system used to create unique and consistent names for the different location bin positions used within a warehouse. It can be useful to use separators as part of the location format to make it easier to identify components of the location such as the aisle number. The wizard will create an initial location format using the name you specify. You can tell the wizard to create separate location formats for each profile or to create one location format for each profile <!-- KFM: These options both seem the same(?) I think we should clarify. -->. After running the wizard, you can add, remove, and/or edit these and other location formats by going to **Warehouse management \> Setup \> Warehouse \> Location formats**. |
| Inventory status | Create | <!-- KFM: What are these and how do we use them? --> The wizard will create an initial inventory status value using the name you specify. After running the wizard, you can add, remove, and/or edit this and other inventory statuses by going to **Warehouse management \> Setup \> Inventory \> Inventory statuses**. |
| Default work user and password | Create | The wizard will create an initial work user using the user name and password you specify.  After running the wizard, you can add, remove, and/or edit this and other work users by going to **Warehouse management \> Setup \> Worker**. |
| Load posting methods | Regenerate | <!-- KFM: What are these and how do we use them? --> The wizard will generate or regenerate the load posting methods. After running the wizard, you can manually regenerate and/or edit the methods list by going to **Warehouse management \> Setup \> Load posting methods**. |
| Wave processing methods | Regenerate | <!-- KFM: What are these and how do we use them? --> The wizard will generate or regenerate the wave processing methods. After running the wizard, you can manually regenerate and/or edit the methods list by going to  **Warehouse management \> Setup \> Waves \> Wave process methods**. |
| Warehouse management parameters | Set up | The wizard will initialize several settings on the **Warehouse management parameters** page based on the settings you make while running the wizard. To open this page, go to **Warehouse management \> Setup \> Warehouse management parameters**. The following values will be set: <ul><li>**User location profile**</li><li>**Location types**</li><li>**Default work user ID**</li><li>**Default inventory status**</li></ul> |

Follow these steps to launch and complete the wizard:

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
1. **Note:** Your user must be associated with the employee record in order to successfully create work user. <!--KFM: Describe how to do this here. -->


## Warehouse initiation wizard

The Warehouse initiation wizard is used to complete warehouse purchase and sales processes with step-by-step guides.

For warehouse management initiation wizard, go to **Warehouse management \> Setup \> Wizards \> Warehouse initiation wizard**.

On the **Welcome** page of the wizard, you will be able to see the wizard description.

The next page in the wizard is the **Warehouse selection** page. On this page, select the warehouse that you will be setting up processes for. Only warehouses that have "Use warehouse management processes" parameter enabled, will be displayed.

The next page in the wizard is the **General warehouse setup** page. It's used to define the names for the configuration of the purchase and sales processes. On this page, default recommendations are suggested with the possibility to override those values. On the **Staging area setup** page of the wizard, define whether you need the staging area in the outbound processes. On the **Final shipping area setup** page of the wizard, define the names for the final shipping area configuration in the outbound processes. On the **Warehouse setup complete** page of the wizard, you will be able to see the summary of the future changes.

After this wizard execution, you will be able to successfully execute sales shipment and purchase receive basic processes. The wizard will automate the following:

| Configuration | Action | Description |
| --- | --- | --- |
| Locations | Create | Locations defined in the wizard will be automatically created. Created locations can be found here: **Warehouse management \> Setup \> Warehouse \> Locations**. |
| Directive codes | Create | Directive codes defined in the wizard will be automatically created. Created directive codes can be found here: **Warehouse management \> Setup \> Directive codes**. |
| Work classes | Create | Work classes defined in the wizard will be automatically created. Created work classes can be found here: **Warehouse management \> Setup \> Work \> Work classes**. |
| Location directives | Create | Location directives defined in the wizard will be automatically created. Created location directives can be found here: **Warehouse management \> Setup \> Location directives**. **Note** : Only location directives with work order types Sales orders and Purchase orders will be created. |
| Wave templates | Create | Wave templates defined in the wizard will be automatically created. Created wave templates can be found here: **Warehouse management \> Setup \> Waves \> Wave templates**. **Note** : Only wave templates with wave template type Shipping will be created. |
| Work templates | Create | Work templates defined in the wizard will be automatically created. Created work templates can be found here: **Warehouse management \> Setup \> Work \> Work template**. **Note** : Only location directives with work order types Sales orders and Purchase orders will be created. |

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
