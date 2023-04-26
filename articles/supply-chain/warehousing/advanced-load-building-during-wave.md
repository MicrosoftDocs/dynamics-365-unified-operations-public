---
# required metadata

title: Advanced load building during wave
description: This article provides information about advanced wave load building, which automatically assigns shipments to existing waves during wave execution. Therefore, you can create meaningful loads that represent trucks without having to use the load planning workbench.
author: Mirzaab
ms.date: 07/01/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: WHSPostMethod,WHSWaveTemplateTable,WHSLoadMixGroup,WHSLoadBuildTemplate, WHSWaveTableListPage, TMSLoadBuildTemplateApply, TMSLoadBuildTemplates, TMSLoadBuildTemplateCreate
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for articles migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: mirzaab
ms.search.validFrom: 2020-07-01
ms.dyn365.ops.version: 10.0.9
---

# Advanced load building during wave

[!include [banner](../includes/banner.md)]

Advanced wave load building automatically assigns shipments to existing waves during wave execution. Therefore, you can create meaningful loads that represent trucks without having to use the load planning workbench. This capability is useful for businesses that want to use the concept of loads to track and plan the shipment of goods in a truck/trailer, but that don't want to manually create those loads every day.

During wave processing, the system usually creates a new load for each shipment that no load is assigned to. However, when advanced wave load building is turned on, the system assigns each unassigned shipment to an existing load (if an appropriate load exists), and new loads are created only when they are required. Advanced wave load building automatically creates the new loads, based on criteria that you define.

To use the feature, you must set up the system in the following way:

- Create *wave templates* that include the new **buildLoads** method. This method makes advanced wave load building available for waves that use those templates.
- Set up *load build templates*, each of which is linked to a specific wave template and method. Load build templates control which load (existing or new) the load lines that are being waved are added to. You can combine or separate shipments, based on criteria such as the load template, equipment, and other field values on the load line.
- Define *load mix groups* to control which items should and should not be combined on a single load. You also specify whether the restriction should produce a warning or an error, and whether the volumetric restriction of the load template should be evaluated.

## Turn on advanced wave load building in your system

To use advanced wave load building, two features must be turned on for your system. Admins can use the [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) settings to check the status of these features and turn them on if necessary. Both of the following features are required:

