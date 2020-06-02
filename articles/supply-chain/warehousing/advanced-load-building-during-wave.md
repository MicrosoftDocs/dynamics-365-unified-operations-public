---
# required metadata

title: Set up and use advanced wave load building
description: Advanced wave load building automatically assigns shipments to existing waves during wave execution, which can help you create meaningful loads that represent trucks without requiring you to use the load-planning workbench.
author: mirzaab
manager: AnnBe
ms.date: 02/01/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope:  Retail, Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: mirzaab
ms.search.validFrom: 2020-02-01
ms.dyn365.ops.version: Release 10.0.8
---

# Set up and use advanced wave load building

Advanced wave load building automatically assigns shipments to existing waves during wave execution, which can help you create meaningful loads that represent trucks without requiring you to use the load-planning workbench. This is useful for businesses who want to use the concept of loads to track and plan the shipment of goods in a truck/trailer, but don't want to manually create these loads each day.

During wave processing, the system normally creates a new load for each shipment that doesn't have a load assigned, but with advanced wave load building, the system instead  assigns each unassigned shipment to an existing load (when an appropriate load exists) and only creates new loads when required. The advanced wave load building feature creates loads automatically based on criteria that you define. You'll set the system up as follows:

- Create *wave templates* that include the new `buildLoads` method, which enables advanced web load building for waves that use those templates.
- Set up *load-build templates*, each of which links to a specific wave template and method. These control which load (existing or new) the load lines being waved will be added to. You can choose to combine or separate shipments based on criteria such as load template, equipment, and other field values on the load line.
- Define *load mix groups* to control which items should and shouldn't be combined on a single load, and choose whether the restriction should produce a warning or an error. You can also choose whether or not to evaluate the volumetric restriction of the load template.

## Enable advanced wave load building on your system

Before you can use this feature, two features must be enabled on on your system. Administrators can use the [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) settings to check the status of these features and enable them if needed. Here, the features are listed listed as:

1. Wave load building feature:
    - **Module**: Warehouse management
    - **Feature name**: Wave load building feature

1. Organization wide wave step code:
    - **Module**: Warehouse management
    - **Feature name**: Organization wide wave step code

### Enable sample data

To work through this demo using the sample records and values specified here, you must be on a system with the standard [demo data](../../fin-ops-core/dev-itpro/deployment/deploy-demo-environment.md) installed, and you must select the **USMF** legal entity before you begin.

You can also use this demo as guidance for how to use this feature when working on a production system, but then you must then substitute your own values, and you may be missing some types of required records that would otherwise be provided by the standard demo data.

### Make sure the scenario setup includes enough available inventory

If you are working with **USMF** demo data, then start by making sure your system is set up with enough inventory at each relevant location. This demo expects that you have the following inventory available in Warehouse **62**:

- **Item A0001** - 10 Pcs
- **Item A0002** - 10 Pcs
- **Item M9200** - 10 ea

Item **M9200** will need to be added to the warehouse. Follow the steps below to add the item inventory:

#### Create a new *License Plate ID*

- Go to **Warehouse management > Setup > Warehouse > License plates**
- Select **New** from the Action Pane
- In the new row, **License plate** field enter *LP6203*.
- Select **Save**

#### Create a *Standard Cost* for item *M9200* in **Site 6**

- Go to **Product information management > Products > Released products**
- Search on **M9200**
- Focus on the item line then Select **Manage costs** from the Action Pane.
- Select **Item price** from the *Set up* group.
- Select the **Pending prices** tab.
- Select **New** from the Action Pane.
- Enter the following values on the line:
  - **Costing type** - *Planned cost*
  - **Price type** - *Cost*
  - **Version** - *10*
  - **Site** - *6*
  - **Price** - *1.60*.
- Select **Save** from the Action Pane.
- Now Select **Activate pending price(s)** in the Action Pane.
- Select the **Active prices** tab to validate that the new cost price for *Site 6* has been added.

#### Create inventory in *Warehouse 62*

- Go to **Inventory management > Journal entries > Items > Inventory adjustment**
- Select **New** from the Action Pane.
- In the **Create inventory journal** FlyOut *Overview* FastTab, accept the defaults and on the **Warehouse** field, enter *62*.
- Select **OK*** to close the FlyOut.
- The **Inventory adjustment** form opens. On the **Journal lines** FastTab Action Pane, select **New** to add a new line.
- Accept the defaults and enter the following on the line:
  - **Item number** - *M9200*
  - **Location** - *bulk-003*
  - Change **Quantity** to *10*.
