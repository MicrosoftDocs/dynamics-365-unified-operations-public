# Advanced load building during wave

Advanced load building automatically assigns shipments to existing waves during wave execution, which can help you create meaningful loads that represent trucks without requiring you to use the load-planning workbench. This is useful for businesses who want to use the concept of loads to track and plan the shipment of goods in a truck/trailer, but don't want to manually create these loads each day.

When a shipment isn't assigned to a load during wave processing, the system normally creates a new load for that shipment, but advanced load building enables the system instead to assign unassigned shipments to existing loads (when an appropriate load exists), and only create new loads when required.

The load building feature creates loads automatically based on user-defined criteria. A load-build template links to a specific wave template method, and controls which load (existing or new) the load lines being waved will be added to. You can choose to combine or separate shipments based on criteria such as load template, equipment, and/or other field values on the load line. You can also define load mix groups to control which items shouldn't be combined on a single load, and choose whether the restriction should produce a warning or an error. You can also choose whether or not to evaluate the volumetric restriction of the load template.

## Set up advanced load building

### Regenerate your wave process methods

You may need to regenerate your wave process methods to make the load building method available. To do this:

1. Go to **Warehouse management** > **Setup** > **Waves** > **Wave process methods**.
2. Check whether **buildLoads** is present in the list. If it isn't, select **Regenerate methods** on the action bar to add it.

<!-- KFM: I don't see buildLoads here. Should we list some prerequisites that I might be missing? -->

### Set up your wave templates

1. Go to **Warehouse management** > **Setup** >  **Waves** > **Wave templates**.
1. Select the template **62 Shipping Default**.
1. Select **Edit** on the command bar to put the page into edit mode.
1. In the **Methods** FastTab, select the **Load Building** method from the **Remaining methods** column.
1. Select the right-pointing arrow button between the columns to move the **Load Building** method to the **Selected Methods** column.
1. Assign the **LoadBuild** wave step code to the method.

<!-- KFM: 

* Is it always "62 Shipping Default" that users should choose, or is that just an example?
* I don't see the **Load Building** method here. 
* What is a "wave step code" and how do I assign this?
* It's a bit tricky to go into edit mode, but I suppose that's standard for SCM. Should we provide full details or assume the user is used to this?

 -->

### Load mix group

1. Go to **Advanced Warehouse Management** > **Setup** >  **Load** > **Load Mix Group**.
1. Create a new mix group named "TV".
1. In the **Item Criteria** create a record and select **TV&Video** in the **Item group** column.
1. In the **Mixing Constraints** grid, create a new record, select **CarAudio** as the **Item group**, and in the **Load build action** column select **Restrict**. This will restrict items with an item group of **CarAudio** from being on the same load as items with an item group of **TV&Video**.

<!-- KFM: This seems like an example based on sample data. Shouldn't we make this more generic? I dont't have **Advanced Warehouse Management**--I must be missing something here. -->

### Load build template

Navigate to _Advanced Warehouse Management - Setup - Load - Load Build Template_ and create a new record.

- Sequence – 1
- Load build name – 62
- Wave step code – LoadBuild
- Load template ID – The load template that will be used for any loads that are created – Stnd Load Template
- Load mix group – Group that is used to determine what can or cannot be combined on a load – TV
- Use open loads – Controls what existing loads are allowed to be used – Any
- Create loads – Should the system create loads if it doesn't find one that matches the criteria? – Yes
- Allow shipment line split – Can a single line be split across multiple loads if the full line exceeds the load capacity? – No
- Validate volumetrics – Controls if the volumetric limits of the load template should be evaluated - No

Open the Edit Query for the template, and in the sorting table, add sorting on Load details – Order number – Ascending.

In the Break by grid, check the 'Break by' box for the Load details – Order number record.

This will create one load per order number. Generally, this functionality is used to break on custom fields that have been extended onto the load line, such as Route, Tour, Run, etc.

## Example scenario

Navigate to _Sales and Marketing_ _-_ _Common - Sales order - All sales orders_ and create a new sales order. Select customer US-007 and warehouse 62.

Add a line and specify item A0001, quantity 1. Click on Inventory – Reservation and reserve inventory to the line. Click on Release to warehouse in the Warehouse _-_ Actions section of the ribbon. A shipment will be created, and added to a new load, as there is no existing load containing load lines with this order number.

Create another line on the same sales order, for item A0002. Reserve the line and release the order to the warehouse again. The system will create a new shipment for the new line, but because of load building it will add that shipment and load line to the existing wave. Without load building enabled, a new load would have been created for the shipment as well.

Create a third line of the same sales order, for item M9200. Reserve the line and release the order to the warehouse. A new shipment will be created, and added to a new load, because the item failed the load mix group constraints. If a load mix group hadn't been specified on the load build template, then this shipment would have been added to the first load as well.
