# Wave template grouping

Wave template grouping enables the system to use [wave template](tasks/configure-wave-processing.md) setups to decide how to split released lines and assign them to new or existing waves based on criteria you define. This can be useful in warehouses where waves are created based on a certain criteria, but where managers prefer to create waves automatically rather than manually. This feature enables the system to add each newly released shipment to the first wave it finds with matching grouping-field values; if no matches are found, it will instead create a new wave for the new shipment.

## Enable the wave template grouping feature

Before you can use this feature, it must be enabled on your system. Administrators can use the [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) settings to check the feature status and enable it if needed. Here, the feature is listed as:

- **Module** - Warehouse management
- **Feature name** - Wave template grouping

<a name=*set-up-template*></a>

## Set a wave template to use wave template grouping

To enable wave template grouping, set up your [wave template](tasks/configure-wave-processing.md) as follows:

1. Go to **Warehouse management > Setup > Waves > Wave templates**.
1. Select the wave template that you want to set up.
    1. If you're preparing to work through the scenario using demo data, select the **62 Shipping default**  template.
1. Select **Edit** to put the page into edit mode.
1. On the **General** FastTab, make the following settings:
    - **Automate wave creation** - *Yes*
    - **Assign to open waves** - *Yes*
    - **Process wave at release to warehouse** - *No*
1. Select **Edit query** to open the query-editor panel.
1. In the query panel, select the **Sorting** tab.
1. Review your sorting criteria and make sure you have a rule that includes the field you want to use to group your waves.
    1. If you're preparing to work through the scenario using demo data, then add a row with the following:
        1. **Table** - *Shipments*
        1. **Derived table** - *Shipments*
        1. **Field** - *Carrier service*
            1. You may receive a popup message *Field Carrier service is not an index field. Do you want to add sorting on this?* Select **Yes**
        1. **Search direction** - *Ascending*
1. Select **OK** to save your changes and close the query panel.
1. In the Action Pane, select **Wave template grouping** to open the **Wave template grouping** page.
1. Select the **Group by** check box for each row that you want to use for grouping your order lines into waves as needed.
    1. If you're preparing to work through the scenario using demo data, then mark the **Group by** check box for the *Carrier service* row.
1. Select **Save**.
1. Close the **Wave template grouping** page.
1. Select **Save** to save your template.

## Scenario

This section provides a script that you can work through to get a feel for what this feature does and how to work with it.

### Enable sample data

To work through this demo using the sample records and values specified here, you must be on a system with the standard [demo data](../../fin-ops-core/dev-itpro/deployment/deploy-demo-environment.md) installed, and you must select the **USMF** legal entity before you begin.

You can also use this demo as guidance for how to use this feature when working on a production system, but then you must then substitute your own values, and you may be missing some types of required records that would otherwise be provided by the standard demo data.

### Scenario: Wave template grouping

This scenario illustrates how to use wave template grouping to automatically create multiple waves based on grouping criteria defined in a wave template. In this scenario, the wave template is set up in the system to create one wave per carrier service.