- Select **Save** from the Action Pane.
- Select **Validate** from the Action Pane to check for errors.
- Select **OK** on the **Check journal** FlyOut to start the check. A message appears when the check is completed.
- Select **Post** from the Action Pane to commit the inventory adjustment.
- Select **OK** on the **Post journal** FlyOut to start the posting. A message appears when the posting is completed.

## Set up advanced wave load building

### Regenerate your wave process methods

You may need to regenerate your wave process methods to make the load building method available. To do this:

1. Go to **Warehouse management** > **Setup** > **Waves** > **Wave process methods**.
2. Check whether **buildLoads** is present in the list. If it isn't, select **Regenerate methods** on the action bar to add it.

### Set up your wave templates

To take advantage of advanced wave load building, you must include the `buildLoads` method in each of your relevant [wave templates](tasks/configure-wave-processing.md) as follows:

1. Go to **Warehouse management** > **Setup** >  **Waves** > **Wave templates**.
1. Select a relevant wave template. (If you're working with the **USMF** legal-entity demo data, select the **62 Shipping Default** template.)
1. Select **Edit** on the action pane to put the page into edit mode.
1. In the **Methods** FastTab, select the **buildLoads** method from the **Remaining methods** table.
1. Select the right-pointing arrow button between the tables to move the **buildLoads** method to the **Selected Methods** table.
1. To assign a value in the **Wave step code** column for the **buildLoads** method you just added to the **Selected Methods** table, you must first create a code in **Wave step codes**. You can choose any value you want, but take note of it because you'll need it later.
1. To create code **WSC2112**, perform the following steps:
    1. In the **Wave step code** field, right-click on the downward selection arrow and select **View details**.
    1. In the **Wave step codes** form, select **New** in the Action Pane.
    1. In the **Wave step code** field, enter *WSC2112*.
    1. In the **Wave step description** field, enter *WSC2112*.
    1. In the **Wave step type** field, select *Load Building*.
1. Select **Save** and close the form.
1. In the **Wave step code** field, select the code you just created **WSC2112**.
1. Select **Save** in the **Wave template** Action Pane.

> [!NOTE]
> Wave step codes are codes that users can set up and use to link specific instances of wave methods to a corresponding template. The templates include templates for replenishment, containerization, label printing, load building, and sorting.
>
> When wave step codes aren't used, users must enter free text to reference a specific template from the wave method instance. Free text is prone to errors because users must make sure that the wave step text that they add for a specific wave step method in a wave template exactly matches the wave step text in the target template.
>
> Wave step codes for a specific wave step type are set up on a separate page. For every wave step method instance in a wave template that requires a wave step code, the wave step code must be selected in a drop-down list. Selection in a drop-down list replaces free text entry and helps reduce the risk and impact of human error. Setup codes are used to link a wave step method in a wave template to a target template for the method.

### Set up your load mix groups

Load mix groups establish rules for which types of items can be combined into a single load. You can set up as many load mix groups as you need, but to use this feature you must have at least one. To create a load mix group:

1. Go to **Warehouse management** > **Setup** >  **Load** > **Load mix groups**.
1. Select **New** on the action pane to create a new load group.
1. Enter a relevant name for your new group in the **Load mix group ID** field.
    1. If you're working with the **USMF** legal-entity demo data:
        1. In the **Load mix group ID** field, enter *TV*.
        1. In the **Description**field, enter *TV*.
    1. Select **Save** to enable the **Load mix group criteria** FastTab.
1. In the **Load mix group criteria** fast tab, select the **New** button to add a row.
1. Then configure the desired values in each column as needed for the new row. This determines which item groups are considered for the load mix.
    1. If you're working with the **USMF** legal-entity demo data, then in the **Item group** column select *TV&Video*.
    1. Select **Save** on the action pane to enable the **Load mix group constraints** FastTab.
1. In the **Load mix group constraints** fast tab, select **New** to create a new row.
1. Then configure the desired values in each column as needed.
1. If you're working with the **USMF** legal-entity demo data:
    1. In the **Item group** field, select *CarAudio*.
    1. In the **Load build action** field, select *Restrict*. This will prevent items with an item group of **CarAudio** from being on the same load as items with an item group of **TV&Video**.
1. Continue working with these rules until you have added all the criteria and constraints you need for this load mix group.
1. If you are working with **USMF** legal-entity demo data, you are done.

### Set up your load build templates

You can set up as many load build templates as you need, but to use this feature you must have at least one. To create a load build template:

1. Go to **Warehouse Management** > **Setup** >  **Load** > **Wave load building templates**.

1. Select **New** on the action pane to add a new row to the table here. Then make the  following settings for the new row:

    | Setting | Instructions | **USMF** legal-entity demo value |
    |--|--|--|
    | **Sequence number** | Sequence in which the template will be evaluated. | 1 |
    | **Load build template name** | Unique identifier of the load build template. Enter the name of the template you created or updated previously during this setup. | 62 Shipping Default |
    | **Wave step code** | Wave step code to link the template to a wave method. Enter the code you chose for the buildLoads method when you set up the wave template previously during this setup | WSC2112 |
    | **Load template ID** | Load template to use when creating new loads, and to match against when assigning to existing loads. The load template defines maximum weight and volume permitted for the entire load. Select the load template to use for any loads that are created. | Stnd Load Template |
    | **Equipment** | Equipment to match against when assigning to existing loads, and to populate on new loads that are created | (leave blank)  |  |
    | **Load mix group ID** | Load mix group that will be used if the item is allowed on the load. The mix group establishes rules for which types of items can can't be combined in a single load. Select one of the mix groups that you created previously during this setup. | TV |
    | **Use open loads** | Should existing open loads be added? ***None*** will not add to any existing loads. ***Any*** will add to any existing loads that are valid for the line. ***Assigned*** will add to the load assigned to the wave. | Any |
    | **Create loads** | Should new loads be created? Choose whether to create a new load if no existing loads match the criteria.  | Yes (selected) |
    | **Allow shipment line split** | Allow a load line to be split across multiple loads if it exceeds the maximum capacity of the load template. Choose whether to allow a single line to be split across multiple loads if the full line exceeds the load capacity. | No (unselected) |
    | **Validate volumetrics** | When enabled load building will check the weight and volume as each load line is added to ensure the load template maximums are respected. Choose whether to evaluate the volumetric limits of the specified load template. | No (unselected) |

1. Select **Save** on the action pane to enable the **Edit query** option.
1. Select **Edit query** on the action pane to open a FlyOut for editing the query.

1. Select the **Sorting** tab in the FlyOut and select the **Add** button to add a new row. Configure the row to define the sorting rules you want to use, for example by entering the following to sort the search result in ascending order by *Order number*:

    - **Table**: Load details
    - **Derived table**: Load details
    - **Field**: Order number
    - **Search direction**: Ascending

1. Select **OK** to save your changes and close the FlyOut.

1. In the **Break by** fast tab, set rules to control how your loads will be split up. You might typically use this to break on custom fields that have been extended onto the load line, such as Route, Tour, Run, etc. For example, to create one load per order number, select the **Break by** check box for the row with the following values:

    - **Reference table name**: Load details
    - **Reference field name**: Order number

## Scenario

This scenario shows how the settings previously described in this topic will affect warehouse operations while processing a sales order. This scenario uses the **USMF** legal-entity demo data combined with other demo values provided in these setup instructions.

### Create Sales Orders

1. Go to **Sales and Marketing** > **Sales orders** >  **All sales orders**.
1. Select **New** on the action pane to open a FlyOut for creating a new sales order.
1. In the FlyOut, enter the following:
    - On the **Customer** fast tab, set **Customer account** to *US-007*.
    - On the **General** fast tab, set **Warehouse** to *62*.
1. Select **OK** to create the sales order and close the FlyOut.
1. Your new sales order opens. It should include a new, empty line in the **Sales order lines** table. For this new line, set the **Item number** to *A0001* and the **Quantity** to *1*.
1. Open the **Inventory** drop-down list at the top of the **Sales order lines** table and select **Reservation**.
1. Select **Reserve lot** from the action pane.
1. Select the close **(X)** button in the upper-right corner to return to your sales order.
1. Open the **Warehouse** tab on the action pane and then select **Actions** > **Release to warehouse**. The system creates a shipment and adds it to a new load because there is no existing load that contains load lines with this order number.
1. Informational messages are displayed indicating the Work, Wave and shipment created for this order. Load, Shipment and Work details can be confirmed on the sales line by focusing on the line and selecting **Warehouse** on the Action Pane, then selecting the *details* menu item you are validating.
1. On the sales order you just created, in the **Sales order lines** fast tab, select **Add line** to add another line to your sales order.
1. Add **Item number** *A0002* with a **Quantity** of *1*.
1. **Reserve** the line and **Release to warehouse**, as you did previously.  The system now creates a **new** shipment for the added line, but because you are using advanced wave load building, it adds that shipment and load line to the existing wave. *Without this feature*, a new load would have been created for the shipment.
1. On the sales order you just created, in the **Sales order lines** fast tab, select **Add line** to add another line to your sales order.
1. Add **Item number** *M9200* with a **Quantity** of *1*. Reserve the line and release the order to the warehouse. As before, a new shipment is created, but because this item is from the **CarAudio** item group, it ***fails to pass the load mix group constraints*** we set up earlier and is therefore ***added to a new load***.
1. If a load mix group hadn't been specified on the load build template, then this shipment would have been added to the first load as well.
