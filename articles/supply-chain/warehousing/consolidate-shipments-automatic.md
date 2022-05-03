---
# required metadata

title: Consolidate shipments released to the warehouse using automatic release of sales orders
description: This topic presents a scenario where multiple orders are released to the warehouse in the same automated release-to-warehouse periodic procedure.
author: Mirzaab
ms.date: 05/12/2020
ms.topic: article
ms.prod:
ms.technology:

# optional metadata

ms.search.form: WHSShipConsolidationPolicy, WHSShipConsolidationWorkbench, WHSFilterGroupTable, WHSShipmentConsolidation, WHSFilterGenerallyAvail
# ROBOTS:
audience: Application User
# ms.devlang:
ms.reviewer: kamaybac
# ms.tgt_pltfrm:
# ms.custom:
ms.search.region: Global
# ms.search.industry:
ms.author: mirzaab
ms.search.validFrom: 2020-05-01
ms.dyn365.ops.version: 10.0.3

---

# Consolidate shipments released to the warehouse using automatic release of sales orders

[!include [banner](../includes/banner.md)]

This topic presents a scenario where multiple orders are released to the warehouse in the same automated release-to-warehouse periodic procedure. The orders will automatically be consolidated into shipments, based on rules that are defined as shipment consolidation policies.

During the scenario, you will create sets of sales orders and release each set to the warehouse. You will then review the shipments that are created or updated during shipment consolidation, based on the configured policies.

## Make demo data available

The scenario in this topic references values and records that are included in the standard demo data that is provided for Microsoft Dynamics 365 Supply Chain Management. If you want to use the values that are provided here as you do the exercises, be sure to work in an environment where the demo data is installed, and set the legal entity to **USMF** before you begin.

## Set up shipment consolidation policies and product filters

The scenario that is described here assumes that you've already turned on the feature, done the exercises in [Configure shipment consolidation policies](configure-shipment-consolidation-policies.md), and created the policies and other records that are described there. Be sure to do those exercises before you continue with this scenario.

## Create the sales orders for this scenario

Start by creating a collection of sales orders that you can work with. You must work with a warehouse that is enabled for advanced warehouse (WMS) processes. Unless a different warehouse is explicitly mentioned, that same warehouse must be used for each of the following sets of orders.

Go to **Accounts receivable \> Orders \> All sales orders**, and create a collection of sales orders that have the settings that are described in the following subsections.

### Create order set 1

#### Sales order 1-1

1. Create a sales order that has the following settings:

    - **Customer account:** *US-001*
    - **Mode of delivery:** *Airwa-Air*

1. Add an order line that has the following settings:

    - **Item number:** *A0001* (an item that no **Code 4** filter is assigned to)
    - **Quantity:** *1.00*

#### Sales order 1-2

1. Create a sales order that has the following settings:

    - **Customer account:** *US-001*
    - **Mode of delivery:** *Airwa-Air*

1. Add an order line that has the following settings:

    - **Item number:** *A0001* (an item that no **Code 4** filter is assigned to)
    - **Quantity:** *1.00*

#### Sales order 1-3

1. Create a sales order that has the following settings:

    - **Customer account:** *US-001*
    - **Mode of delivery:** *10*

1. Add an order line that has the following settings:

    - **Item number:** *A0001* (an item that no **Code 4** filter is assigned to)
    - **Quantity:** *1.00*

1. Add a second order line that has the following settings:

    - **Item number:** *A0002* (an item that no **Code 4** filter is assigned to)
    - **Quantity:** *1.00*
    - **Mode of delivery:** *Airwa-Air*

### Create order set 2

#### Sales orders 2-1 and 2-2

1. Create two identical sales orders that have the following settings:

    - **Customer account:** *US-002*

1. Add an order line that has the following settings:

    - **Item number:** *M9200* (an item where the **Code 4** filter is set to *Flammable*)
    - **Quantity:** *1.00*

