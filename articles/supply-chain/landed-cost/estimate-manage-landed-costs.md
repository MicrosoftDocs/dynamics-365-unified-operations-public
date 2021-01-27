---
# Delivery information setup

title: Estimate and manage landed costs
description: The system uses your auto cost setup to determine an estimate for your landed cost and you can also specify various scenarios to deliver a more accurate estimate. These are stored so you can later review and compare them to actuals within a report. Furthermore, you are also able to update the item price.
author: RichardLuan
manager: tfehr
ms.date: 01/26/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: [Operations AOT form name to tie this topic to]
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: riluan
ms.search.validFrom: 2021-01-26
ms.dyn365.ops.version: Release 10.0.17
---

# Estimate and manage landed costs

[!include [banner](../includes/banner.md)]

The system uses your [auto cost setup](auto-cost-setup.md) to determine an estimate for your landed cost and you can also specify various scenarios to deliver a more accurate estimate. These are stored so you can later review and compare them to actuals within a report. Furthermore, you are also able to update the item price.

## Set up cost estimates

### Set up cost templates

Cost templates establish default settings that users getting the estimate may not necessarily know. Templates can help reduce complexity in the estimating process by minimizing the selections that users need to specify to get an accurate estimate. <!-- KFM: Add a few words about how/where the templates are used (eg, when setting up a new voyage or journey) -->

To set up your cost templates, go to **Landed cost \> Costing setup \> Cost templates**. This page includes a list pane that lists current cost templates and provides Action Pane actions to create, delete, and edit listed templates. The following table describes the settings available for each template.

| Setting | Description |
| --- | --- |
| **Cost template** | Enter a unique name for the cost template. It typically describes the factor or cost multiplier for the template. |
| **Description** | Enter a description of the cost template. |
| **Shipping company** | Select the shipping company to be applied when this template is used. |
| **Mode of delivery** | Select the mode of delivery, such as sea or air, to be applied when this template is used. This will assist in determining the auto costs associated to the goods on the cost estimate. |
| **Shipping container type** | Select the shipping container type to be applied when this template is used. This will assist in determining which auto costs are associated to the goods during a cost estimate. |
| **Customs broker** | The customs broker (vendor) to be applied when this template is used. This will assist in determining which auto costs are associated to the cost estimate. |
| **Factor** | Enter a multiplier (in percent) to automatically to the cost estimate when this template is used. For example, if you would like to add 10% to the calculated cost estimate, enter a value of *1.10* here. |

### Create a cost estimate

Use the **Cost estimate** dialog box to generate a new cost estimate based on a selected cost template, set of items, and other details of a journey. These settings are then used to determine the estimated landed costs of goods. These cost estimates are primarily used when working with standard cost items. By adding in the estimate landed costs to the standard cost of goods in inventory, you should experience smaller variance transactions when the goods are added to a voyage, as the standard cost will reflect the estimates of such landed costs.

To open the **Cost estimate** dialog box, go to **Landed cost \> Periodic tasks \> Cost estimate**. Then make the settings described in the following subsections and finally select **OK** to create the estimate. The **Cost estimate** page (**Landed cost \> Inquiries \> Cost estimates**) then opens showing your new estimate, as described later in this topic.

### The Parameters tab

Make the following settings on the **Parameters** tab of the **Cost estimate** dialog box.

| Setting | Description |
| --- | --- |
| **Cost template** | Select a cost template. The settings associated with your selected template will be used to identify the auto costs to apply. |
| **Estimate date** | This is set to today's date by default, but you can change it if needed. The date specified will be used to select the appropriate sales prices, purchase prices, auto costs and exchange rate (where shipping rate is used). |
| **Measurement** | If the cost depends on a measurement (such as when using air freight, where volumetric pricing may apply) then enter the value of that measurement. Otherwise, we recommend that set this to 1 unless you are certain that no apportionment occurs using measurement. <!-- KFM:  What about the unit? As defined on auto cost? --> |
| **Journey template** | Select a [journey template](multi-leg-journey-setup.md). This selection is used to locate the correct auto costs to apply. |
| **From port** | Shows the port that the items will be shipped from. This is populated based on the selected journey template. |
| **To port** | Shows the port that the items will be shipped to. This is populated based on the selected journey template. |
| **Currency** | Select the currency that the items will be purchased in. |
| **Containers** | If multiple containers are normally used, then specify the number of containers. The system will then use costs for multiple containers while estimating the costs. |
| **Folios** | If multiple folios are normally used, then specify the quantity (this is normally 1). |
| **Site** | Specify the site where the goods will be delivered. |

### Items tab

The **Items** tab lets you add as many items as needed to the estimate. Use the toolbar to add and remove items in the grid. Select **Inventory \> Display dimensions** on the toolbar to open a dialog box where you can add or remove dimension columns in the grid. The following table describes the settings available for each item.

