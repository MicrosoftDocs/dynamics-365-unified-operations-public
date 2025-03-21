---
title: Reservations in Warehouse management
description: Learn about the functionality for reservations in Warehouse management
ms.author: atapiabailon
author: Atapiabailon
ms.date: 03/13/2025
ms.topic: article
ms.reviewer: kamaybac
ms.search.form: WHSReservationHierarchy
---

# Reservations in Warehouse management

[!include [banner](../includes/banner.md)]

This article describes the functionality for reservations that is introduced in Warehouse management and provides information about how it is implemented.

## <a name="reservations-in-warehouse-management"></a>Reservations in Warehouse management

The Warehouse management (WHS) solution introduces functionality for reserving items and materials.

The reservation functionality can be used only for items that are enabled for warehouse management processes. However, if an item is itself enabled for warehouse management processes, it can be used both in warehouses that are enabled for warehouse management processes and warehouses that are not. The behavior in reservation scenarios is different, depending on the warehouse setup. Later sections of this article will provide more details about the differences.

The functionality is built on reservation hierarchies and is intended to support the following:
- Flexible warehouse operations
- Postponement of reservation details
- Clear separation of which inventory dimensions can be specified, and when they can be specified

### Reservation hierarchies

One of the key components of the reservation system in WHS is the reservation hierarchy. The reservation hierarchy 
defines the different levels on which reservations can be made. Each level represents a physical inventory dimension. 

The following illustration shows a typical reservation hierarchy for an item that uses the Site, Warehouse, Inventory 
status, Location, and License plate dimensions as physical inventory dimensions. 

:::image type="content" source="media/inventory-reservation-hierarchies.svg" alt-text="Inventory reservation hierarchies":::

The level with the lowest value in the Reservation hierarchy level column is the least-specific level. In the illustration, this is the site level. The higher the value, the more details are required to make a reservation on that level.

Information about on-hand inventory is stored separately for each level in the reservation hierarchy.

### Details about the implementation of reservation hierarchies

The following illustration shows the data model for the setup of a reservation hierarchy and its relation to the 
inventTable table.

:::image type="content" source="media/inventory-reservation-hierarchies-setup-of-reservation-hierarchies.png" alt-text="Setup of reservation hierarchies":::

The definitions of reservation hierarchies are stored in the WHSReservationHierarchy and WHSReservationHierarchyElement tables.These are shared tables. A reservation hierarchy can be associated with one item within a company.

The **WHSReservationHierarchyProvider** class provides a large number of APIs that are useful when you work with and 
query the reservation hierarchy for an item.

### Making reservations on different levels

Based on the reservation hierarchy, you can make reservations on different levels without providing details about where to reserve and what dimensions to reserve on. This lets you postpone specific details, such as the location or license plate to make the reservation on. The location to reserve items on can be determined later by the location directive.

For example, you make a reservation only on the site level. In this case, inventory blocking can be used to block a 
quantity of an item on a given site.

As another example, you make reservations for a sales order created on site 4 and warehouse 42, which is a warehouse 
that is enabled for WHS processes, and for the **Available** inventory status. For this example, the reservation is made only on the inventory status level.

### Impact of the reservation hierarchy setup

For warehouses that are enabled for warehouse management processes, the setup of reservation hierarchies greatly 
affects the processes for outbound orders, such as sales orders and transfer orders.

When you set up a reservation hierarchy, the key is to determine which dimensions should be positioned above the 
location level in the hierarchy, and which should be below. The following table describes the effects of arranging 
dimensions either above or below the location level.

|Dimension placement|Description|
|-------------------|-----------|
|Dimension above location | The inventory dimension above the location level must be determined before the Warehouse management functionality can be used. Therefore, this typically happens during order processing or by letting the reservation system determine the dimensions.<br><br> If a dimension is above the location level, warehouse workers cannot change this dimension, because it is considered a strict picking requirement. For example, if the Batch number dimension is above the location level, a worker cannot pick a batch that is different from the one that he or she was instructed to pick.  |
|Batch above location | Process industry functionality for batches requires that the Batch number dimension be above the Location dimension in the reservation hierarchy. When this is the case, all functionality for First Expiry First Out (FEFO), same batch, batch disposition codes, and batch attributes is supported. |
|Dimensions below location | WHS and warehouse workers can determine the Location dimension and the dimensions below it. <br><br>The Location dimension and any dimensions below it should not be entered on sales and transfer lines if you expect work to be created. For example, if the Batch number dimension is below the Location dimension, it should not be specified on the sales line. Otherwise, WHS cannot create work to carry out the pick and pack operations. |

