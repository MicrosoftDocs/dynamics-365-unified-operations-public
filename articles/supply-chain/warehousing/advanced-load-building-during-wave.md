# Advanced load building during wave

# Released in version 10.0.1

# About

Some businesses want to use the concept of loads to track and plan the shipment of goods in a truck/trailer, but don&#39;t want to manually create these loads each day. If a shipment isn&#39;t assigned to a load during wave processing, the wave will be default create a new load for that shipment. Advanced load building allows the wave to assign the shipment to an existing load, if one exists that meets the criteria, or create a new load if required.

Load building allows the system to automatically assign shipments to existing waves during wave execution, letting users create meaningful loads representing trucks without using the load planning workbench.

The load building features allows users to create loads automatically based on user defined criteria. A load build template is created, which links to a specific wave template method, and controls what load (existing or new) load lines being waved will be added to. Criteria such as load template, equipment, and any fields on the load line can be used to combine/separate shipments. Load mix groups can be defined to control what items should not be combined on a single load, users can choose if the restriction should product a warning or an error. Users can also choose whether to evaluate the volumetric restriction of the load template, or if volumetric/weight maximums should not be considered and only other criteria.

# Setup

## Wave process methods

You may need to regenerate the wave process methods for the load building method to become available. Navigate to _Warehouse management - Setup - Waves -  Wave process methods_ and check if buildLoads is present in the list. If it isn&#39;t, click on &#39;Regenerate methods&#39; in the action bar to add it.

## Wave templates

Navigate to _Warehouse management - Setup -  Waves - Wave templates._ Select the template &#39;62 Shipping Default&#39;. In the Methods FastTab, add the Load Building method to the Selected Methods. Assign the &#39;LoadBuild&#39; wave step code to the method.

## Load mix group

Navigate to _Advanced Warehouse Management -Setup - Load - Load Mix Group_. Create a new mix group named TV.

In the Item Criteria create a record and select &#39;TV&amp;Video&#39; in the Item group column.

In the Mixing Constraints grid, create a new record, select CarAudio as the Item group, and in the Load build action column select &#39;Restrict.&#39;

This will restrict items with an item group of CarAudio from being on the same load as items with an item group of TV&amp;Video.

## Load build template

Navigate to _Advanced Warehouse Management - Setup - Load - Load Build Template_ and create a new record.

- Sequence – 1
- Load build name – 62
- Wave step code – LoadBuild
- Load template ID – The load template that will be used for any loads that are created – Stnd Load Template
- Load mix group – Group that is used to determine what can or cannot be combined on a load – TV
- Use open loads – Controls what existing loads are allowed to be used – Any
- Create loads – Should the system create loads if it doesn&#39;t find one that matches the criteria? – Yes
- Allow shipment line split – Can a single line be split across multiple loads if the full line exceeds the load capacity? – No
- Validate volumetrics – Controls if the volumetric limits of the load template should be evaluated - No

Open the Edit Query for the template, and in the sorting table, add sorting on Load details – Order number – Ascending.

In the Break by grid, check the &#39;Break by&#39; box for the Load details – Order number record.

This will create one load per order number. Generally, this functionality is used to break on custom fields that have been extended onto the load line, such as Route, Tour, Run, etc.

# Process

Navigate to _Sales and Marketing_ _-_ _Common - Sales order - All sales orders_ and create a new sales order. Select customer US-007 and warehouse 62.

Add a line and specify item A0001, quantity 1. Click on Inventory – Reservation and reserve inventory to the line. Click on Release to warehouse in the Warehouse _-_ Actions section of the ribbon. A shipment will be created, and added to a new load, as there is no existing load containing load lines with this order number.

Create another line on the same sales order, for item A0002. Reserve the line and release the order to the warehouse again. The system will create a new shipment for the new line, but because of load building it will add that shipment and load line to the existing wave. Without load building enabled, a new load would have been created for the shipment as well.

Create a third line of the same sales order, for item M9200. Reserve the line and release the order to the warehouse. A new shipment will be created, and added to a new load, because the item failed the load mix group constraints. If a load mix group hadn&#39;t been specified on the load build template, then this shipment would have been added to the first load as well.
