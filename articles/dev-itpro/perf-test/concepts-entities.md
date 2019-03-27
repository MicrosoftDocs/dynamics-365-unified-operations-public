---

title: Acceptance test library commands
description: This topic provides information about the acceptance test library.
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

# Acceptance test library commands

[!include [banner](../includes/banner.md)]

[!include [banner](../includes/preview-banner.md)]

# Entities
A test entity class represents data and associated behavior that is perceived as a single concept. Usually test entity classes are based on forms like: Sales order, Transfer order, Released product, etc.

The test entity classes exposes the properties that are most frequently used in test scenarios as well as the behavior that is most important from the test data setup and scenario test perspective.

An entity in ATL must have:
- Property methods for getting and setting entity properties
- Fluent setters which allow setting entity properties in a fluent manner
- The save method which saves the entity to the database

An entity in ATL can have:
- Action methods to expose business operations relevant to the entity.
- Query methods to enable navigation to components/related entities.

## Naming convention
`AtlEntity]<ModuleName><EntityName>`

Where:
- ModuleName is based on the names of the modules in main menu. However a short version or an abbreviation should be used to support brevity of test code.

- EntityName is based on the UI names rather than based on table names. E.g. Use SalesOrder rather than SalesTable.
 
If an entity has two UI names then it’s fine to choose the shorter one. E.g. it’s fine to use Item instead of ReleasedProduct since both terms are used interchangeably.

### Examples
```
AtlEntitySalesOrder
AtlEntityTransferOrderLine
```

## Property methods
As mentioned above one of the main purposes of a test entity is to expose data. Properties of the entity can be set or retrieved using `parm` methods. 

### Primitive type properties
Create a `parm` method to expose a primitive type property. 

#### Example
```
public SalesQty parmQuantity(SalesQty _qty = 0)
{
    if (!prmisDefault(_qty))
    { // setter
        salesLine.SalesQty = _qty;
        this.onSalesQtyOrInventDimChange();
    }
 
    return salesLine.SalesQty;
}
```
 
### Entity references
Suppose there is a customer entity `AtlEntityCustomer`. Then the reference to the customer should be exposed as a property method on the `AtlEntitySalesOrder` entity:

```
public AtlEntityCustomer parmCustomer(AtlEntityCustomer _custTable = null)
```
 
The property method can be used as either a setter or a getter:
```
salesOrder.parmCustomer(customer); // setter
customer = salesOrder.parmCustomer(); // getter
```
 
#### Entity reference methods naming conventions
The parm prefix should be used to identify property methods. When you are exposing an entity reference property use the UI name of the field rather than the AOT name. If the UI name includes Id, Code or Number postfixes then skip them. I.e. use `parmItem` rather than `parmItemNumber`. 

### Record references
If the customer entity has not been created yet (and will not be created in the near future) then the reference property should expose the corresponding record buffer (`CustTable`):
```
public CustTable parmCustomer(CustTable _custTable = null)
```
#### Record reference naming conventions
Use the same naming conventions as for entity references. 

### Id references
In addition to having an entity/record reference it’s fine to also introduce the ID reference property. 
 
```
public CustAccount customerId(CustAccount _custTable = null)
```
 
Do not introduce ID references without introducing corresponding entity/buffer references. ID references are just “shortcuts” to the entity/buffer reference methods. The implementation of ID references should just delegate the call to the entity/buffer references.

#### Id reference naming conventions
Use the UI term if it includes terms like ID, Number, Account, Code, Name. Otherwise add an appropriate suffix to the entity/record reference name.

#### Id reference methods contract
The id reference method always finds the referenced entity based on the provided ID and delegates the call to the entity/record reference method.
If no entity/record was found based on the specified ID then an error message will be thrown.

## Fluent setters
In order to support fluent initialization and modification of entities fluent setter methods are created.

### Declaration example

```
public AtlEntitySalesLine setQty(SalesQty _qty)
```
	
