---
title: Wave template grouping
description: Wave template grouping enables the system to use wave template setups to determine, based on criteria that you define and assign them to new or existing waves.
author: Mirzaab
ms.author: mirzaab
ms.topic: article
ms.date: 07/01/2020
ms.custom:
ms.reviewer: kamaybac
ms.search.form: WHSWaveTableListPage, WHSWaveTemplateTable
---

# Wave template grouping

[!include [banner](../includes/banner.md)]

Wave template grouping enables the system to use [wave template](tasks/configure-wave-processing.md) setups to determine, based on criteria that you define, how it should split released lines and assign them to new or existing waves. This feature can be useful in warehouses where waves are created based on specific criteria, but where managers prefer to create waves automatically instead of manually. It enables the system to add each newly released shipment to the first wave that it finds that has matching grouping field values. If no match is found, the system creates a new wave for the new shipment.

> [!IMPORTANT]
> Wave template grouping isn't supported for the work types *production raw material picking* or *Kanban picking*. This is because wave grouping is based on shipments and these work types don't use shipments.

## Turn on the Wave template grouping feature

Before you can use the *Wave template grouping* feature, it must be turned on for your system. Admins can use the [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) settings to check the status of the feature and turn it on if it's required. In the **Feature management** workspace, the feature is listed in the following way:

- **Module:** *Warehouse management*
- **Feature name:** *Wave template grouping*

## <a name="set-up-template"></a>Set a wave template to use wave template grouping

To make wave template grouping available, follow these steps to set up your [wave template](tasks/configure-wave-processing.md).

1. Go to **Warehouse management \> Setup \> Waves \> Wave templates**.
1. In the left pane, select the wave template to set up. If you're preparing to work through the scenario later in this article by using demo data, select the **62 Shipping default** template.
1. Select **Edit** to put the page into edit mode.
1. On the **General** FastTab, set the following values:

    - **Automate wave creation:** *Yes*
    - **Assign to open waves:** *Yes*
    - **Process wave at release to warehouse:** *No*

1. On the Action Pane, select **Edit query** to open the query dialog box.
1. In the query dialog box, on the **Sorting** tab, review the sorting criteria, and make sure that there is a rule that includes the field that you want to use to group your waves.

    If you're preparing to work through the scenario by using demo data, add a row that has the following values:

    - **Table:** *Shipments*
    - **Derived table:** *Shipments*
    - **Field:** *Carrier service*

        > [!NOTE]
        > After you select this value, you might receive the following message: "Field Carrier service is not an index field. Do you want to add sorting on this?" Select **Yes** to add sorting.

    - **Search direction:** *Ascending*

1. Select **OK** to save your changes and close the query dialog box.
1. On the Action Pane, select **Wave template grouping**.
1. On the **Wave template grouping** page, select the **Group by** check box for each row that you want to use to group your order lines into waves, as required. If you're preparing to work through the scenario by using demo data, select the **Group by** check box for the *Carrier service* row.
1. Select **Save**.
1. Close the **Wave template grouping** page.
1. Select **Save** to save your template.

## Scenario

This section provides a script that you can work through to learn what this feature does and how to work with it.

### Make sample data available

To work through this scenario by using the sample records and values that are specified here, you must be on a system where the standard [demo data](../../fin-ops-core/fin-ops/get-started/demo-data.md) is installed. Additionally, you must select the **USMF** legal entity before you begin.

You can also use this scenario as guidance for using the feature when you work on a production system. However, in that case, you must substitute your own values, and you might be missing some types of required records that the standard demo data provides.

### Scenario: Wave template grouping

This scenario shows how to use wave template grouping to automatically create multiple waves, based on grouping criteria that are defined in a wave template. In this scenario, the wave template is set up in the system to create one wave per carrier service.