1. Add a second order line that has the following settings:

    - **Item number:** *M9201* (an item where the **Code 4** filter is set to *Explosive*)
    - **Quantity:** *1.00*
    - **Mode of delivery:** *Airwa-Air*

### Create order set 3

#### Sales order 3-1

1. Create a sales order that has the following settings:

    - **Customer account:** *US-002*

1. Add an order line that has the following settings:

    - **Item number:** *M9200* (an item where the **Code 4** filter is set to *Flammable*)
    - **Quantity:** *1.00*

1. Add a second order line that has the following settings:

    - **Item number:** *M9201* (an item where the **Code 4** filter is set to *Explosive*)
    - **Quantity:** *1.00*
    - **Mode of delivery:** *Airwa-Air*

> [!NOTE]
> This order is identical to the two orders that you created for order set 2. However, it's listed as its own order set because you will release it separately later in this scenario.

### Create order set 4

#### Sales order 4-1

1. Create a sales order that has the following settings:

    - **Customer account:** *US-001*
    - **Customer requisition:** *1*

1. Add an order line that has the following settings:

    - **Item number:** *A0001* (an item that no **Code 4** filter is assigned to)
    - **Quantity:** *1.00*

### Create order set 5

#### Sales orders 5-1 and 5-2

1. Create two identical sales orders that have the following settings:

    - **Customer account:** *US-001*
    - **Customer requisition:** *2*

1. Add an order line that has the following settings:

    - **Item number:** *A0001* (an item that no **Code 4** filter is assigned to)
    - **Quantity:** *1.00*

#### Sales order 5-3

1. Create a sales order that has the following settings:

    - **Customer account:** *US-001*
    - **Customer requisition:** *1*

1. Add an order line that has the following settings:

    - **Item number:** *A0001* (an item that no **Code 4** filter is assigned to)
    - **Quantity:** *1.00*

### Create order set 6

#### Sales orders 6-1 and 6-2

1. Create two identical sales orders that have the following settings:

    - **Customer account:** *US-003*
    - **Customer requisition:** *2*

1. Add an order line that has the following settings:

    - **Item number:** *A0001* (an item that no **Code 4** filter is assigned to)
    - **Quantity:** *1.00*

#### Sales orders 6-3 and 6-4

1. Create two identical sales orders that have the following settings:

    - **Customer account:** *US-004*
    - **Customer requisition:** *1*

1. Add an order line that has the following settings:

    - **Item number:** *A0001* (an item that no **Code 4** filter is assigned to)
    - **Quantity:** *1.00*

#### Sales orders 6-5 and 6-6

1. Create two identical sales orders that have the following settings:

    - **Customer account:** *US-007*
    - **Site:** *6*
    - **Warehouse:** *61*
    - **Pool:** *ShipCons*

1. Add an order line that has the following settings:

    - **Item number:** *A0001* (an item that no **Code 4** filter is assigned to)
    - **Quantity:** *1.00*

#### Sales orders 6-7 and 6-8

1. Create two identical sales orders that have the following settings:

    - **Customer account:** *US-007*
    - **Site:** *6*
    - **Warehouse:** *61*
    - **Pool:** Leave this field blank.

1. Add an order line that has the following settings:

    - **Item number:** *A0001* (an item that no **Code 4** filter is assigned to)
    - **Quantity:** *1.00*

## Automatic release of sales orders to the warehouse

