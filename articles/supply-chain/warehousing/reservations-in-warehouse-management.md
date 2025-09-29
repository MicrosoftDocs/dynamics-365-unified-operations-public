---
title: Reservations in Warehouse management
description: Learn about the functionality for reservations in Warehouse management
author: Mirzaab
ms.author: mirzaab
ms.reviewer: kamaybac
ms.search.form: WHSReservationHierarchy
ms.topic: how-to
ms.date: 04/08/2025
ms.custom:
  - bap-template
---

# Reservations in Warehouse management

[!include [banner](../includes/banner.md)]

[!INCLUDE [Lightbox tip](~/../shared-content/shared/lightbox-tip.md)]

This article describes the reservation functionality in Warehouse management and provides information about how it's implemented.

The **Warehouse management** module introduces functionality for reserving items and materials. The reservation functionality can be used only for items that are enabled for warehouse management processes (WMS). However, an item that is enabled for WMS can be used in both warehouses that are enabled for WMS and warehouses that aren't enabled for WMS.

The behavior in reservation scenarios varies, depending on the warehouse setup. Later sections of this article provide more details about the differences.

The reservation functionality is built on *reservation hierarchies* and is intended to support the following cases:

- Flexible warehouse operations
- Postponement of reservation details
- Clear separation of which inventory dimensions can be specified, and when they can be specified

## Reservation hierarchies

A key component of the reservation system in the **Warehouse management** module is the reservation hierarchy. The reservation hierarchy defines the different levels where reservations can be made. Each level represents a physical inventory dimension.

The following illustration shows an example of a reservation hierarchy on the **Inventory reservation hierarchies** page. *Default* is a typical reservation hierarchy for an item that uses the Site, Warehouse, Inventory status, Location, and License plate dimensions as physical inventory dimensions.

:::image type="content" source="media/inventory-reservation-hierarchies.svg" alt-text="Screenshot of an inventory reservation hierarchy on the Inventory reservation hierarchies page." lightbox="media/inventory-reservation-hierarchies.svg":::

The lower the value in the **Reservation hierarchy level** column of the grid, the less specific the level is. The higher the value, the more details are required to make a reservation on the level. In the previous illustration, the **Site** level has the lowest value (*1*) and is therefore the least specific level. The **License plate** level has the highest value (*5*) and is therefore the most specific level.

Information about on-hand inventory is stored separately for each level in the reservation hierarchy.

### Details about the implementation of reservation hierarchies

The following illustration shows the data model for the setup of a reservation hierarchy and its relation to the `inventTable` table.

:::image type="content" source="media/inventory-reservation-hierarchies-setup-of-reservation-hierarchies.png" alt-text="Diagram that shows the data model for the setup of reservation hierarchies." lightbox="media/inventory-reservation-hierarchies-setup-of-reservation-hierarchies.png":::

The definitions of reservation hierarchies are stored in the `WHSReservationHierarchy` and `WHSReservationHierarchyElement` tables. These tables are shared tables. A reservation hierarchy can be associated with one item within a company.

The `WHSReservationHierarchyProvider` class provides a large number of APIs that are useful when you work with and query the reservation hierarchy for an item.

### Making reservations on different levels

Based on the reservation hierarchy, you can make reservations on different levels without providing details about where to reserve and what dimensions to reserve on. In this way, you can postpone specific details, such as the location or license plate to make the reservation on. The location to reserve on can be determined later by the location directive.

Here are some examples:

- You make a reservation only on the site level. In this case, inventory blocking can be used to block a quantity of an item on a given site.
- You make reservations for a sales order that was created on site 4 and warehouse 42, and for the *Available* inventory status. Warehouse 42 is enabled for WMS. In this case, the reservation is made only on the inventory status level.

## Impact of the reservation hierarchy setup

For WMS-enabled warehouses, the setup of reservation hierarchies greatly affects the processes for outbound orders, such as sales orders and transfer orders.

When you set up a reservation hierarchy, the key is to determine which dimensions should be positioned above the location level in the hierarchy, and which dimensions should be positioned below the location level. The following table describes the effects of arranging dimensions either above or below the location level.