### Code example
```
salesLine.setItem(batchItem).setInventDims([warehouse]).setQty(10).save();
```
### Naming convention
`set<PropertyName>`

Property name should be the same as in the corresponding property method.

## Action methods
Entities not only represent data but also actions that are relevant for them. Actions can be implemented either as a simple action method or as a command object initializer.

### Simple action methods
Simple action method represents a complete action. Simple action methods should not be fluently chained except for the save method that should be fluent. 
#### Naming convention
`<ExecuteBusinessOperation>`

ExecuteBusinessOperation is a verb that represents the business operation. Preferably it should be the same term that is used on the menu item in the UI.
#### Examples
```
salesOrder.save();
salesOrder.postInvoice();
```
### Command object initializers
Command object initializers return a command object that allows to specify parameters of the command and execute it:
```
transferLine.pick().setQty(10).setWMSLocation(bulkLocation).execute();
```
#### Naming convention
`<ExecuteBusinessOperation>`

ExecuteBusinessOperation is a verb that represents the business operation. Preferably it should be the same term that is used on the menu item in the UI.
#### Examples
```
salesOrder.pick().execute();
purchaseOrder.register().execute();
```
### Action entities
Some actions that are available for an entity can be considered as entities themselves. Imagine vendor invoices. Before actually posting an invoice you need to set up parameters of the invoice, edit lines and you can even save it for later. For such commands  introduce a separate entity class.
 
#### Naming convention
`new<ActionName>`

ActionName is a noun that represents the business operation. Ideally the name should be the UI name of the business operation.

#### Example
```
receipt = transfer.newReceipt().setEditLines(true).setExplodeLines(true);
receipt.lines().withBatch(batch1).single().setReceiptQty(6).setScrapQty(1).save();
receipt.lines().withBatch(batch2).single().setReceiptQty(4).setScrapQty(1).save();
receipt.post();
```

#### Class naming convention
`AtlEntity<ModuleName><EntityName><ActionName>`

#### Example
```
AtlEntityInventTransferOrderReceipt
```	
## Adding components
Composition is a kind of relationship where the composite entity has the sole responsibility for the disposition of the component parts. The relationship between the composite and the component is a strong “has a” relationship, as the composite object takes ownership of the component. This means the composite is responsible for the creation and destruction of the component parts. An object instance may only be part of one composite. If the composite object is destroyed, all the component parts must be destroyed. The part has no life of itself and cannot be transferred to another object. Composition enforces encapsulation as the component parts usually are members of the composite object.
For example; creating a source document which is composed of source document lines.
### Adding components
The document entity serves as the composition root and it is responsible for creating a new instance of the document line. Source document entities should have an addLine() method which initializes and returns a new line for the document.

#### Example
```
public AtlEntitySalesLine addLine()
```
 
The addLine() method adds the line object (salesLine in this example) to a collection of lines and returns the parent entity (SalesOrder) in order to preserve fluency of APIs. For creating a new line please create a newLine() method. 
#### Naming convention for adding components
Methods for adding components should follow UI names of the buttons. 
#### Example
```
salesLine = salesOrder.addLine();
```
### Components collections
You can search for components using query methods.

#### Naming convention for components collection
Methods for accessing components collection should follow the UI name of the grid in the hosting form.  

## Query methods
Query methods on an entity allow searching for components/related entities.

### Example
```
transferOrderLine = transferOrder.lines().withItem(item).single();
```
	
In this example lines() is a query method that returns the AtlQueryTransferOrderLines query which is already filtered to only return transfer order lines for the transfer order on which the lines() method was called.

### Naming convention
Use the UI names when possible. Abbreviations are acceptable if the UI term is way too long for using in test automation.

### Example 
```
public AtlQueryWHSLoadLines lines()
{
    return new AtlQueryWHSLoadLines().forLoadId(this.parmLoadId());
}
```
	
See the Queries section for more details.