For each set of sales orders that you created earlier, you will complete a procedure for automatic release to the warehouse. In each case, you will work through the [basic release-to-warehouse procedure](#release-procedure) that is provided here.

### <a name="release-procedure"></a>Basic release-to-warehouse procedure

For each set of sales orders that you created earlier, you will complete the three procedures that are outlined in the following subsections.

#### Update the wave template that will be used during release

1. Go to **Warehouse management \> Setup \> Waves \> Wave templates**.
1. Set the **Wave template type** field to *Shipping*.
1. Find and select the wave template that is associated with the warehouse that you used in the order sets that you created for this scenario. For example, if you used warehouse *24*, select the **24 Shipping Default** wave template. If you used warehouse *61*, select the **61 Shipping** wave template.
1. On the Action Pane, select **Edit**.
1. Set the **Process wave at release to warehouse** option to *No*.

#### Release to the warehouse

1. Go to **Warehouse management \> Release to warehouse \> Automatic release of sales orders**.
1. Set the **Quantity to release** field to *All*.
1. On the **Records to include** FastTab, select **Filter** to open the query dialog box.
1. On the **Range** tab, select **Add** to add a row that has the following settings to the grid:

    - **Table:** *Sales order*
    - **Derived table:** *Sales order*
    - **Field:** *Sales order*
    - **Criteria:** Enter a comma-separated list of the sales order numbers from the desired order set.

1. Select **OK** to save your query.
1. Select **OK** to start the *Automatic release to warehouse* procedure.

#### Review the shipment that is created or updated

1. Go to **Warehouse management \> Shipments \> All shipments**.
1. Find and select the required shipment.
1. If a consolidation policy was used when the shipment was created or updated, you should see it in the **Shipment consolidation policy** field.

### Release sales orders from order set 1

Follow the [basic release-to-warehouse procedure](#release-procedure) to release the sales orders from order set 1.

When you've finished, you should see that two shipments were created:

- The first shipment contains three lines and was created by using the *CustomerMode* shipment consolidation policy.
- The second shipment, which doesn't use the *Airways* transportation mode of delivery, was created by using the *CustomerOrderNo* shipment consolidation policy.

### Release sales orders from order set 2

Follow the [basic release-to-warehouse procedure](#release-procedure) to release the sales orders from order set 2.

When you've finished, you should see that three shipments were created:

- The first shipment contains *Flammable* items.
- Each of the other two shipments contains one line that has the *Explosive* item.

### Release sales orders from order set 3

Follow the [basic release-to-warehouse procedure](#release-procedure) to release the sales orders from order set 3.

When you've finished, you should see that the following actions occurred:

- One existing shipment (the shipment that was created when order set 2 was released to the warehouse) was updated. A line that has the *Flammable* item was added.
- One new shipment was created that contains the *Explosive* item.

### Release sales orders from order set 4

Follow the [basic release-to-warehouse procedure](#release-procedure) to release the sales orders from order set 4.

When you've finished, you should see that one existing shipment (where the **Customer requisition** field is set to *1*) was updated. One new line was added to it.

### Release sales orders from order set 5

Follow the [basic release-to-warehouse procedure](#release-procedure) to release the sales orders from order set 5.

When you've finished, you should see that the following actions occurred:

- One existing shipment (where the **Customer requisition** field is set to *1*) was updated. A line from sales order 5-3 (where the **Customer requisition** field is set to *1*) was added to it.
- One new shipment was created, where lines from sales orders 5-1 and 5-2 are grouped into one shipment.

### Release sales orders from order set 6

Follow the [basic release-to-warehouse procedure](#release-procedure) to release the sales orders from order set 6.

When you've finished, you should see that four shipments were created:

- Lines from two orders for customer *US-003* were grouped into one shipment by using the *Order pool* shipment consolidation policy.
- Lines from two orders for customer *US-004* were grouped into one shipment by using the *Order pool* shipment consolidation policy.
- Lines from sales orders 6-5 and 6-6 for customer *US-007* were grouped into one shipment by using the *Order pool* shipment consolidation policy.
- Lines from sales orders 6-7 and 6-8 for customer *US-007* were grouped into one shipment by using the *CrossOrder* shipment consolidation policy.

## Additional resources

- [Shipment consolidation policies](about-shipment-consolidation-policies.md)
- [Configure shipment consolidation policies](configure-shipment-consolidation-policies.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]