## <a name="impact-of-the-reservation-hierarchy-setup"></a>Impact of the reservation hierarchy setup

For warehouses that are enabled for warehouse management processes, the setup of reservation hierarchies greatly affects the processes for outbound orders, such as sales orders and transfer orders.

When you set up a reservation hierarchy, the key is to determine which dimensions should be positioned above the location level in the hierarchy, and which should be below. The following table describes the effects of arranging dimensions either above or below the location level.

|Dimension placement|Description|
|-|-|
|Dimension above location | The inventory dimension above the location level must be determined before the Warehouse management functionality can be used. Therefore, this typically happens during order processing or by letting the reservation system determine the dimensions. <br><br> If a dimension is above the location level, warehouse workers cannot change this dimension, because it is considered a strict picking requirement. For example, if the Batch number dimension is above the location level, a worker cannot pick a batch that is different from the one that he or she was instructed to pick. |
|Batch above location| Process industry functionality for batches requires that the Batch number dimension be above the Location dimension in the reservation hierarchy. When this is the case, all functionality for First Expiry First Out (FEFO), same batch, batch disposition codes, and batch attributes is supported |
|Dimensions below location | WHS and warehouse workers can determine the Location dimension and the dimensions below it. <br><br>The Location dimension and any dimensions below it should not be entered on sales and transfer lines if you expect work to be created. For example, if the Batch number dimension is below the Location dimension, it should not be specified on the sales line. Otherwise, WHS cannot create work to carry out the pick and pack operations. |

## <a name="on-hand-representation-and-calculations"></a>On-hand representation and calculations

To support reservations on different levels, a new way of storing information about on-hand inventory is used for items 
that are enabled for warehouse management processes. Each level in the hierarchy corresponds to a set of physical 
inventory dimensions. For each level in the reservation hierarchy, the following information is stored: 
- The quantity that is available physical 
- The quantity that is available ordered 
- The quantity that is reserved physical 
- The quantity that is reserved ordered 
 
The following table shows how the data might look for an item with 10 pieces available physical and 2 pieces reserved physical on the status level.

|Level|Site|Warehouse|Inventory status|Location|License plate|Available physical|Available ordered|Reserved physical|Reserved ordered|
|-|-|-|-|-|-|-|-|-|-|
|Item| | | | | |10|10|2|0|
|Site|S1| | | | |10|10|2|0|
|Warehouse|S1|WH1| | | |10|10|2|0|
|Status|S1|WH1|Good | | |10|10|2|0|
|Location|S1|WH1|Good|Bulk| |12|12|0|0|
|License plate|S1|WH1|Good|Bulk|LP1|12|12|0|0|

As the table shows, reservations are tracked only on the levels that are affected by the reservation. 
 
Because of the way that information about availability and reservations is stored, the corresponding values from the InventSum table cannot be used directly for WHS-enabled items.

### On-hand calculation algorithm

The following steps provide a high-level overview of the algorithm that determines the available on-hand quantity for 
an item and a set of inventory dimensions: 
1. Determine the available on-hand quantity, based on the exact dimensions. This is the lowest level in the hierarchy. 
1. Determine the smallest available quantity from all levels above the level found in step 1. 
1. Return the smaller of the quantities found in step 1 and step 2. This is the available quantity. 
For example, based on the data in the previous table, the available physical quantity is calculated for the following dimensions:
- Site: Site1
- Warehouse: WH1
- Inventory status: Good
- Location: Bulk

In step 1 of the algorithm, the quantity is 12, because that is the quantity that is available on the location level. However, in step 2, the smallest quantity from the levels above the location level is 10. Therefore, in step 3, the available physical quantity is 10, which is the smaller of 12 and 10. 

Calculations of on-hand quantity for work transactions are done differently. The on-hand quantity is determined only up to the location level, because work affects reservations only on the location level and lower. For example, based on the data in the previous table, the available physical quantity is calculated for work on the following dimensions: 
- Site: Site1
- Warehouse: WH1
- Inventory status: Good
- Location: Bulk

In this case, the available physical quantity is 12, because the quantity is determined only up to the location level.

### Details about the implementation of on-hand calculations

The on-hand information is stored in a new table called WHSInventReserve. The WHSInventReserveDelta table is used to track changes that the current transaction causes in the on-hand quantity. On the final commit, the WHSInventReserve table is updated based on the changes in the WHSInventReserveDelta table. 

Because many scenarios involve calculating on-hand quantities based on itemId, InventDim, or InventSum records for both WHS-enabled and non-WHS-enabled items, APIs are provided to support the calculations in a seamless way.

