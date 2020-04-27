---
# required metadata

title: Consolidate shipments using shipment consolidation policies
description: This topic provides an overview of functionality that provides use of shipment consolidation policies.
author: GarmMSFT
manager: tfehr
ms.date: 04/23/2020
ms.topic: article
ms.prod:
ms.service: dynamics-ax-applications
ms.technology:

# optional metadata

ms.search.form: WHSShipConsolidationPolicy, WHSShipConsolidationWorkbench
# ROBOTS:
audience: Application User
# ms.devlang:
ms.reviewer: kamaybac
ms.search.scope: Core, Operations
# ms.tgt_pltfrm:
# ms.custom:
ms.search.region: Global
# ms.search.industry:
ms.author: v-olbara
ms.search.validFrom: 2020-04-23
ms.dyn365.ops.version: 10.0.3

---

# Consolidate shipments when released to warehouse by automatic release of sales orders

[!include [banner](../includes/banner.md)]

This topic presents a scenario where multiple orders are released to the warehouse within the same automated release-to-warehouse periodic procedure. They will be consolidated into shipments automatically based on rules defined as shipment consolidation policies.

During the scenario, you will create sets of sales orders, release each of them to the warehouse, and review shipments that will be created or updated during shipment consolidation according to the configured policies.  

## Enable demo data

Each of the scenarios in this topic reference values and records included in the standard demo data provided for Supply Chain Management. If you'd like to run the exercises using the values provided here, be sure to work on an environment with the demo data installed, and set the legal entity to **USMF** before you begin.

## Set up shipment consolidation policies and product filters

The scenario described here assumes that you have already done the exercises and created the records described in [Configure shipment consolidation policies](configure-shipment-consolidation-policies.md). Please do those exercises before continuing with this scenario.

## Create the sales orders for this scenario

Start by creating a collection of sales orders that you can work with. You must work with a warehouse that is enabled for advanced warehouse (WHS) processes, and the same warehouse must be used for each of the following sets of orders unless another warehouse is explicitly mentioned.

<!-- KFM: Should users set a **Warehouse** for each of the sales orders created here? If so, we should specify that for each of them. We should be able to specify a particular warehouse that is already set up correctly in the standard demo data -->

<!-- KFM: Throughout this section we refer to item A0001 and A0002 as having no Code 4, while items D0001 and D0002 have Code 4 values. However, on my demo setup, I could only set Code 4 for items A0001 and A0002. The setting is disabled for D0001 and D0002. Therefore, the "Configure shipment consolidation policies" topic describes making this setting for items A0001 and A0002 (not D000x). We need to align this scenario with that one and with the actual USMF demo data people will have. (Or we need to add steps here for how to enable this setting for the D000x items.) -->

<!-- KFM: We are never reserving the inventory for the order lines in this topic, but we do in one of the others. Should we also do that here? -->

### Create order set 1

1. Go to **Accounts receivable > Orders > All sales orders** and create a new sales order with the following settings:

    - **Customer account** - *US-001*
    - **Mode of delivery** - *Airwa-Air*

1. Add an order line with the following settings to the sales order you just created:

    - **Item number** - *A0001* (an item without a **Code 4** filter assigned)
    - **Quantity** - *1.00*

1. Create a second sales order with the following settings:

    - **Customer account** - *US-001*
    - **Mode of delivery** - *Airwa-Air*

1. Add an order line with the following settings to the second sales order:

    - **Item number** - *A0001* (an item without a **Code 4** filter assigned)
    - **Quantity** - *1.00*

1. Create a third sales order with the following settings:

    - **Customer account** - *US-001*
    - **Mode of delivery** - *10*
    - **Customer requisition** - *1*

1. Add an order line with the following settings to the third sales order you just created:

    - **Item number** - *A0001* (an item without a **Code 4** filter assigned)
    - **Quantity** - *1.00*

1. Add a second order line with the following settings to the third sales order:

    - **Item number** - *A0002* (an item without a **Code 4** filter assigned)
    - **Quantity** - *1.00*
    - **Mode of delivery** - *Airwa-Air*


1. Add the following two order lines to the third sales order:

    - Order line 1:
        - **Item number** - *A0001* (an item without a **Code 4** filter assigned)
        - **Quantity** - *1.00*

    - Order line 2:
        - **Item number** - *A0002* (an item without a **Code 4** filter assigned)
        - **Quantity** - *1.00*
        - **Mode of delivery** - *Airwa-Air*