- *Wave load building feature* (As of Supply Chain Management version 10.0.32, this feature is mandatory and can't be turned off.)
- *Organization wide wave step code* (As of Supply Chain Management version 10.0.32, this feature is mandatory and can't be turned off.)

### Make sample data available

To work through this demo by using the sample records and values that are specified here, you must be on a system where the standard [demo data](../../fin-ops-core/fin-ops/get-started/demo-data.md) is installed. Additionally, you must select the **USMF** legal entity before you begin.

You can also use this demo as guidance for using this feature when you work on a production system. However, in that case, you must substitute your own values, and you might be missing some types of required records that the standard demo data provides.

### Make sure that the scenario setup includes enough available inventory

If you're working with the **USMF** demo data, you must first make sure that your system is set up so that there is enough inventory at each relevant location. For this demo, the expectation is that the following inventory is available in warehouse *62*:

- **Item A0001:** 10 pcs
- **Item A0002:** 10 pcs
- **Item M9200:** 10 ea

Item **M9200** must be added to the warehouse. Complete the procedures in the following subsections to add the item inventory.

#### Create a new license plate ID

1. Go to **Warehouse management** \> **Setup** \> **Warehouse** \> **License plates**.
1. On the Action Pane, select **New**.
1. In the new row, in the **License plate** field, enter *LP6203*.
1. Select **Save**.

#### Create a standard cost for item M9200 in site 6

1. Go to **Product information management** \> **Products** \> **Released products**.
1. Search on **M9200**.
1. Select the row for the item, and then, on the Action Pane, on the **Manage costs** tab, in the **Set up** group, select **Item price**.
1. On the **Item price** page, select the **Pending prices** tab.
1. On the Action Pane, select **New**.
1. On the new line, set the following values:

    - **Costing type:** *Planned cost*
    - **Price type:** *Cost*
    - **Version:** *10*
    - **Site:** *6*
    - **Price:** *1.60*

1. On the Action Pane, select **Save**.
1. On the Action Pane, select **Activate pending price(s)**.
1. Select the **Active prices** tab to verify that the new cost price for site *6* has been added.

#### Create inventory in warehouse 62

1. Go to **Inventory management** \> **Journal entries** \> **Items** \> **Inventory adjustment**.
1. On the Action Pane, select **New**.
1. In the **Create inventory journal** dialog box, on the **Overview** FastTab, in the **Warehouse** field, enter *62*. Accept the default values in all the other fields.
1. Select **OK** to close the dialog box.
1. The **Inventory adjustment** page is opened. On the **Journal lines** FastTab, select **New** to add a line.
1. On the new line, set the following values. Accept the default values in all the other fields.

    - **Item number:** *M9200*
    - **Location:** *bulk-003*
    - **Quantity:** Change the value to *10*.

1. On the Action Pane, select **Save**.
1. On the Action Pane, select **Validate** to check for errors.
1. In the **Check journal** dialog box, select **OK** to start the check. You receive a message when the check is completed.
1. On the Action Pane, select **Post** to commit the inventory adjustment.
1. In the **Post journal** dialog box, select **OK** to start the posting. You receive a message when the posting is completed.

## Set up advanced wave load building

### Regenerate wave process methods

You might have to regenerate your wave process methods to make the load building method (**buildLoads**) available.

1. Go to **Warehouse management** \> **Setup** \> **Waves** \> **Wave process methods**.
2. Verify that **buildLoads** is present in the list. If it isn't present, select **Regenerate methods** on the Action Pane to add it.

### Set up wave templates

To take advantage of advanced wave load building, you must include the **buildLoads** method in each relevant [wave template](tasks/configure-wave-processing.md).

1. Go to **Warehouse management** \> **Setup** \> **Waves** \> **Wave templates**.
1. Select a wave template.

    If you're working with the **USMF** demo data, select the **62 Shipping Default** template.

1. On the Action Pane, select **Edit** to put the page into edit mode.
1. On the **Methods** FastTab, in the **Remaining methods** grid, select the **buildLoads** method.
1. Select the right arrow button to move the **buildLoads** method to the **Selected methods** grid.
1. To assign a **Wave step code** value for the **buildLoads** method, you must first create a code on the **Wave step codes** page. You can use any value that you want, but be sure to make a note of it, because you will need it later. Follow these steps to create code **WSC2112**:

    1. In the row for the **buildLoads** method, right-click the down arrow in the **Wave step code** field, and then select **View details**.
    1. On the **Wave step codes** page, on the Action Pane, select **New**.
    1. In the **Wave step code** field, enter *WSC2112*.
    1. In the **Wave step description** field, enter *WSC2112*.
    1. In the **Wave step type** field, select *Load Building*.

1. Select **Save**, and close the page.
1. In the row for the **buildLoads** method, in the **Wave step code** field, select the code that you just created (**WSC2112**).
1. On the Action Pane, select **Save**.

> [!NOTE]
> Wave step codes are codes that users can set up and use to link specific instances of wave methods to corresponding templates. The templates include templates for replenishment, containerization, label printing, load building, and sorting.
>
> When wave step codes aren't used, users must enter free text to reference a specific template from the wave method instance. Free text is prone to errors, because users must make sure that the wave step text that they add for a specific wave step method in a wave template exactly matches the wave step text in the target template.
>
> Wave step codes for a specific wave step type are set up on a separate page. For every instance of a wave step method in a wave template that requires a wave step code, the wave step code must be selected in a drop-down list. Selection in a drop-down list replaces free text entry and helps reduce the risk and impact of human error. Setup codes are used to link a wave step method in a wave template to a target template for the method.

### Set up load mix groups

Load mix groups establish rules for the types of items that can be combined on a single load. You can set up as many load mix groups as you require. However, to use advanced wave load building, you must have at least one. Follow these steps to create a load mix group.

1. Go to **Warehouse management** \> **Setup** \> **Load** \> **Load mix groups**.
1. On the Action Pane, select **New** to create a load group.
1. In the **Load mix group ID** field, enter a name for the new group.

    If you're working with the **USMF** demo data, set the following values:

    - **Load mix group ID:** *TV*
    - **Description:** *TV*

1. On the Action Pane, select **Save** to make the **Load mix group criteria** FastTab available.
1. On the **Load mix group criteria** FastTab, select **New** to add a row to the grid.
1. In the new row, set the desired values in each field. These values determine the item groups that are considered for the load mix.

    If you're working with the **USMF** demo data, select *TV&Video* in the **Item group** field.

1. On the Action Pane, select **Save** to make the **Load mix group constraints** FastTab available.
1. On the **Load mix group constraints** FastTab, select **New** to add a row to the grid.
1. In the new row, set the desired values in each field.

    If you're working with the **USMF** demo data, set the following values:

    - **Item group:** *CarAudio*
    - **Load build action:** *Restrict* (This value will prevent items that belong to the **CarAudio** item group from being on the same load as items that belong to the **TV&Video** item group.)

1. Continue to work with the rules until you've added all the criteria and constraints that you require for the load mix group.

If you're working with the **USMF** demo data, you've now finished this setup.

### Set up load build templates

You can set up as many load build templates as you require. However, to use advanced wave load building, you must have at least one. Follow these steps to create a load build template.

1. Go to **Warehouse Management** \> **Setup** \> **Load** \> **Wave load building templates**.
1. On the Action Pane, select **New** to add a row to the grid.
1. In the new row, set the following values.

    | Field | Description | Value in the USMF demo data |
    |---|---|---|
    | Sequence number | The order that the template will be evaluated in. | *1* |
    | Load build template name | Enter the unique identifier of the load build template. You should enter the name of the template that you created or updated earlier in this setup. | *62 Shipping Default* |
    | Wave step code | Enter the wave step code to use to link the template to a wave method. You should enter the code that you selected for the **buildLoads** method when you set up the wave template earlier in this setup. | *WSC2112* |
    | Load template ID | Select the load template to use when new loads are created and to match against when assigning to existing loads. The load template defines the maximum weight and volume that are permitted for the whole load. | *Stnd Load Template* |
    | Equipment | The equipment to match against when assigning to existing loads and to enter on new loads that are created. | Leave this field blank. |
    | Load mix group ID | Select the load mix group to use if the item is allowed on the load. The mix group establishes rules for the types of items that can be combined on a single load. You should select one of the mix groups that you created earlier in this setup. | *TV* |
    | Use open loads | Select whether existing open loads should be added. The following options are available:<ul><li>**None** – Don't add open loads to any existing loads.</li><li>**Any** – Add open loads to any existing loads that are valid for the line.</li><li>**Assigned** – Add open loads to the load that is assigned to the wave.</li></ul> | *Any* |
    | Create loads | Specify whether new loads should be created if no existing loads match the criteria. | Selected (= *Yes*) |
    | Allow shipment line split | Specify whether a single load line can be split across multiple loads if the full line exceeds the maximum capacity of the load template. | Cleared (= *No*) |
    | Validate volumetrics | Specify whether load building should check the weight and volume as each load line is added, to ensure that the volumetric limits of the load template are respected. | Cleared (= *No*) |

1. On the Action Pane, select **Save** to make the **Edit query** option available.
1. On the Action Pane, select **Edit query** to open a dialog box for editing the query.
1. In the dialog box, on the **Sorting** tab, select **Add** to add a row to the grid.
1. In the new row, define the sorting rules that you want to use. For example, set the following values to sort the search results in ascending order by order number:

    - **Table:** *Load details*
    - **Derived table:** *Load details*
    - **Field:** *Order number*
    - **Search direction:** *Ascending*

1. Select **OK** to save your changes and close the dialog box.
1. On the **Break by** FastTab, set rules to control how your loads are split up. Typically, you might break on custom fields that have been extended onto the load line, such as **Route**, **Tour**, or **Run**. For example, to create one load per order number, select the **Break by** check box for the row that has the following values:

    - **Reference table name:** *Load details*
    - **Reference field name:** *Order number*

## Scenario

This scenario shows how the settings that were described earlier in this article affect warehouse operations while a sales order is processed. This scenario uses the **USMF** demo data together with other demo values that are provided in those setup instructions.

### Create sales orders

1. Go to **Sales and marketing** \> **Sales orders** \> **All sales orders**.
1. On the Action Pane, select **New** to open the **Create sales order** dialog box.
1. In the dialog box, set the following values:

    - On the **Customer** FastTab, set the **Customer account** field to *US-007*.
    - On the **General** FastTab, set the **Warehouse** field to *62*.

1. Select **OK** to create the sales order and close the dialog box.
1. Your new sales order is opened. It should include a new, empty line in the grid on the **Sales order lines** FastTab. On this new line, set the **Item number** field to *A0001* and the **Quantity** field to *1*.
1. On the **Inventory** menu above the grid, select **Reservation**.
1. On the **Reservation** page, on the Action Pane, select **Reserve lot**.
1. Select the **Close** button (**X**) in the upper-right corner of the page to return to the sales order.
1. On the Action Pane, on the **Warehouse** tab, in the **Actions** group, select **Release to warehouse**. The system creates a shipment and adds it to a new load, because no existing load contains load lines that have this order number.

    You receive informational messages that indicate the work, wave, and shipment that are created for this order.

1. To confirm the load, shipment, and work details on the sales line, select the line, and then, on the **Warehouse** menu above the grid, select **Load details**, **Shipment details**, or **Work details**.
1. In the sales order that you just created, on the **Sales order lines** FastTab, select **Add line** to add another line.
1. On the new line, set the **Item number** field to *A0002* and the **Quantity** field to *1*.
1. Repeat lines 6 through 9 to reserve the line and release it to the warehouse. The system creates a **new** shipment for the line that you added. However, because you're using advanced wave load building, the system adds that shipment and load line to the existing wave. If you weren't using advanced wave load building, the system would create a new load for the shipment.
1. In the sales order that you just created, on the **Sales order lines** FastTab, select **Add line** to add another line.
1. On the new line, set the **Item number** field to *M9200* and the **Quantity** field to *1*.
1. Repeat lines 6 through 9 to reserve the line and release it to the warehouse. As before, the system creates a **new** shipment for the line that you added. However, because the item is from the **CarAudio** item group, it **fails to pass the constraints that you set up for the load mix group**. Therefore, it's **added to a new load**. If you hadn't specified a load mix group on the load build template, this shipment would have been added to the first load.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]