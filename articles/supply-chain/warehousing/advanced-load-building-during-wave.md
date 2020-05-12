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

Advanced wave load building automatically assigns shipments to existing waves <!-- do we mean *existing loads*? --> during wave execution, which can help you create meaningful loads that represent trucks without requiring you to use the load-planning workbench. This is useful for businesses who want to use the concept of loads to track and plan the shipment of goods in a truck/trailer, but don't want to manually create these loads each day.

During wave processing, the system normally creates a new load for each shipment that doesn't have a load assigned, but with advanced wave load building, the system instead  assigns each unassigned shipment to an existing load (when an appropriate load exists) and only creates new loads when required. The advanced wave load building feature creates loads automatically based on criteria that you define. You'll set the system up as follows:

- Create *wave templates* that include the new `buildLoads` method, which enables advanced web load building for waves that use those templates.
- Set up *load-build templates*, each of which links to a specific wave template and method. These control which load (existing or new) the load lines being waved will be added to. You can choose to combine or separate shipments based on criteria such as load template, equipment, and other field values on the load line.
- Define *load mix groups* to control which items should and shouldn't be combined on a single load, and choose whether the restriction should produce a warning or an error. You can also choose whether or not to evaluate the volumetric restriction of the load template.

## Enable advanced wave load building on your system

Before you begin trying to set up or use advanced wave load building, you must make sure the feature is available on your system. Administrators can use the [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) settings to check the feature status and enable it if needed. Here, the feature is listed listed as:

- **Module**: Warehouse management
- **Feature name**: Wave load building feature

The **Wave load building feature** is dependent upon another feature to be enabled, **Organization wide wave step code**. You must also enable this feature. Here, the feature is listed listed as:

- **Module**: Warehouse management
- **Feature name**: Organization wide wave step code

<!-- KFM: Add this?: "If you don't see the feature listed here, then it may have become a standard part of the product since this documentation was written, in which case you can proceed with the remaining sections of this topic and all of the described features should be available to you." -->

### Enable sample data

To work through this demo using the sample records and values specified here, you must be on a system with the standard [demo data](../../fin-ops-core/dev-itpro/deployment/deploy-demo-environment.md) installed, and you must select the **USMF** legal entity before you begin.

You can also use this demo as guidance for how to use this feature when working on a production system, but then you must then substitute your own values, and you may be missing some types of required records that would otherwise be provided by the standard demo data.

### Make sure the scenario setup includes enough available inventory

If you are working with **USMF** demo data, then start by making sure your system is set up with enough inventory at each relevant location. This demo expects that you have the following inventory available in Warehouse **62**:

- **Item A0001** - 10 Pcs
- **Item A0002** - 10 Pcs
- **Item M9200** - 10 ea
<!-- HHM: Karl, Item M9200 will need to be added in inventory with a standard cost price for Site 6. Should this process be spelled out in detail or called out with assumption user has prior knowledge of this task? -->

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
1. To assign a value in the **Wave step code** column for the **buildLoads** method you just added to the **Selected Methods** table, you must first create a code in **Wave step codes**. You can choose any value you want, but take note of it because you'll need it later.<!-- HHM: Commenting this out: More information: [Wave step codes](wave-step-codes.md) -->
1. To create code **WSC2112**, perform the following steps:
1. In the **Wave step code** field, right-click on the downward selection arrow and select **View details**.
1. In the **Wave step codes** form, select **New** in the Action Pane.
1. In the **Wave step code** field, enter **WSC2112**. In the **Wave step description** field, enter **WSC2112**. In the **Wave step type** field, select **Load Building**.
1. Select **Save** and close the form.
1. In the **Wave step code** field, select the code you just created **WSC2112**.
1. Select **Save** in the **Wave template** Action Pane.