Prepare your wave template as described in [Set a wave template to use wave template grouping](#set-up-template). Be sure to use the demo values suggested in that procedure if you will be working with demo data for this procedure. This setup will group your waves according to the carrier service set for each sales order.

#### Create Sales Order 1

1. Go to **Sales and marketing > Sales orders > All sales orders**.
1. Select **New** to create a new sales order.
1. The **Create sales order** FlyOut opens. Enter the following:
    - On the **Customer** FastTab, set **Customer account** to *US-004*.
    - On the **General** FastTab, set **Warehouse** to *62*.
1. Select **OK** to create the new sales order and close the FlyOut.
1. Your new sales order opens with the **Lines** section tab showing. ***Make note of the sales order number***.
1. Select the **Header** section tab and expand the **Delivery** FastTab. Enter the following in the **Transportation** group:
    - **Shipping carrier** - *Air cargo*
    - **Carrier service** - *Air*
1. Select the **Lines** section tab.
1. Select *Add line* in the **Sales order lines** FastTab to add a line with the following values:
    - **Item number** - *A0002*
    - **Quantity** - *2*
1. Focus on the new order line, in the **Sales order lines** FastTab select **Inventory** then select *Reservation* from the list.
1. The **Reservation** page opens. Select **Reserve lot** to reserve your selected line's full quantity in the warehouse.
1. Close the **Reservation** page to return to your sales order.
1. In the Action Pane, select the **Warehouse** tab.
1. Select **Release to warehouse** from the *Actions* group.
1. An informational message displays with the shipment and wave for this order. Note the ***Wave ID*** number and the ***Shipment ID*** numbers.

#### View the Wave Created from Sales Order 1

1. Go to **Warehouse management > Outbound Waves > Shipment Waves > All Waves**
1. Select the *Wave ID* created from the sales order.
1. Select the wave ID to open the wave details.
1. Note that the shipment has been added to the **Wave lines** FastTab.

#### Create Sales Order 2

1. Go to **Sales and marketing > Sales orders > All sales orders**
1. Select **New** to create a new sales order.
1. The **Create sales order** FlyOut opens. Enter the following:
    - On the **Customer** FastTab, set **Customer account** to *US-005*.
    - On the **General** FastTab, set **Warehouse** to *62*.
1. Select **OK** to create the new sales order and close the FlyOut.
1. Your new sales order opens with the **Lines** section tab showing. ***Make note of the sales order number***.
1. Select the **Header** section tab and expand the **Delivery** FastTab. Enter the following in the **Transportation** group:
    - **Shipping carrier** - *Flower moving*
    - **Carrier service** - *Std*
1. Select the **Lines** section tab.
1. Select *Add line* in the **Sales order lines** FastTab to add a line with the following values:
    - **Item number** - *A0001*
    - **Quantity** - *1*
1. Focus on the new order line, in the **Sales order lines** FastTab select **Inventory** then select *Reservation* from the list.
1. The **Reservation** page opens. Select **Reserve lot** to reserve your selected line's full quantity in the warehouse.
1. Close the **Reservation** page to return to your sales order.
1. In the Action Pane, select the **Warehouse** tab.
1. Select **Release to warehouse** from the *Actions* group.
1. An informational message displays with the shipment and wave for this order. Note the ***Wave ID*** number and the ***Shipment ID*** numbers. Note that the *Wave* number is different from the first sales order's wave number.

#### View the Wave Created from Sales Order 2

1. Go to **Warehouse management > Outbound Waves > Shipment Waves > All Waves**
1. Select the *Wave ID* created from the second sales order.
1. Select the wave ID to open the wave details.
1. Note that the shipment has been added to the **Wave lines** FastTab.
1. A new wave was created for this shipment because it uses a different carrier service than the first sales order.

#### Create Sales Order 3

1. Go to **Sales and marketing > Sales orders > All sales orders**
1. Select **New** to create a new sales order.
1. The **Create sales order** FlyOut opens. Enter the following:
    - On the **Customer** FastTab, set **Customer account** to *US-006*.
    - On the **General** FastTab, set **Warehouse** to *62*.
1. Select **OK** to create the new sales order and close the FlyOut.
1. Your new sales order opens with the **Lines** section tab showing. ***Make note of the sales order number***.
1. Select the **Header** section tab and expand the **Delivery** FastTab. Enter the following in the **Transportation** group:
    - **Shipping carrier** - *Air Cargo*
    - **Carrier service** - *Air*
1. Select the **Lines** section tab.
1. Select *Add line* in the **Sales order lines** FastTab to add a line with the following values:
    - **Item number** - *A0001*
    - **Quantity** - *1*
1. Focus on the new order line, in the **Sales order lines** FastTab select **Inventory** then select *Reservation* from the list.
1. The **Reservation** page opens. Select **Reserve lot** to reserve your selected line's full quantity in the warehouse.
1. Close the **Reservation** page to return to your sales order.
1. In the Action Pane, select the **Warehouse** tab.
1. Select **Release to warehouse** from the *Actions* group.
1. An informational message displays with the shipment and wave for this order. Note the ***Wave ID*** number and the ***Shipment ID*** numbers. The shipment has been been assigned to the existing *Wave* from the first sales order.

#### View the Wave for Sales Orders 1 & 3

1. Go to **Warehouse management > Outbound Waves > Shipment Waves > All Waves**
1. Select the *Wave ID* created from the third sales order.
1. Select the wave ID to open the wave details.
1. Note that the shipment has been added to the **Wave lines** FastTab along with the first sales order's shipment.