### Create order set 2

1. Go to **Accounts receivable > Orders > All sales orders** and create a new sales order with the following settings:

    - **Customer account** - *US-002*

1. Add the following two order lines to the sales order you just created:

    - Order line 1:
        - **Item number** - *D0001* (an item with its **Code 4** filter set to *Flammable*)
        - **Quantity** - *1.00*

    - Order line 2:
        - **Item number** - *D0002* (an item with its **Code 4** filter set to *Explosive*)
        - **Quantity** - *1.00*

1. Repeat this procedure to create a second sales order that is identical to this one.

### Create order set 3

1. Go to **Accounts receivable > Orders > All sales orders** and create a new sales order with the following settings:

    - **Customer account** - *US-002*

1. Add the following two order lines to the sales order you just created:

    - Order line 1:
        - **Item number** - *D0001* (an item with its **Code 4** filter set to *Flammable*)
        - **Quantity** - *1.00*

    - Order line 2:
        - **Item number** - *D0002* (an item with its **Code 4** filter set to *Explosive*)
        - **Quantity** - *1.00*

<!-- KFM: This order is identical to the two created in set 2. Is that intentional? If so, why not just create three orders in set 2 and drop this one? -->

### Create order set 4

1. Go to **Accounts receivable > Orders > All sales orders** and create a new sales order with the following settings:

    - **Customer account** - *US-001*
    - **Customer requisition** - *1*

1. Add an order line with the following settings to the sales order you just created:

    - **Item number** - *A0001* (an item without a **Code 4** filter assigned)
    - **Quantity** - *1.00*

### Create order set 5

1. Go to **Accounts receivable > Orders > All sales orders** and create a new sales order with the following settings:

    - **Customer account** - *US-001*
    - **Customer requisition** - *2*

1. Add an order line with the following settings to the sales order you just created:

    - **Item number** - *A0001* (an item without a **Code 4** filter assigned)
    - **Quantity** - *1.00*

1. Repeat the previous two steps to create a second sales order that is identical to the first one.

1. Create a third sales order with the following settings:

    - **Customer account** - *US-001*
    - **Customer requisition** - *1*

1. Add an order line with the following settings to the third sales order:

    - **Item number** - *A0001* (an item without a **Code 4** filter assigned)
    - **Quantity** - *1.00*

### Create order set 6

1. Go to **Accounts receivable > Orders > All sales orders** and create a new sales order with the following settings:

    - **Customer account** - *US-003*

1. Add an order line with the following settings to the sales order you just created:

    - **Item number** - *A0001* (an item without a **Code 4** filter assigned)
    - **Quantity** - *1.00*

1. Repeat the previous two steps to create a second sales order that is identical to the first one.

1. Create a third sales order with the following settings:

    - **Customer account** - *US-004*

1. Add an order line with the following settings to the third sales order:

    - **Item number** - *A0001* (an item without a **Code 4** filter assigned)
    - **Quantity** - *1.00*

1. Repeat the previous two steps to create a fourth sales order that is identical to the third one.

1. Create a fifth sales order with the following settings:

    - **Customer account** - *US-007*
    - **Site** - *6*
    - **Warehouse** - *61*
    - **Pool** - *ShipCons*

1. Add an order line with the following settings to the fifth sales order:

    - **Item number** - *A0001* (an item without a **Code 4** filter assigned)
    - **Quantity** - *1.00*

1. Repeat the previous two steps to create a sixth sales order that is identical to the fifth one.

1. Create a seventh sales order with the following settings:

    - **Customer account** - *US-007*
    - **Site** - *6*
    - **Warehouse** - *61*
    - **Pool** - (leave empty)

1. Add an order line with the following settings to the fifth sales order:

    - **Item number** - *A0001* (an item without a **Code 4** filter assigned)
    - **Quantity** - *1.00*

1. Repeat the previous two steps to create an eighth sales order that is identical to the seventh one.

## Automatic release of sales orders to the warehouse

For this scenario, you will run an automatic release to warehouse procedure for each of the sets of sales orders you created previously. In each case, you'll work through the process outlined in the [basic release to warehouse procedure](#release-procedure) provided here.