| Setting | Description |
| --- | --- |
| **Item number** | Select the item you wish to determine the price for. (If the item doesn't yet exist in your system, create a dummy item, optionally attach it to a voyage item cost group, and either leave the price blank or create/change the price.) |
| **Vendor account** | Select the vendor to use for the estimate of this item. (If the item has a default vendor assigned, this will be populated automatically.) |
| **Quantity** | Select the quantity that you will purchase. |
| **Cost price** | The system finds an initial price using its pricing rules, but you can override if necessary. |
| **Sales price** | <!-- KFM: Description needed --> |
| **Measurement** | <!-- KFM: Description needed --> |
| **Update item weight/volume** | <!-- KFM: Description needed --> |
| (Other dimensions) | Depending on which dimensions you have chosen to display, you may see additional columns of information about each item. |

To view or adjust volume an/or weight details for an item, select the item in the grid and then use the fields at the bottom of the page.

## Manage estimate costs

To view and edit the cost estimates you have created, go to **Landed cost \> Inquiries \> Cost estimates**. This page includes a list pane that lists current cost estimates and provides Action Pane actions to work with the selected estimate. Note that you can't create a new cost estimate from this Action Pane (instead, go to **Landed cost \> Periodic tasks \> Cost estimate**, as described previously in this topic).

The **Cost estimates** page shows how each estimated cost was derived and the estimated landed cost for each item. You can modify a cost estimate by changing the cost price and/or currency associated with the various goods. You can also modify the associated voyage costs at both the voyage and container level. When you modify the costs using this page, you will be asked to recalculate the estimate costs for the items within the cost estimate. When you're ready, you can choose to use the estimates to update the cost price of the items within the cost template.

### Information in the header

At the top of the **Cost estimates** page you can see the settings used to generate the selected cost estimate, as described in the previous section. 

### The Lines FastTab

The **Lines** FastTab lists each item included in the current estimate. The following table describes the settings available for each row here.

| Setting | Description |
| --- | --- |
| **Vendor Account** | The vendor account associated with the item. |
| **Item Number** | The item number. |
| **Site** | The site is shown here. <!-- KFM: I don't see this. Removed? --> |
| **Quantity** | The number of items used to determine the cost. |
| **Cost Price** | The cost price (according to the trade agreement) shown in local currency. |
| **Measurement** | The individual measurement is shown here.<!-- KFM:  What about the unit? As defined on auto cost? --> |
| **Estimated landed cost** | The estimated landed cost for the total quantity. |
| **Per unit** | The estimated landed cost divided by the quantity. |
| (Other dimensions) | Depending on which dimensions you have chosen to display, you may see additional columns of information about each item. |

The following table describes the commands available on the **Lines** FastTab toolbar.

| Action | Description |
| --- | --- |
| **Add** | Add items to the cost estimate. You must select **Recalculate** from the Action Pane after making changes to this value. |
| **Remove** | Remove items from the cost estimate. You must select **Recalculate** from the Action Pane after making changes to this value. |
| **Voyage costs** | Opens a page where you can view and edit various types of voyage costs for the item. |
| **Inventory \> Display dimensions** | Select this command to open a dialog box where you can add or remove dimension columns shown in the grid. |

### The General FastTab

The **General** FastTab shows details about the item currently selected on the **Lines** FastTab. Much of this information is repeated from the Lines FastTab and can be edited at either location. However, additional details are also available here. <!-- KFM: The original was very out of date, so I added this. Please confirm. More to say? -->

### The Dimension FastTab

The **Dimension** FastTab shows values for all available inventory dimensions for the item selected on the **Lines** FastTab, regardless of which dimensions you have chosen to display there. <!-- KFM: I added this. Please confirm. More to say? -->

### Commands on the Action Pane

The **Cost estimates** page includes an Action Pane with commands for working with the selected cost estimate. The following table describes each available action.

| Action | Description |
| --- | --- |
| **Cost Inquiry** | View all costs for the shipment. Cost can be viewed at the individual item level if required. <!-- KFM: Do we mean "shipment". How can I view them at the individual item level? --> |
| **Update standard cost** | Updates the standard cost using the default costing version defined on the shipment parameters <!-- KFM: Where is this setting? -->. It is possible to override this version <!-- KFM: How? -->.<br><br>**Note**: If an item has many <!-- KFM: How many? --> item dimensions (such as various sizes, colors, configurations, and so on) and these have not been selected for the estimate, the system will create a pending price for each combination.<br><br>**Important**: The price breakdown is created. This is used to determine the standard cost variance per landed cost.<!-- KFM: This isn't clear to me. What is a price breakdown? --> |
| **Voyage costs** | View and edit voyage costs for all goods within the shipment. |
| **Recalculate** | When voyage costs are updated, added, or removed, select this button to update the estimated landed costs. |
| **Lock** | Lock the cost estimate record so that no further changes can be made. |

## Item cost price update

The Item **Item cost price update** periodic task updates all cost estimates that match the filters you set when running the task. The effect is similar to when you select **Recalculate** from the Action Pane for a single estimate, but in this case it applies to all matching estimates. <!-- KFM: I wrote this. Please confirm. -->

To run the task:

1. Go to **Landed cost \> Periodic tasks \> Item cost price update**.
1. The update cost price from estimate dialog box opens. Set the following options as needed to limit the scope of the update:
    - **Version** - Only update estimates that use this costing version.
    - **Site** - Only update estimates that use this site.
    - **Cost template** - Only update estimates that use this template.
    - **To port** - Only update estimates that use this to port.
    - **Estimate date** - Only update estimates that have this date.
1. Set the **Records to include** and **Run in the background** options as usual for periodic tasks.
1. Select **OK** to run the task.

> [!NOTE]
> The following information must be populated for this periodic task to run:
>
> - Released Products \> Gross depth
> - Released Products \> Gross width
> - Released Products \> Gross height
> - Released Products \> Default vendor
> - Vendor \> From port