> [!NOTE]
> Wave step codes are codes that users can set up and use to link specific instances of wave methods to a corresponding template. The templates include templates for replenishment, containerization, label printing, load building, and sorting.  
When wave step codes aren't used, users must enter free text to reference a specific template from the wave method instance. Free text is prone to errors because users must make sure that the wave step text that they add for a specific wave step method in a wave template exactly matches the wave step text in the target template.  
Wave step codes for a specific wave step type are set up on a separate page. For every wave step method instance in a wave template that requires a wave step code, the wave step code must be selected in a drop-down list. Selection in a drop-down list replaces free text entry and helps reduce the risk and impact of human error. Setup codes are used to link a wave step method in a wave template to a target template for the method.

<!-- KFM: Anything more to say about how to pick a wave step code? -->

### Set up your load mix groups

Load mix groups establish rules for which types of items can be combined into a single load. You can set up as many load mix groups as you need, but to use this feature you must have at least one. To create a load mix group:
<!-- KFM: seems like we have no other documentation about load mix groups. Are these added by this feature? Should we say more about them here? -->

1. Go to **Warehouse management** > **Setup** >  **Load** > **Load mix groups**.
1. Select **New** on the action pane to create a new load group.
1. Enter a relevant name for your new group in the **Load mix group ID** field. (If you're working with the **USMF** legal-entity demo data, enter "TV" for the **Load mix group ID** and **Description**.)
1. Select **Save**.
1. In the **Load mix group criteria** fast tab, select the **New** button to add a row.
1. Then configure the desired values in each column as needed for the new row. (If you're working with the **USMF** legal-entity demo data, select **TV&Video** in the **Item group** column.) <!-- KFM: We should add a sentence to explain what this will do, as we do later in this procedure. What are all these "code" columns for? -->
1. Select **Save** on the action pane to save your work.
1. In the **Load mix group constraints** fast tab, select **New** to create a new row.
1. Then configure the desired values in each column as needed. (If you're working with the **USMF** legal-entity demo data, select **CarAudio** in the **Item group** column and **Restrict** in the **Load build action** column.) *This will prevent items with an item group of **CarAudio** from being on the same load as items with an item group of **TV&Video**.* <!-- KFM: What are all these "code" columns for? -->
1. Continue working with these rules until you have added all the criteria and constraints you need for this load mix group. (If you are working with **USMF** legal-entity demo data, you are done.)

### Set up your load build templates

You can set up as many load build templates as you need, but to use this feature you must have at least one. To create a load build template:
<!-- KFM: Again, it seems like we have no other documentation about load build templates. Are these added by this feature? Should we say more about them here? -->

1. Go to **Warehouse Management** > **Setup** >  **Load** > **Wave load building templates**.

1. Select **New** on the action pane to add a new row to the table here. Then make the  following settings for the new row:

    | Setting | Instructions | **USMF** legal-entity demo value |
    |--|--|--|
    | **Sequence** | <!-- KFM: What is this? --> | 1 |
    | **Load build template name** | Enter the name of the template you created or updated previously during this setup. <!-- KFM: Exact? Seems like I get no help --> | 62 Shipping Default <!-- KFM: Or just "62" --> |
    | **Wave step code** | Enter the code you chose for the LoadBuild method when you set up the wave template previously during this setup <!-- KFM: Exact? Looks like a drop-down but offers no values --> | WSC2112 |
    | **Load template ID** | The load template defines maximum weight and volume permitted for the entire load. Select the load template to use for any loads that are created.   <!-- Seems like we have no documentation about load templates. --> | Stnd Load Template |
    | **Equipment** | Equipment to match against when assigning to existing loads, and to populate on new loads that are created | (leave blank) <!-- KFM: This setting is offered, but you didn't mention it. Should we? --> |  |
    | **Load mix group ID** | The mix group establishes rules for which types of items can can't be combined in a single load. Select one of the mix groups that you created previously during this setup. | TV |
    | **Use open loads** | Choose whether to allow existing loads to be used (any or none) | Any |
    | **Create loads** | Choose whether to create a new load if no existing loads match the criteria. <!-- KFM: Which criteria? What happens if this is "no" and we don't have a match? --> | Yes (selected) |
    | **Allow shipment line split** | Choose whether to allow a single line to be split across multiple loads if the full line exceeds the load capacity. <!-- KFM: What happens if this is "no" and we are over capacity? --> | No (unselected) |
    | **Validate volumetrics** | Choose whether to evaluate the volumetric limits of the specified load template. <!-- KFM: Does the load template do anything if this is set to "no"? What happens if this is "yes" and the check fails? --> | No (unselected) |

1. Select **Save** on the action pane to enable the **Edit query** option.
1. Select **Edit query** on the action pane to open a flyout for editing the query.

1. Select the **Sorting** tab in the flyout and select the **Add** button to add a new row. Configure the row to define the sorting rules you want to use, for example by entering the following to sort the search result in ascending order by *Order number*: <!-- KFM: It's not clear to me what we are doing here. -->

    - **Table**: Load details
    - **Derived table**: Load details
    - **Field**: Order number
    - **Search direction**: Ascending

1. Select **OK** to save your changes and close the flyout.

1. In the **Break by** fast tab, set rules to control how your loads will be split up. You might typically use this to break on custom fields that have been extended onto the load line, such as Route, Tour, Run, etc. For example, to create one load per order number, select the **Break by** check box for the row with the following values:

    - **Reference table name**: Load details
    - **Reference field name**: Order number

## Scenario

This scenario shows how the settings previously described in this topic will affect warehouse operations while processing a sales order. This scenario uses the **USMF** legal-entity demo data combined with other demo values provided in these setup instructions.

### Create Sales Orders

1. Go to **Sales and Marketing** > **Sales orders** >  **All sales orders**.
1. Select **New** on the action pane to open a flyout for creating a new sales order.
1. In the flyout, enter the following:
    - On the **Customer** fast tab, set **Customer account** to "US-007".
    - On the **General** fast tab, set **Warehouse** to "62".
1. Select **OK** to create the sales order and close the flyout.
1. Your new sales order opens. It should include a new, empty line in the **Sales order lines** table. For this new line, set the **Item number** to "A0001" and the **Quantity** to "1".
1. Open the **Inventory** drop-down list at the top of the **Sales order lines** table and select **Reservation**. <!-- KFM: How do I "reserve inventory to the line" here, just edit the **Reservation** column? -->
1. Select **Reserve lot** from the action pane.
1. Select the close **(X)** button in the upper-right corner to return to your sales order.
1. Open the **Warehouse** tab on the action pane and then select **Actions** > **Release to warehouse**. The system creates a shipment and adds it to a new load because there is no existing load that contains load lines with this order number. <!-- KFM: Where is a good place to go to confirm this? -->
1. Informational messages are displayed indicating the Work, Wave and shipment created for this order.
1. On the sales order you just created, in the **Sales order lines** fast tab, select **Add line** to add another line to your sales order.
1. Add **Item number** "A0002" with a **Quantity** of "1".
1. **Reserve** the line and **Release to warehouse**, as you did previously.  The system now creates a **new** shipment for the added line, but because you are using advanced wave load building, it adds that shipment and load line to the existing wave. *Without this feature*, a new load would have been created for the shipment.
1. On the sales order you just created, in the **Sales order lines** fast tab, select **Add line** to add another line to your sales order.
1. Add **Item number** "M9200" with a **Quantity** of "1". Reserve the line and release the order to the warehouse. As before, a new shipment is created, but because this item is from the **CarAudio** item group, it ***fails to pass the load mix group constraints*** we set up earlier and is therefore ***added to a new load***.
1. If a load mix group hadn't been specified on the load build template, then this shipment would have been added to the first load as well. <!-- KFM: It seems like I can't reserve this item (none in warehouse?). Does the demo data really support this example? -->