| Dimension placement | Description |
|---|---|
| Dimensions above location | <p>The inventory dimensions above the location level must be determined before the Warehouse management functionality can be used. Typically, workers make this determination during order processing, or they let the reservation system make it.</p><p>If a dimension is above the location level, warehouse workers can't change it, because it's considered a strict picking requirement. For example, if the Batch number dimension is above the location level, a worker can't pick a batch that differs from the one that they were instructed to pick.</p> |
| Batch above location | Process industry functionality for batches requires that the Batch number dimension is above the Location dimension in the reservation hierarchy. In this case, all functionality for first expiry, first out (FEFO), same batch reservation, batch disposition codes, and batch attributes is supported. |
| Dimensions below location | <p>Both the system and warehouse workers can determine the Location dimension and the dimensions below it.</p><p>The Location dimension and any dimensions below it should not be entered on sales and transfer lines if you expect work to be created. For example, if the Batch number dimension is below the Location dimension, it should not be specified on the sales line. Otherwise, WHS can't create work to carry out the pick and pack operations.</p> |

## On-hand representation and calculations

To support reservations on different levels, a new method is used to store information about on-hand inventory for WMS-enabled items. Each level in the hierarchy corresponds to a set of physical inventory dimensions. For each level in the reservation hierarchy, the following information is stored:

- The quantity that is available physical
- The quantity that is available ordered
- The quantity that is reserved physical
- The quantity that is reserved ordered

The following table shows how the data might look for an item that has 10 pieces available physical and 2 pieces reserved physical on the status level.

| Level | Site | Warehouse | Inventory status | Location | License plate | Available physical | Available ordered | Reserved physical | Reserved ordered |
|---|---|---|---|---|---|---|---|---|---|
| Item | | | | | | 10 | 10 | 2 | 0 |
| Site | S1 | | | | | 10 | 10 | 2 | 0 |
| Warehouse | S1 | WH1 | | | | 10 | 10 | 2 | 0 |
| Status | S1 | WH1 | Good | | | 10 | 10 | 2 | 0 |
| Location | S1 | WH1 | Good | Bulk | | 12 | 12 | 0 | 0 |
| License plate | S1 | WH1 | Good | Bulk | LP1 | 12 | 12 | 0 | 0 |

As the table shows, reservations are tracked only on the levels that are affected by the reservation.

Because of the way that information about availability and reservations is stored, the corresponding values from the `InventSum` table can't be used directly for WHS-enabled items.

### On-hand calculation algorithm

The following steps provide a high-level overview of the algorithm that determines the available on-hand quantity for an item and a set of inventory dimensions:

1. Determine the available on-hand quantity based on the exact dimensions. This level is the lowest level in the hierarchy.
1. Determine the smallest available quantity from all levels above the level that was found in step 1.
1. Return the smaller of the quantities that were found in steps 1 and 2. This quantity is the available quantity.

For example, based on the data in the previous table, the available physical quantity is calculated for the following dimensions:

- **Site:** *Site1*
- **Warehouse:** *WH1*
- **Inventory status:** *Good*
- **Location:** *Bulk*

In step 1 of the algorithm, the quantity is 12, because that quantity is the one that is available on the location level. However, in step 2, the smallest quantity from the levels above the location level is 10. Therefore, in step 3, the available physical quantity is 10, because that quantity is the smaller of 12 and 10.

Calculations of on-hand quantity for work transactions are done differently. The on-hand quantity is determined only up to the location level, because work affects reservations only on the location level and below. For example, based on the data in the previous table, the available physical quantity is calculated for work on the following dimensions:

- **Site:** *Site1*
- **Warehouse:** *WH1*
- **Inventory status:** *Good*
- **Location:** *Bulk*

In this case, the available physical quantity is 12, because the quantity is determined only up to the location level.

### Details about the implementation of on-hand calculations

The on-hand information is stored in a new table that is named `WHSInventReserve`. The `WHSInventReserveDelta` table is used to track changes that the current transaction causes in the on-hand quantity. When the final commit occurs, the `WHSInventReserve` table is updated based on the changes in the `WHSInventReserveDelta` table.

Because many scenarios involve the calculation of on-hand quantities based on `itemId`, `InventDim`, or `InventSum` records for both WMS-enabled and non-WMS-enabled items, APIs are provided to support the calculations in a seamless way.

The following example shows how to instantiate the class that can be used to calculate availability for both WMS-enabled and non-WMS-enabled items.

```xpp
InventAvailabilitySearch availabilitySearch;
InventIAvailability availability;

availabilitySearch = InventAvailabilitySearch::construct();
availabilitySearch.setItemId(_itemId);
availabilitySearch.setInventDimCriteria(_inventDimCriteria, _inventDimCriteriaParm);
availabilitySearch.setInventSum(_inventSum);
availability = InventAvailabilityProvider::construct().find(availabilitySearch).parmInventAvailability();

this.AvailOrderedCalculated = availability.availTotal();
this.AvailPhysicalCalculated = availability.availPhysical();
this.ReservPhysical = availability.reservPhysical();
this.OrderedSum = availability.orderedSum();
```