Before you begin, prepare your wave template as described in the [Set a wave template to use wave template grouping](#set-up-template) section earlier in this article. If you will be working with demo data for this scenario, be sure to use the demo data values that are suggested in that procedure. This setup will group your waves according to the carrier service that is set for each sales order.

#### Create sales order 1

1. Go to **Sales and marketing \> Sales orders \> All sales orders**.
1. Select **New** to create a sales order.
1. In the **Create sales order** dialog box, set the following values:

    - On the **Customer** FastTab, set the **Customer account** field to *US-004*.
    - On the **General** FastTab, set the **Warehouse** field to *62*.

1. Select **OK** to create the sales order and close the **Create sales order** dialog box.
1. The new sales order is opened in the **Lines** view. Make a note of the sales order number.
1. Switch to the **Header** view.
1. On the **Delivery** FastTab, in the **Transportation** section, set the following values:

    - **Shipping carrier:** *Air cargo*
    - **Carrier service:** *Air*

1. Switch back to the **Lines** view.
1. In the **Sales order lines** section, select **Add line** to add a line to the grid.
1. On the new line, set the following values:

    - **Item number:** *A0002*
    - **Quantity:** *2*

1. Select the new order line, and then, on the **Inventory** menu above the grid, select **Reservation**.
1. On the **Reservation** page, on the Action Pane, select **Reserve lot** to reserve the full quantity of the selected line in the warehouse.
1. Close the **Reservation** page to return to the sales order.
1. On the Action Pane, on the **Warehouse** tab, in the **Actions** group, select **Release to warehouse**.
1. You receive an informational message that shows the shipment and wave for this order. Make a note of the wave ID number and the shipment ID numbers.

#### View the wave that was created from sales order 1

1. Go to **Warehouse management \> Outbound waves \> Shipment waves \> All waves**.
1. Select the wave ID that was created from the sales order.
1. Select the wave ID link to open the wave details page.
1. Notice that the shipment has been added to the **Wave lines** FastTab.

#### Create sales order 2

1. Go to **Sales and marketing \> Sales orders \> All sales orders**.
1. Select **New** to create a sales order.
1. In the **Create sales order** dialog box, set the following values:

    - On the **Customer** FastTab, set the **Customer account** field to *US-005*.
    - On the **General** FastTab, set the **Warehouse** field to *62*.

1. Select **OK** to create the sales order and close the **Create sales order** dialog box.
1. The new sales order is opened in the **Lines** view. Make a note of the sales order number.
1. Switch to the **Header** view.
1. On the **Delivery** FastTab, in the **Transportation** section, set the following values:

    - **Shipping carrier:** *Flower moving*
    - **Carrier service:** *Std*

1. Switch back to the **Lines** view.
1. In the **Sales order lines** section, select **Add line** to add a line to the grid.
1. On the new line, set the following values:

    - **Item number:** *A0001*
    - **Quantity:** *1*

1. Select the new order line, and then, on the **Inventory** menu above the grid, select **Reservation**.
1. On the **Reservation** page, on the Action Pane, select **Reserve lot** to reserve the full quantity of the selected line in the warehouse.
1. Close the **Reservation** page to return to the sales order.
1. On the Action Pane, on the **Warehouse** tab, in the **Actions** group, select **Release to warehouse**.
1. You receive an informational message that shows the shipment and wave for this order. Make a note of the wave ID number and the shipment ID numbers. Notice that the wave ID differs from the wave ID of the first sales order.

#### View the wave that was created from sales order 2

1. Go to **Warehouse management \> Outbound waves \> Shipment waves \> All waves**.
1. Select the wave ID that was created from the second sales order.
1. Select the wave ID link to open the wave details page.
1. Notice that the shipment has been added to the **Wave lines** FastTab.

A new wave was created for this shipment, because it uses a different carrier service than the first sales order.

#### Create sales order 3

1. Go to **Sales and marketing \> Sales orders \> All sales orders**.
1. Select **New** to create a sales order.
1. In the **Create sales order** dialog box, set the following values:

    - On the **Customer** FastTab, set the **Customer account** field to *US-006*.
    - On the **General** FastTab, set the **Warehouse** field to *62*.

1. Select **OK** to create the sales order and close the **Create sales order** dialog box.
1. The new sales order is opened in the **Lines** view. Make a note of the sales order number.
1. Switch to the **Header** view.
1. On the **Delivery** FastTab, in the **Transportation** section, set the following values:

    - **Shipping carrier:** *Air Cargo*
    - **Carrier service:** *Air*

1. Switch back to the **Lines** view.
1. In the **Sales order lines** section, select **Add line** to add a line to the grid.
1. On the new line, set the following values:

    - **Item number:** *A0001*
    - **Quantity:** *1*

1. Select the new order line, and then, on the **Inventory** menu above the grid, select **Reservation**.
1. On the **Reservation** page, on the Action Pane, select **Reserve lot** to reserve the full quantity of the selected line in the warehouse.
1. Close the **Reservation** page to return to the sales order.
1. On the Action Pane, on the **Warehouse** tab, in the **Actions** group, select **Release to warehouse**.
1. You receive an informational message that shows the shipment and wave for this order. Make a note of the wave ID number and the shipment ID numbers. The shipment has been assigned to the existing wave from the first sales order.

#### View the wave for sales orders 1 and 3

1. Go to **Warehouse management \> Outbound waves \> Shipment waves \> All waves**.
1. Select the wave ID that was created from the third sales order.
1. Select the wave ID link to open the wave details page.
1. Notice that the shipment has been added to the **Wave lines** FastTab, together with the shipment for the first sales order.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]