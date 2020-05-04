---
# required metadata

title: Consolidate shipments using shipment consolidation policies
description: This topic provides an overview of functionality that provides use of shipment consolidation policies.
author: GarmMSFT
manager: tfehr
ms.date: 05/01/2020
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
ms.search.validFrom: 2020-05-01
ms.dyn365.ops.version: 10.0.3

---

# Consolidate shipments when released to warehouse by automatic release of sales orders

[!include [banner](../includes/banner.md)]

This topic presents a scenario where multiple orders are released to the warehouse within the same automated release-to-warehouse periodic procedure. They will be consolidated into shipments automatically based on rules defined as shipment consolidation policies.

During the scenario, you will create sets of sales orders, release each of them to the warehouse, and review shipments that will be created or updated during shipment consolidation according to the configured policies.  

## Enable demo data

Each of the scenarios in this topic reference values and records included in the standard demo data provided for Supply Chain Management. If you'd like to run the exercises using the values provided here, be sure to work on an environment with the demo data installed, and set the legal entity to **USMF** before you begin.

## Set up shipment consolidation policies and product filters

The scenario described here assumes that you have already enabled the feature, done the exercises, and created the policies and other records described in [Configure shipment consolidation policies](configure-shipment-consolidation-policies.md). Please do those exercises before continuing with this scenario.

## Create the sales orders for this scenario

Start by creating a collection of sales orders that you can work with. You must work with a warehouse that is enabled for advanced warehouse (WMS) processes, and the same warehouse must be used for each of the following sets of orders unless another warehouse is explicitly mentioned. <!-- KFM: The original didn't mention warehouses. Should I remove that again? >>> Add specific warehouse everywhere. Use Warehouse 24. -->

Go to **Accounts receivable \> Orders \> All sales orders** and create a collection of sales orders with the settings described in the following subsections.

<!-- KFM: Should users set a **Warehouse** for each of the sales orders created here? If so, we should specify that for each of them. We should be able to specify a particular warehouse that is already set up correctly in the standard demo data >>> YES -->

<!-- KFM: Throughout this section we refer to item A0001 and A0002 as having no Code 4, while items D0001 and D0002 have Code 4 values. However, on my demo setup, I could only set Code 4 for items A0001 and A0002. The setting is disabled for D0001 and D0002. Therefore, the "Configure shipment consolidation policies" topic describes making this setting for items A0001 and A0002 (not D000x). We need to align this scenario with that one and with the actual USMF demo data people will have. (Or we need to add steps here for how to enable this setting for the D000x items.) -->

<!-- KFM: We are never reserving the inventory for the order lines in this topic, but we do in one of the others. Should we also do that here? >>> NO, not needed here. -->

### Create order set 1

#### Sales order 1-1

Create a sales order with the following settings:

- **Customer account** - *US-001*
- **Mode of delivery** - *Airwa-Air*
- Add an order line with the following settings:
  - **Item number** - *A0001* (an item without a **Code 4** filter assigned)
  - **Quantity** - *1.00*

#### Sales order 1-2

Create a sales order with the following settings:

- **Customer account** - *US-001*
- **Mode of delivery** - *Airwa-Air*
- Add an order line with the following settings:
  - **Item number** - *A0001* (an item without a **Code 4** filter assigned)
  - **Quantity** - *1.00*

#### Sales order 1-3

Create a sales order with the following settings:

- **Customer account** - *US-001*
- **Mode of delivery** - *10*
- Add an order line with the following settings:
  - **Item number** - *A0001* (an item without a **Code 4** filter assigned)
  - **Quantity** - *1.00*
- Add a second order line with the following settings:
  - **Item number** - *A0002* (an item without a **Code 4** filter assigned)
  - **Quantity** - *1.00*
  - **Mode of delivery** - *Airwa-Air*

### Create order set 2

#### Sales orders 2-1 and 2-2

Create two identical sales orders with the following settings:

- **Customer account** - *US-002*
- Add an order line with the following settings:
  - **Item number** - *D0001* (an item with its **Code 4** filter set to *Flammable*)
  - **Quantity** - *1.00*
- Add a second order line with the following settings:
  - **Item number** - *D0002* (an item with its **Code 4** filter set to *Explosive*)
  - **Quantity** - *1.00*
  - **Mode of delivery** - *Airwa-Air*

### Create order set 3

#### Sales order 3-1

Create a sales order with the following settings:

- **Customer account** - *US-002*
- Add an order line with the following settings:
  - **Item number** - *D0001* (an item with its **Code 4** filter set to *Flammable*)
  - **Quantity** - *1.00*
- Add a second order line with the following settings:
  - **Item number** - *D0002* (an item with its **Code 4** filter set to *Explosive*)
  - **Quantity** - *1.00*
  - **Mode of delivery** - *Airwa-Air*

> [!NOTE]
> Although this order is the same as the two you created for order set 2, it is listed as its own order set because you will release it separately later in this scenario.

### Create order set 4

#### Sales order 4-1

Create a sales order with the following settings:

- **Customer account** - *US-001*
- **Customer requisition** - *1*
- Add an order line with the following settings:
  - **Item number** - *A0001* (an item without a **Code 4** filter assigned)
  - **Quantity** - *1.00*

