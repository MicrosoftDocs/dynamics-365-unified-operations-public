# Wave template grouping

Wave template grouping enables the system to use [wave template](tasks/configure-wave-processing.md) setups to decide how to split released lines and assign them to new or existing waves based on criteria you define. This can be useful in warehouses where waves are created based on a certain criteria, but where managers prefer to create waves automatically rather than manually. This feature enables the system to add each newly released shipment to the first wave it finds with matching grouping-field values; if no matches are found, it will instead create a new wave for the new shipment.

<!-- KAMAYBAC: I revised this intro pretty heavily. Please review and confirm -->

## Enable the wave template grouping feature

Before you can use this feature, it must be enabled on your system. Administrators can use the [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) settings to check the feature status and enable it if needed. Here, the feature is listed as:

- **Module** - Warehouse management
- **Feature name** - Wave template grouping

<a name="set-up-template"></a>

## Set a wave template to use wave template grouping

To enable wave template grouping, set up your [wave template](tasks/configure-wave-processing.md) as follows:

1. Go to **Warehouse management > Setup > Waves > Wave templates**.
1. Select the wave template that you want to set up.<br>(If you're preparing to work through the demo using sample data, then select the **62 Shipping default**  template.)
1. Select **Edit** to put the page into edit mode.
1. On the **General** FastTab, make the following settings:
    - **Automate wave creation** - Set to **Yes**. (This feature only takes effect whe you use automatic wave creation. <!-- KAMAYBAC: Right? -->)
    - **Process wave at release to warehouse** - Set to **No**. <!-- KAMAYBAC: Why are we setting this? Is this required to use this feature? What effect does it have? Or is this setting only important for the upcoming demo? -->
1. Select **Edit query** to open the query-editor panel.
1. In the query panel, open the **Sorting** tab.
1. Review your sorting criteria and make sure you have a rule that includes the field you want to use to group your waves.<br>(If you're preparing to work through the demo using sample data, then add a row with **Table** "Shipments", **Derived table** "Shipments", **Field** "Carrier service", and **Search direction** "Ascending".)
1. Select **OK** to save your changes and close the query panel.
1. Select **Wave template grouping** to open the **Wave template grouping** page.
1. Select the **Group by**check box for each row that you want to use for grouping your order lines into waves as needed.<br>(If you're preparing to work through the demo using sample data, then mark the **Group by** check box for the **Carrier service** row.)
1. Close the **Wave template grouping** page.
1. Select **Save** to save your template.

## Try out the feature

This section provides a demo script that you can work through to get a feel for what this feature does and how to work with it.

### Enable sample data

To work through this demo using the sample records and values specified here, you must be on a system with the standard [demo data](../../fin-ops-core/dev-itpro/deployment/deploy-demo-environment.md) installed, and you must select the **USMF** legal entity before you begin.

You can also use this demo as guidance for how to use this feature when working on a production system, but then you must then substitute your own values, and you may be missing some types of required records that would otherwise be provided by the standard demo data.

### Demo: Wave template grouping

This demo illustrates how to use wave template grouping to automatically create multiple waves based on grouping criteria defined in a wave template. In this example, we'll set up the system to create one wave per carrier service.

1. Prepare your wave template as described in [Set a wave template to use wave template grouping](#set-up-template). Be sure to use the demo values suggested in that procedure if you will be working with demo data for this procedure. This setup will group your waves according to the carrier service set for each sales order.
1. Go to **Sales and marketing > Sales orders > All sales orders**.
1. Select **New** to create a new sales order.
1. The **Create sales order** panel opens. Make the following settings here:
    - On the **Customer** FastTab, set **Customer account** to "US-004".
    - On the **General** FastTab, set **Warehouse** to "62".
1. Select **OK** to create the new sales order and close the panel.
1. Your new sales order opens with the **Lines** tab showing. Go to the **Header** tab, expand the **Delivery** FastTab, and make the following settings in the **Transportation** section here:
    - **Shipping carrier** - Air cargo
    - **Carrier service** - Air
1. Go back to the **Lines** tab for your sales order and add a line to the **Sales order lines** table with the following values:
    - **Item number** - A0002
    - **Quantity** - 2
    - **Unit** - Pcs
1. Select the new order line, open the **Inventory** drop-down list and select **Reservation**.
1. The **Reservation** page opens. Select **Reserve lot** to reserve your selected line's full quantity in the warehouse.
1. Close the **Reservation** page to return to your sales order.
1. Open the **Warehouse** tab and select **Release to warehouse**. The system announces that it has created a new shipment and wave for this order. Note the wave number.
1. Go to **Warehouse management > Outbound Waves > Shipment Waves > All Waves**,  open the newly created wave, and note that the shipment has been added to it on the **Wave lines** FastTab.
1. Go back to **Sales and marketing > Sales orders > All sales orders** and create a second sales order, this time for **Customer account** "US-005" and **Warehouse** "62".
1. For this second sales order, go again to the **Header** tab, expand the **Delivery** FastTab, and make the following settings, this time to establish different transportation options:
    - **Shipping carrier** - Flower moving
    - **Carrier service** - STD
1. Go back to the **Lines** tab for your second sales order and add a line to the **Sales order lines** table with the following values:
    - **Item number** - A0001
    - **Quantity** - 1
    - **Unit** - Pcs
1. As before, reserve inventory for this order line and then release the order to warehouse. The system announces that it has created a new shipment and wave for this order. Note the wave number and notice that it is different from the first wave number.
1. Go to **Warehouse management > Outbound Waves > Shipment Waves > All Waves**,  open the second new wave, and note that the shipment has been added to it. A new wave was created for this shipment because it uses a different carrier service than the first sales order.
1. Go back to **Sales and marketing > Sales orders > All sales orders** and create a third sales order, this time for **Customer account** "US-006" and **Warehouse** "62".
1. For this third sales order, go again to the **Header** tab, expand the **Delivery** FastTab, and make the following settings, this time with the same transportation options as the first sales order:
    - **Shipping carrier** - Air cargo
    - **Carrier service** - Air
1. Go back to the **Lines** tab for your third sales order and add a line to the **Sales order lines** table with the following values:
    - **Item number** - A0002
    - **Quantity** - 1
    - **Unit** - Pcs
1. As before, reserve inventory for this order line and then release the order to warehouse. The system announces that it has created a new shipment and wave for this order. Note the wave number, which should be the same as the wave number for your first sales order.
1. Go to **Warehouse management > Outbound Waves > Shipment Waves > All Waves**,  open the combined wave, and note that it now has two shipments listed on the **Wave lines** FastTab. These shipments have been combined into the same wave because both of them are set to use the same carrier service.

<!-- KAMAYBAC: When I did this, I got a new wave each time, even though the carrier service was the same. I did it twice, same result. Is something missing here? -->