<a name="release-procedure"></a>

### The basic release to warehouse procedure

For each set of sales orders you created earlier, you'll work through the three procedures outlined below.

#### Update the wave template that will be used during releasing

1. Go to **Warehouse management > Setup > Waves > Wave templates**.
1. Set the **Wave template type** to *Shipping*.
1. Find and select the wave template that is associated with the warehouse that you used in the order sets you created for this scenario. For example, if you used warehouse **24**, select the **24 Shipping Default** wave template. If you used warehouse **61**, select the **61 Shipping** wave template.
1. Select **Edit** on the action pane and then set **Process wave at release to warehouse** to *No*.

#### Release to warehouse

1. Go to **Warehouse management > Release to warehouse > Automatic release of sales orders**.
1. Set **Quantity to release** to *All*.
1. Expand the **Records to include** FastTab and select **Filter** to open the query pane.
1. On the **Range** tab, select **Add** to add a new row to the table and make the following settings for it:
    - **Table** - <!-- KFM: What should this be? -->
    - **Derived table** - <!-- KFM: What should this be? -->
    - **Field** - *Sales order* <!-- KFM: Assuming this is table "Sales order", I see two different fields with this name here. Which one should I pick? -->
    - **Criteria** -Enter sales order numbers from the desired order set. <!-- KFM: Which ones, all of them? Should we have taken note of the sales order numbers as we made them? Comma-separated? -->
1. Select **OK** to save your query.
1. Select **OK** to launch the *automatic release to warehouse* procedure.

#### Review the created or updated shipment

1. Go to **Warehouse management > Shipments > All shipments**.
1. Find and select the required shipment.
1. If a consolidation policy was used during shipment creation or update, you can find it in the **Shipment consolidation policy** field.

### Release sales orders from Order set 1

Follow the [basic release to warehouse procedure](#release-procedure) to release the sales orders from order set one.

When your done, you should see that two shipments were created:

- The first shipment contains three lines and was created using the *CustomerMode* shipment consolidation policy.
- The second shipment (without the *Airways* transportation mode of delivery) is created using the *CustomerOrderNo* shipment consolidation policy.

### Release sales orders from Order set 2

Follow the [basic release to warehouse procedure](#release-procedure) to release the sales orders from order set two.

When your done, you should see that three shipments were created:

- The first shipment contains *Flammable* items.
- Each of the other two shipments contains one line with the *Explosive* item.

### Release sales orders from Order set 3

Follow the [basic release to warehouse procedure](#release-procedure) to release the sales orders from order set three.

When your done, you should see that:

- One existing shipment was updated (the one that was created as a result of order set 2 release to warehouse). A line with the *Flammable* item was added.
- One new shipment was created. It contains the *Explosive* item.

### Release sales orders from Order set 4

Follow the [basic release to warehouse procedure](#release-procedure) to release the sales orders from order set four.

When your done, you should see that one existing shipment (where **Customer requisition** = *1*) was updated to have one new line added to it.

### Release sales orders from Order set 5

Follow the [basic release to warehouse procedure](#release-procedure) to release the sales orders from order set five.

When your done, you should see that:

- One existing shipment (where **Customer requisition** = *1*) was updated. It now has a line from sales order 5-3 (with **Customer requisition** = *1*) added to it.
- One new shipment was created, where lines from sales orders 5-1 and 5-2 are grouped into one shipment.

### Release sales orders from Order set 6

Follow the [basic release to warehouse procedure](#release-procedure) to release the sales orders from order set six.

When your done, you should see that four shipments were created:

- Lines from two orders for customer *US-003* are grouped into one shipment using the *Order pool* shipment consolidation policy;
- Lines from two orders for customer *US-004* are grouped into one shipment using the *Order pool* shipment consolidation policy;
- Lines from sales orders 5 and 6 for customer *US-007* are grouped into one shipment using the *Order pool* shipment consolidation policy;
- Lines from sales orders 7 and 8 for customer *US-007* are grouped into one shipment using the *CrossOrder* shipment consolidation policy.

## Related topics and scenarios

- [About shipment consolidation policies](about-shipment-consolidation-policies.md)  
- [Configure shipment consolidation policies](configure-shipment-consolidation-policies.md)
- [Consolidate shipments](consolidate-shipments.md)
