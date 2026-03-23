---
title: Test data methods
description: Learn about the most common types of test data methods, including naming conventions and code examples for various methods.
author: MichaelFruergaardPontoppidan
ms.author: mfp
ms.topic: how-to
ms.date: 03/16/2026
ms.custom: 
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2019-03-27
ms.dyn365.ops.version: App Update 10.0.2
---

# Test data methods

[!include [banner](../includes/banner.md)]

Entity and helper navigation objects expose test methods that you can use to set up test data. This article provides information about the most common types of test data methods.

## Factory methods

Factory methods focus on creating data that doesn't yet exist in the database. Two types of entity factory methods exist: `init` methods and `create` methods. An `init` method initializes the entity but doesn't save it to the database. A `create` method initializes the entity and saves it to the database.

### Naming convention

`init<EntitySpecification>`

`create<EntitySpecification>`

In this naming convention, `<EntitySpecification>` is the description of the key characteristics of the object that you must create.

### Examples

```xpp
salesOrder = data.sales().salesOrders().initDefault();

purchaseOrder = data.purch().purchaseOrders().createDefault();
```

### Best practices

The `create` method should always call the `init` method that has the same entity specification.

#### Example

```xpp
public AtlEntitySalesOrder createDefault()
{
    AtlEntitySalesOrder salesOrder = this.initDefault();
    salesOrder.save();
    return salesOrder;
}
```

### Prerequisite data

The `init` method sets up prerequisite data.

Before you can create some entities, you need to set up specific prerequisites. In these cases, call the `ensure` method before you initialize the entity. Also, subscribe to all the entity events that require automatic setup of prerequisites.

#### Example

```xpp
public AtlEntitySalesOrder initDefault()
{
    AtlEntitySalesOrder salesOrder;

    this.ensureCanCreate();

    salesOrder = new AtlEntitySalesOrder();
    salesOrder.parmCustomer(data.cust().customers().default());

    _salesOrder.postingInvoice += eventhandler(this.ensureCanPostInvoice);
    _salesOrder.postingPackingSlip += eventhandler(this.ensureCanPostPackingSlip);
    _salesOrder.releasingToWarehouse += eventhandler(this.ensureCanReleaseToWarehouse);
}
```

## Builder methods

Builder methods initialize creator objects that you use to create data that doesn't yet exist in the database.

### Naming convention

`<EntitySpecification>Builder`

In this naming convention, `<EntitySpecification>` is the description of the key characteristics of the object that you must create.

### Example

```xpp
catchWeightItem = data.invent().items().cwBuilder();
```

## Well-known data methods

Well-known data methods provide a way to reference an entity that is set up in a specific way. If the entity doesn't exist in the database, the method creates it.

### Naming convention

`<EntitySpecification>`

In this naming convention, `<EntitySpecification>` is the description of the key characteristics of the object that you must retrieve.

### Example

```xpp
fifo = data.invent().modelGroup().fifo();
```

In this example, the contract of the method specifies that the model group should use first in, first out (FIFO) as the inventory model. The rest of the settings can be left at their default values.

Sometimes, a real-world name communicates the contract better.

```xpp
pieces = data.common().units().pieces();
```

In this example, it's clear that **pieces** is a unit of measure of the "quantity" class, and it has a decimal precision of 0 (zero).

### Contract of well-known data methods

Here are a few things to remember about the common contract of the well-known data methods.

- Two calls to the same well-known data method should provide the caller with the reference to the same entity.

    ```xpp
    fifo1 = data.invent().modelGroups().fifo();
    fifo2 = data.invent().modelGroups().fifo();
    fifo1.InventModelGroupId == fifo2.InventModelGroupId;
    ```

- Creating a test entity isn't always worth the effort. If you don't create a test entity, return the corresponding record buffer from the well-known data method. For example, if you don't invest the time and effort to create the Site entity, the `site` well-known data method returns InventSite records.

    ```xpp
    InventSite site = data.invent().sites().default();
    ```

- Well-known data methods can take IDs as optional parameters when this approach makes sense.

    ```xpp
    item1 = data.products().items().default('Item1');
    item2 = data.products().items().default('item2');
    ```

### Implementation

If there's already a builder or a factory method named `<EntitySpecification>`, use it as the internal implementation to create the well-known entity.

#### Example

```xpp
public InventTable whsBatchAbove(ItemId _itemId = this.whsBatchAboveItemId())
{
    InventTable whsItem = InventTable::find(_itemId, true);
    if (!whsItem)
    {
        whsItem = this.whsBatchAboveBuilder().setItemId(_itemId).create();
    }
    return whsItem;
}
```

## Ensure methods

Ensure methods set up prerequisites that are required to create an entity or run a business operation.

### Naming convention

`ensureCan<ExecuteBusinessOperation>`

In this naming convention, `<ExecuteBusinessOperation>` is a verb that describes the business operation.

### Examples

```xpp
data.sales().salesOrders().ensureCanCreate();

data.purch().purchaseOrders().ensureCanPostProductReceipt();
```

### Implementation

Figuring out prerequisites for a complex business operation, such as invoice posting, can be complicated and requires lots of knowledge about the feature area.

#### Example

```xpp
public void ensureCanCreate()
{
    data.helpers().setNumberSequenceReference(extendedTypeNum(InventDimId));
}
```

#### Automatic prerequisite setup

To enable automatic prerequisite setup, call the `ensure` methods in the appropriate `init` method. For more information, see the [Factory methods](#factory-methods) section earlier in this article.

## Query methods

Query methods initialize new queries for the entity type of the navigation node that they define.

### Naming convention

`query`

### Examples

```xpp
loadLinesQuery = data.whs().loadLines().query();

purchaseLinesQuery = data.invent().transferOrderLines().query();
```

## Specification methods

Specification methods initialize new specification objects for the entity type of the navigation node that they define.

### Naming convention

`spec`

### Example

```xpp
loadLinesSpec = data.whs().loadLines().spec();
```

## Find methods

Find methods let you find an entity based on the primary key.

### Naming convention

`find`

### Example

```xpp
salesOrder = data.sales().salesOrders().find(salesOrderId);
```

### Automatic prerequisite setup

If the entity supports queries, use the query that already sets up prerequisite support. Otherwise, after you find the record buffer and initialize the new instance of the entity, subscribe `ensure` methods to the business operation events of the entity.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