### Create order set 5

#### Sales orders 5-1 and 5-2

Create two identical sales orders with the following settings:

- **Customer account** - *US-001*
- **Customer requisition** - *2*
- Add an order line with the following settings:
  - **Item number** - *A0001* (an item without a **Code 4** filter assigned)
  - **Quantity** - *1.00*

#### Sales order 5-3

Create a sales order with the following settings:

- **Customer account** - *US-001*
- **Customer requisition** - *1*
- Add an order line with the following settings:
  - **Item number** - *A0001* (an item without a **Code 4** filter assigned)
  - **Quantity** - *1.00*

### Create order set 6

#### Sales orders 6-1 and 6-2

Create two identical sales orders with the following settings:

- **Customer account** - *US-003*
- **Customer requisition** - *2*
- Add an order line with the following settings:
  - **Item number** - *A0001* (an item without a **Code 4** filter assigned)
  - **Quantity** - *1.00*

#### Sales orders 6-3 and 6-4

Create two identical sales orders with the following settings:

- **Customer account** - *US-004*
- **Customer requisition** - *1*
- Add an order line with the following settings:
  - **Item number** - *A0001* (an item without a **Code 4** filter assigned)
  - **Quantity** - *1.00*

#### Sales orders 6-5 and 6-6

Create two identical sales orders with the following settings:

- **Customer account** - *US-007*
- **Site** - *6*
- **Warehouse** - *61*
- **Pool** - *ShipCons*
- Add an order line with the following settings:
  - **Item number** - *A0001* (an item without a **Code 4** filter assigned)
  - **Quantity** - *1.00*

#### Sales orders 6-7 and 6-8

Create two identical sales orders with the following settings:

- **Customer account** - *US-007*
- **Site** - *6*
- **Warehouse** - *61*
- **Pool** - (leave empty)
- Add an order line with the following settings:
  - **Item number** - *A0001* (an item without a **Code 4** filter assigned)
  - **Quantity** - *1.00*

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
    - **Table** - *Sales order*
    - **Derived table** - *Sales order*
    - **Field** - *Sales order*
    - **Criteria** - Enter sales order numbers from the desired order set. <!-- KFM:  Comma-separated -->
1. Select **OK** to save your query.
1. Select **OK** to launch the *automatic release to warehouse* procedure.

#### Review the created or updated shipment

1. Go to **Warehouse management > Shipments > All shipments**.
1. Find and select the required shipment.
1. If a consolidation policy was used during shipment creation or update, you can find it in the **Shipment consolidation policy** field.

### Release sales orders from order set 1

Follow the [basic release to warehouse procedure](#release-procedure) to release the sales orders from order set one.

When your done, you should see that two shipments were created:

- The first shipment contains three lines and was created using the *CustomerMode* shipment consolidation policy.
- The second shipment (without the *Airways* transportation mode of delivery) is created using the *CustomerOrderNo* shipment consolidation policy.

### Release sales orders from order set 2

Follow the [basic release to warehouse procedure](#release-procedure) to release the sales orders from order set two.

When your done, you should see that three shipments were created:

- The first shipment contains *Flammable* items.
- Each of the other two shipments contains one line with the *Explosive* item.

### Release sales orders from order set 3

Follow the [basic release to warehouse procedure](#release-procedure) to release the sales orders from order set three.

When your done, you should see that:

- One existing shipment was updated (the one that was created as a result of order set 2 release to warehouse). A line with the *Flammable* item was added.
- One new shipment was created. It contains the *Explosive* item.

### Release sales orders from order set 4

Follow the [basic release to warehouse procedure](#release-procedure) to release the sales orders from order set four.

When your done, you should see that one existing shipment (where **Customer requisition** = *1*) was updated to have one new line added to it.

### Release sales orders from order set 5

Follow the [basic release to warehouse procedure](#release-procedure) to release the sales orders from order set five.

When your done, you should see that:

- One existing shipment (where **Customer requisition** = *1*) was updated. It now has a line from sales order 5-3 (with **Customer requisition** = *1*) added to it.
- One new shipment was created, where lines from sales orders 5-1 and 5-2 are grouped into one shipment.

### Release sales orders from order set 6

Follow the [basic release to warehouse procedure](#release-procedure) to release the sales orders from order set six.

When your done, you should see that four shipments were created:

- Lines from two orders for customer *US-003* were grouped into one shipment using the *Order pool* shipment consolidation policy;
- Lines from two orders for customer *US-004* were grouped into one shipment using the *Order pool* shipment consolidation policy;
- Lines from sales orders 5 and 6 for customer *US-007* were grouped into one shipment using the *Order pool* shipment consolidation policy;
- Lines from sales orders 7 and 8 for customer *US-007* were grouped into one shipment using the *CrossOrder* shipment consolidation policy.

## Additional resources

- [About shipment consolidation policies](about-shipment-consolidation-policies.md)  
- [Configure shipment consolidation policies](configure-shipment-consolidation-policies.md)
- [Consolidate shipments](consolidate-shipments.md)