The `InventAvailabilityProvider` class provides numerous other APIs that are used to determine availability based on various types of input. The existing `InventOnHandQty` class was updated so that it also provides correct results for WMS-enabled items.

The following illustration shows the various classes and interfaces that are used to provide and encapsulate the calculations. For the sake of simplicity, some details are omitted.

:::image type="content" source="media/inventory-reservation-hierarchies-encapsulations.png" alt-text="Diagram that shows the classes and interfaces that encapsulate the calculations." lightbox="media/inventory-reservation-hierarchies-encapsulations.png":::

## Reservation strategies

To control the levels of the reservation hierarchy that reservations are made on, the system uses the concept of *reservation strategies*. A reservation strategy determines the outcome of a reservation, and the dimensions that are used to make the reservation. Reservation strategies are implemented in the code and aren't currently user configurable.

Each reservation strategy determines the level that the reservation should be made on. If the dimensions that are passed to the reservation system don't cover all the dimensions to the level that is defined by the strategy, the reservation system queries the on-hand availability until the required level. Then, based on the results of this query, it does the reservation so that it covers all the required dimensions.

The reservation strategies that are chosen for a reservation depend on the following factors, among others:

- Warehouse setup
- Order type

The following table describes the reservation strategies that the reservation system uses.

| Reservation strategy | Description |
|---|---|
| None | The reservation is made on the dimensions that are passed, if possible. This strategy is used by inventory blocking. It lets you make reservations on, for example, the site or warehouse level. |
| All | The reservation is made on all the dimensions in the reservation hierarchy. This strategy is used, for example, for transfer journals or non-WMS-enabled warehouses. |
| Above location | The reservation is made only on the dimensions above the location level. This strategy is used, for example, for sales and transfer orders when reservations are made in a WMS-enabled warehouse. |
| All not allowed blank | The reservation is made on the first lowest level that doesn't allow for blank issue for the inventory dimensions. This strategy enables automatic reservations on locations that aren't license plate controlled. |
| Batch level | This strategy is applied for items that the Batch number dimension is selected for, and that are above the Location dimension in the reservation hierarchy. This strategy is used when only reservations that are reserved ordered can be made. In that case, the reservation system attempts a reservation until the batch level. |

The reservation system supports multiple reservation strategies in sequential order when reservations are made. For example, the system uses the All and All not allowed blank strategies to make reservations for transfer journals.

### Details about the implementation of reservation strategies

The following illustration shows the classes that are used to implement reservation strategies, and the main consumers of those classes. For the sake of simplicity, some details are omitted.

:::image type="content" source="media/inventory-reservation-hierarchies-strategy-classes.png" alt-text="Diagram that shows the implementation of reservation strategies." lightbox="media/inventory-reservation-hierarchies-strategy-classes.png":::

The implementation is easy to extend, because the instantiation uses the SysExtension framework.

## Synchronization of dimensions between receipts and issues

When an inventory transaction is marked or reserved ordered, the inventory dimensions are typically synchronized between receipts and issues. For example, when a purchase order that was created based on a sales order is modified or received, the dimensions are transferred to the inventory transactions for the sales line.

For WMS-enabled items, the synchronization differs from the standard behavior. When work must be created, the source line transactions can be reserved only until the level above the location level. If all dimensions are synchronized, work can't be created. Therefore, dimensions above the location level aren't synchronized for all scenarios.

If both the item and the warehouse are enabled for WMS, and if the issue type is one that can generate work, such as a sales line, only dimensions above the location level are synchronized. Therefore, if an item uses batch numbers, and the Batch number dimension is below the location level in the reservation hierarchy, the batch number isn't synchronized from receipt to issue transactions.

### Details about the implementation of synchronization between receipts and issues

The logic that determines how dimensions are synchronized is implemented in the following methods on the `inventMovement` class. (However, new methods that are added might also require consideration.)

- `getInventDimForReservedTransPhysChange`
- `getInventDimForIssueTransFromReceipt`

> [!NOTE]
> When products use an inventory reservation hierarchy of the *Batch-below\[location\]* type and are batch tracked for WMS, you should set a *flexible warehouse-level dimension reservation policy*. In this way, you ensure that reservations can be done for those products.
>
> Learn more about the flexible warehouse-level dimension reservation policy in [Flexible warehouse-level dimension reservation policy](flexible-warehouse-level-dimension-reservation.md).
