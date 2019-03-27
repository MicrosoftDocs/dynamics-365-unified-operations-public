---
# required metadata

title: Test data methods
description: This topic provides information about the most common types of test data methods.
author: MichaelFruergaardPontoppidan
manager: AnnBe
ms.date: 03/27/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: RobinARH
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: MichaelFruergaardPontoppidan
ms.search.validFrom: 2018-XX-XX
ms.dyn365.ops.version: App Update 10.0.2

---

# Test data methods

[!include [banner](../includes/banner.md)]

[!include [banner](../includes/preview-banner.md)]

Entity and helper navigation objects expose test methods that allow you to setup test data. In this topic, you will find information about the most common types of test data methods.

## Factory methods

Factory methods focus on creating data that doesn't exist in the database yet. There are two types of entity factory methods, `init` methods and `create` methods. An `init` method initializes the entity, but does not save it to the database. The `create` method initializes the entity and saves it to the database.

### Naming convention
```
init<EntitySpecification> 
create<EntitySpecification>
```

EntitySpecification is the description of the key characteristics of the object that needs to be created.

### Examples
```
salesOrder = data.sales().salesOrders().initDefault();
purchaseOrder = data.purch().purchaseOrders().createDefault();
```
### Best practices
The `create` method should always call the `init` method with the same entity specification. 

### Example
```
public AtlEntitySalesOrder createDefault()
{
    AtlEntitySalesOrder salesOrder = this.initDefault();
    salesOrder.save();
    return salesOrder;
}
```
### Prerequisite data 
The `init` method should take care of prerequisites setup.

Some entities require certain prerequisites to be set up before the entity can be created. If this is the case, prior to initializing the entity, the `ensure` method needs to be called. You also need to subscribe to all the entity events that require automatic prerequisites setup.

#### Example
```
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
Builder methods are responsible for initializing creator objects which will be used to create data that does not yet exist in the database. 

### Naming convention
`<EntitySpecification>Builder`

EntitySpecification is the description of the object's key characteristics that need to be created.

### Example
```
	catchWeightItem = data.invent().items().cwBuilder();
```

## Well-known data methods
Well-known data methods provide the possibility of a reference to an entity that is set up in a specific way. If the entity doesn't exist in the database, it will be created.

### Naming convention
`<EntitySpecification>`

EntitySpecification is the description of the key characteristics of the object that needs to be retreived.
### Example
```
fifo = data.invent().modelGroup().fifo();
```
In this example, the contract of the method is that the model group should be using FIFO as inventory model. The rest of the settings can be left as defaulted. 

Sometimes, a real-world name communicates the contract better:
```
pieces = data.common().units().pieces();
```
It is clear that **pieces** is a unit of measure of class "quantity", and has a decimal precision of zero. 

### Contract of well-known data methods

There are a few things to remember about the common contract of the well-known data method.

- Calling the same well-known data method twice should provide the caller with the reference to the same entity. 

    ```
    fifo1 = data.invent().modelGroups().fifo();
    fifo2 = data.invent().modelGroups().fifo();
    fifo1.InventModelGroupId == fifo2.InventModelGroupId;
    ```

- Investing in creating a test entity is not always worth the effort. In this case, the corresponding record buffer should be returned from the well-known data method. This means that if we didn’t invest time into creating the Site entity, then the site well-known data method will be returning InventSite records:
    ```
    InventSite site = data.invent().sites().default();
    ```
- Well-known data methods can take IDs as optional parameters when it makes sense:
    ```
    item1 = data.products().items().default(‘Item1’);
    item2 = data.products().items().default(‘item2’);
    ```

### Implementation
If there is already a builder or a factory method with the name `<EntitySpecification>`, it should be used as the internal implementation for creating the well-known entity.

#### Example
```
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
Ensure methods are responsible for setting up prerequisites that are required for creating an entity or executing a business operation. 

### Naming convention
`ensureCan<ExecuteBusinessOperation>`

ExecuteBusinessOperation is a verb that describes the business operation.

### Examples
```
data.sales().salesOrders().ensureCanCreate();
data.purch().purchaseOrders().ensureCanPostProductReceipt();
```

### Implementation
Figuring out prerequisites for a complex business operation, such as invoice posting, can be complicated and requires a lot of knowledge of the feature area. 

#### Example
```
public void ensureCanCreate()
{
    data.helpers().setNumberSequenceReference(extendedTypeNum(InventDimId));
}
```

#### Automatic prerequisite setup
To enable automatic prerequisite setup, you need to call the ensure methods in the appropriate `init` method. See the Factory methods section earlier in this topic for more details.

## Query methods
Query methods are responsible for initializing a new query for the entity type of the navigation node that they are defined on.

### Naming convention
`query`

### Examples
```
loadLinesQuery = data.whs().loadLines().query();
purchaseLinesQuery = data.invent().transferOrderLines().query();
```
## Specification methods
Specification methods are responsible for initializing new specification objects for the entity type of the navigation node where the specification method is defined.

### Naming convention
`spec`

### Example
```
loadLinesSpec = data.whs().loadLines().spec();
```
## Find methods
Find methods allow to find an entity based on the primary key.

### Naming convention
`find`

### Example
```
salesOrder = data.sales().salesOrders().find(salesOrderId);
```

### Automatic prerequisite setup
If the entity has query support, the implementation should use the query that has already set up prerequisites support. Otherwise, after finding the record buffer and initializing the new instance of the entity, you should subscribe `ensure` methods to the business operation events of the entity.