The following example shows how to instantiate the class that can be used to calculate availability for both WHS enabled and non-WHS-enabled items.

```
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

The **InventAvailabilityProvider** class provides numerous other APIs that are used to determine the availability based on various types of input. The existing **InventOnHandQty** class has been updated so that it also provides correct results for items that are enabled for warehouse management processes. 

The following illustration shows the various classes and interfaces that are used to provide and encapsulate the calculations. Note that, for the sake of simplicity, some details have been omitted.

:::image type="content" source="media/inventory-reservation-hierarchies-encapsulations.png" alt-text="Encapsulation of the calculations":::

## <a name="reservation-strategies"></a>Reservation strategies

To control the levels of the reservation hierarchy at which reservations are made, the system uses the concept of a reservation strategy. A reservation strategy determines the outcome of a reservation, and the dimensions that are used to make the reservation. Reservation strategies are implemented in the code and are not currently user-configurable. 

Each reservation strategy determines the level that the reservation should be made on. If the dimensions that are passed to the reservation system do not cover all the dimensions to the level defined by the strategy, the reservation system queries the on-hand availability until the required level; then, based on the results of this query, it does the reservation so that it covers all the required dimensions.

The reservation strategies that are chosen for a reservation depend on multiple factors, such as the following:
- Warehouse setup
- Order type

The following table describes the reservation strategies that the reservation system uses.

|Reservation strategy|Description|
|--------------------|-----------|
|None|The reservation is made on the dimensions that are passed, if possible. This strategy is used by inventory blocking, and lets you make reservations on, for example, the site level or the warehouse level.|
|All|The reservation is made on all of the dimensions in the reservation hierarchy. This strategy is used, for example, for transfer journals, or for warehouses that have not been enabled for warehouse management processes. |
|Above location|The reservation is made only on the locations above the location level. This strategy is used, for example, for sales and transfer orders when reservations are made in a warehouse that is enabled for warehouse management processes. |
|All not allowed blank|The reservation is made on the first lowest level that does not allow for blank issue for the inventory dimensions. This strategy enables automatic reservations on non-license plate-controlled locations. |
|Batch level|This strategy is applied for items for which the Batch number dimension is selected and positioned above the Location dimension in the reservation hierarchy. This strategy is used when only reservations that are reserved ordered can be made. In that case, a reservation until the batch level is attempted. |

The reservation system supports multiple reservation strategies in sequential order when reservations are made. For example, the system uses the All and All not allowed blank strategies to make reservations for transfer journals. 


### Details about the implementation of reservation strategies

The following illustration shows the classes that are used to implement the reservation strategies, and the main consumers of the classes. Note that, for the sake of simplicity, some details have been omitted. 

:::image type="content" source="media/inventory-reservation-hierarchies-strategy-classes.png" alt-text="Implementation of reservation strategies":::

The implementation is easy to extend, because the instantiation uses the SysExtension framework.


## <a name="synchronization-of-dimensions-between-receipts-and-issues"></a>Synchronization of dimensions between receipts and issues

When an inventory transaction is marked or reserved ordered, the inventory dimensions are typically synchronized between receipts and issues. For example, when a purchase order that was created based on a sales order is modified or received, the dimensions are transferred to the inventory transactions for the sales line.

For items that are enabled for warehouse management processes, the synchronization differs from the standard 
behavior. When work must be created, the source line transactions can be reserved only until the level above the location level. If all dimensions are synchronized, work cannot be created. Therefore, dimensions above the location level are not synchronized for all scenarios.

If the item and warehouse are enabled for warehouse management processes, and if the issue type is a type that can generate work, such as a sales line, only dimensions above the location level are synchronized. This means that if an item uses batch numbers, and the batch number is placed below the location in the eservation hierarchy, the batch number is not synchronized from receipt to issue transactions.

### Details about the implementation of synchronization between receipts and issues

The logic that determines how the dimensions are synchronized is implemented in the following methods on the 
inventMovement class:
- getInventDimForReservedTransPhysChange
- getInventDimForIssueTransFromReceipt


> [!NOTE]
>
> When using the inventory reservation hierarchy of the Batch-below[location] type, and selling batch-tracked products for enabled warehouse management processes (WMS), a **Flexible warehouse-level dimension reservation policy** should be set, so reservations can be done to those products.
>
> To learn more about the *Flexible warehouse-level dimension reservation policy*, see [Flexible warehouse-level dimension reservation policy](flexible-warehouse-level-dimension-reservation.md)