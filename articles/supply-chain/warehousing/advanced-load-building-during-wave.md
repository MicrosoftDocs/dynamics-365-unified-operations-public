# Advanced load building during wave

Advanced wave load building automatically assigns shipments to existing waves during wave execution, which can help you create meaningful loads that represent trucks without requiring you to use the load-planning workbench. This is useful for businesses who want to use the concept of loads to track and plan the shipment of goods in a truck/trailer, but don't want to manually create these loads each day.

When a shipment isn't assigned to a load during wave processing, the system normally creates a new load for that shipment, but advanced wave load building enables the system instead to assign unassigned shipments to existing loads (when an appropriate load exists), and only create new loads when required.

The advanced wave load building feature creates loads automatically based on user-defined criteria. A load-build template links to a specific wave template method, and controls which load (existing or new) the load lines being waved will be added to. You can choose to combine or separate shipments based on criteria such as load template, equipment, and/or other field values on the load line. You can define load mix groups to control which items shouldn't be combined on a single load, and choose whether the restriction should produce a warning or an error. You can also choose whether or not to evaluate the volumetric restriction of the load template.

## Enable wave load building on your system

Before you begin trying to set up or use advanced wave load building, you must make sure the feature is available on your system. Administrators can use the [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) settings to check the feature status and enable it if needed. Here, the feature is listed listed as:

- **Module**: Warehouse management
- **Feature name**: Wave load building feature

<!-- KFM: Add this?: "If you don't see the feature listed, then it may have been made a standard part of the product since this documentation was written, in which case you can proceed with the remaining sections of this topic and all of the described features should be available to you." -->

## Set up wave load building

### Regenerate your wave process methods

You may need to regenerate your wave process methods to make the load building method available. To do this:

1. Go to **Warehouse management** > **Setup** > **Waves** > **Wave process methods**.
2. Check whether **buildLoads** is present in the list. If it isn't, select **Regenerate methods** on the action bar to add it.

### Set up your wave templates

To take advantage of advanced wave load building, you must include the `buildLoads` method in each of your relevant [wave templates](tasks/configure-wave-processing.md) as follows:

1. Go to **Warehouse management** > **Setup** >  **Waves** > **Wave templates**.
1. Select a relevant wave template.<BR>(If you're working with the **USMF** company demo data, select the **62 Shipping Default** template.)
1. Select **Edit** on the action pane to put the page into edit mode.
1. In the **Methods** FastTab, select the **buildLoads** method from the **Remaining methods** table.
1. Select the right-pointing arrow button between the tables to move the **buildLoads** method to the **Selected Methods** table.
1. Assign a value in he **Wave step code** column for the **LoadBuild** method you just added to the **Selected Methods** table. You can choose any value you want, but take note of it because you'll need it later. More information: [Wave step codes](wave-step-codes.md)<BR>(If you're working with the **USMF** company demo data, you could enter "WSC2112", which is the value we'll show later in this topic.)

<!-- KFM: Anything more to say about how to pick a wave step code? -->

### Set up your load mix groups

You can set up as many load mix groups as you need, but to use this feature you must have at least one. To create a load mix group:
<!-- KFM: seems like we have no other documentation about load mix groups. Are these added by this feature? Should we say more about them here? -->

1. Go to **Warehouse management** > **Setup** >  **Load** > **Load mix groups**.
1. Select **New** on the action pane to create a new load group.
1. Enter a relevant name for your new group in the **Load mix group ID** field.<BR>(If you're working with the **USMF** company demo data, enter "TV".)
1. In the **Load mix group criteria** FastTab, select the **New** button to add a row here and then make settings in each column as needed for the new row.<BR>(If you're working with the **USMF** company demo data, select **TV&Video** in the **Item group** column.) <!-- KFM: We should add a sentence to explain what this will do, as we do later in this procedure. What are all these "code" columns for? -->
1. Select **Save** on the action pane to save your work.
1. In the **Load mix group constraints** FastTab, select **New** to create a new row here and then make settings in each column as needed. <BR>(If you're working with the **USMF** company demo data, select **CarAudio** in the **Item group** column and **Restrict** in the **Load build action** column. This will restrict items with an item group of **CarAudio** from being on the same load as items with an item group of **TV&Video**.)

### Set up your load build templates

You can set up as many load build templates as you need, but to use this feature you must have at least one. To create a load build template:
<!-- KFM: Again, it seems like we have no other documentation about load build templates. Are these added by this feature? Should we say more about them here? -->

1. Go to **Warehouse Management** > **Setup** >  **Load** > **Wave load building templates**.
1. Select **New** on the action pane to add a new row to the table here. Then make the settings described in the following table:
    | Column | Description | **USMF** company demo value |
    |--|--|--|
    | **Sequence** | <!-- KFM: What is this? --> | 1 |
    | **Load build template name** | Enter the name of the template you created previously during this setup. <!-- KFM: Exact? Seems like get no help --> | 62 Shipping Default <!-- KFM: Or just "62" --> |
    | **Wave step code** | Enter the code you chose for the LoadBuild method when you set up the wave template previously during this setup | WSC2112 |
    | **Load template ID** | 

1. Make the following settings:
    - Sequence – 1
    - Load build name – 62
    - Wave step code – LoadBuild
    - Load template ID – The load template that will be used for any loads that are created – Stnd Load Template
    - Load mix group – Group that is used to determine what can or cannot be combined on a load – TV
    - Use open loads – Controls what existing loads are allowed to be used – Any
    - Create loads – Should the system create loads if it doesn't find one that matches the criteria? – Yes
    - Allow shipment line split – Can a single line be split across multiple loads if the full line exceeds the load capacity? – No
    - Validate volumetrics – Controls if the volumetric limits of the load template should be evaluated - No
1. Open the **Edit Query** for the template, and in the sorting table, add sorting on Load details – Order number – Ascending.
1. In the **Break by** grid, select the **Break by** check box for the Load details – Order number record.

This will create one load per order number. Generally, this functionality is used to break on custom fields that have been extended onto the load line, such as Route, Tour, Run, etc.

## Example scenario

<!-- Add intro. What does this scenario demonstrate? What will we do here? -->

Navigate to _Sales and Marketing_ _-_ _Common - Sales order - All sales orders_ and create a new sales order. Select customer US-007 and warehouse 62.

<!-- KFM: I can't find this path--maybe "common" doesn't exist? Where does this sample data come from? -->

Add a line and specify item A0001, quantity 1. Click on Inventory – Reservation and reserve inventory to the line. Click on Release to warehouse in the Warehouse _-_ Actions section of the ribbon. A shipment will be created, and added to a new load, as there is no existing load containing load lines with this order number.

<!-- KFM: When I click on **Add line**, nothing happens. How do I specify an "item"? I don't see any of these settings here. -->


Create another line on the same sales order, for item A0002. Reserve the line and release the order to the warehouse again. The system will create a new shipment for the new line, but because of load building it will add that shipment and load line to the existing wave. Without load building enabled, a new load would have been created for the shipment as well.

Create a third line of the same sales order, for item M9200. Reserve the line and release the order to the warehouse. A new shipment will be created, and added to a new load, because the item failed the load mix group constraints. If a load mix group hadn't been specified on the load build template, then this shipment would have been added to the first load as well.
