---

title: Entities in the Acceptance test library
description: This topic discusses the test entity class that represents data and associated behavior.
author: MichaelFruergaardPontoppidan
ms.date: 03/27/2019
ms.topic: article
ms.prod: 
ms.technology: 

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: tfehr
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: mfp
ms.search.validFrom: 2019-03-27
ms.dyn365.ops.version: App Update 10.0.2

---

# Entities in the Acceptance test library

[!include [banner](../includes/banner.md)]

A test entity class represents data and behavior that are perceived as a single concept. Test entity classes are based on pages such as **Sales order**, **Transfer order**, and **Released product**. The test entity classes expose the properties that are most often used in test scenarios, and the behavior that is most important from the perspective of test data setup and scenario tests.

An entity in the Acceptance test library (ATL) **must** have the following methods:

+ Property methods that are used to get and set entity properties.
+ Fluent setter methods that enable entity properties to be set in a fluent manner.
+ A method that saves the entity to the database.

An entity in ATL *can* have the following methods:

+ Action methods that are used to expose business operations that are relevant to the entity.
+ Query methods that are used to enable navigation to components and related entities.

## Naming convention

`[AtlEntity]<ModuleName><EntityName>`

In this naming convention:

+ `<ModuleName>` is based on the names of the modules in main menu. You should use a short version or an abbreviation to support brevity of test code.
+ `<EntityName>` is based on the user interface (UI) names instead of the table names. For example, use `SalesOrder`, not `SalesTable`.

If an entity has two UI names, it's OK to use the shorter name. For example, you can use `Item` instead of `ReleasedProduct`, because these names are used interchangeably.

### Examples

```xpp
AtlEntitySalesOrder

AtlEntityTransferOrderLine
```

## Property methods

One of the main purposes of a test entity is to expose data. The properties of the entity can be set or retrieved by using `parm` (property) methods.

### Primitive type properties

Create a `parm` method to expose a primitive type property.

#### Example

```xpp
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

If there is a customer entity that is named `AtlEntityCustomer`, for example, a reference to `customer` should be exposed as a property method on the `AtlEntitySalesOrder` entity.

```xpp
public AtlEntityCustomer parmCustomer(AtlEntityCustomer _custTable = null)
```

The property method can be used as either a setter or a getter.

```xpp
salesOrder.parmCustomer(customer); // setter

customer = salesOrder.parmCustomer(); // getter
```

#### Entity reference methods naming conventions

The `parm` prefix should be used to identify property methods. When you expose an entity reference property, use the UI name of the field instead of the Application Object Tree (AOT) name. If the UI name includes the `Id`, `Code`, or `Number` suffix, omit the suffix. For example, use `parmItem` instead of `parmItemNumber`.

### Record references

If the customer entity hasn't yet been created and won't be created in the near future, the reference property should expose the corresponding record buffer (`CustTable`).

```xpp
public CustTable parmCustomer(CustTable _custTable = null)
```

#### Record reference naming conventions

Use the same naming conventions that are used for entity references.

### Id references

In addition to having an entity or record reference, you can introduce the `Id` reference property.

```xpp
public CustAccount customerId(CustAccount _custTable = null)
```

Don't introduce `Id` references unless you also introduce corresponding entity or buffer references. `Id` references are shortcuts to the entity or buffer reference methods. The implementation of `Id` references should delegate the call to the entity or buffer reference.

#### Id reference naming conventions

Use the UI name if it includes terms such as `Id`, `Number`, `Account`, `Code`, or `Name`. Otherwise, add an appropriate suffix to the name of the entity or record reference.

#### Id reference methods contract

The `Id` reference method always uses the provided `Id` to find the referenced entity, and it delegates the call to the entity or record reference method. If no entity or record is found based on the specified `Id` value, an error message is thrown.

## Fluent setter methods

Create fluent setter methods to support the fluent initialization and modification of entities.

### Declaration example

```xpp
public AtlEntitySalesLine setQty(SalesQty _qty)
```
	
### Code example

```xpp
salesLine.setItem(batchItem).setInventDims([warehouse]).setQty(10).save();
```

### Naming convention

`set<PropertyName>`

In this naming convention, `<PropertyName>` should match what is used in the name of the corresponding property method.

## Action methods

Entities represent not only data but also relevant actions. Actions can be implemented either as a simple action method or as a command object initializer.

### Simple action methods

Simple action methods represent a complete action. They should not be fluently chained. The exception is the `save` method, which should be fluent.

#### Naming convention

`<ExecuteBusinessOperation>`

In this naming convention, `<ExecuteBusinessOperation>` is a verb that represents the business operation. It should be the same term that is used on the menu item in the UI.

#### Examples

```xpp
salesOrder.save();

salesOrder.postInvoice();
```

### Command object initializers

Command object initializers return a command object that lets you specify parameters of the command and run it.

```xpp
transferLine.pick().setQty(10).setWMSLocation(bulkLocation).execute();
```

#### Naming convention

`<ExecuteBusinessOperation>`

In this naming convention, `<ExecuteBusinessOperation>` is a verb that represents the business operation. It should be the same term that is used on the menu item in the UI.

#### Examples

```xpp
salesOrder.pick().execute();

purchaseOrder.register().execute();
```

### Action entities

Some actions that are available for an entity can be considered entities themselves. Vendor invoices are one example. Before you post an invoice, you might want to set up parameters of the invoice, edit lines, and save the invoice for later. For these commands, you can introduce a separate entity class.

#### Naming convention

`new<ActionName>`

In this naming convention, `<ActionName>` is a noun that represents the business operation. The name should be the UI name of the business operation.

#### Example

```xpp
receipt = transfer.newReceipt().setEditLines(true).setExplodeLines(true);
receipt.lines().withBatch(batch1).single().setReceiptQty(6).setScrapQty(1).save();
receipt.lines().withBatch(batch2).single().setReceiptQty(4).setScrapQty(1).save();
receipt.post();
```

#### Class naming convention

`AtlEntity<ModuleName><EntityName><ActionName>`

#### Example

```xpp
AtlEntityInventTransferOrderReceipt
```

## Adding components

Composition is a relationship where the composite entity has sole responsibility for the disposition of the component parts. The relationship between the composite and the component is a strong "has a" relationship, because the composite object takes ownership of the component. Therefore, the composite is responsible for creating and destroying the component parts.

An object instance can be part of only one composite. If the composite object is destroyed, all the component parts must be destroyed. The component parts have no independent existence outside the composite object, and they can't be transferred to another object. Composition enforces encapsulation, because the component parts are usually members of the composite object.

An example of a composite object is a source document that is made up of source document lines.

### Example

In the source document example, the document entity serves as the composition root and is responsible for creating any new instances of document lines. In this case, the source document entity will have an `addLine()` method that initializes and returns a new line for the document.


```xpp
public AtlEntitySalesLine addLine()
```

The `addLine()` method adds the line object (`salesLine` in this example) to a collection of lines and returns the parent entity (`SalesOrder` in this example) to preserve the fluency of application programming interfaces (APIs). To create a new line, create a `newLine()` method.

### Naming convention for adding components

Methods for adding components should use the UI names of the buttons.

#### Example

```xpp
salesLine = salesOrder.addLine();
```

### Component collections

You can search for components by using query methods.

#### Naming convention for component collections

Methods for accessing component collections should use the UI names of the grid on the hosting page.

## Query methods

Query methods on an entity let you search for components and related entities.

### Example

```xpp
transferOrderLine = transferOrder.lines().withItem(item).single();
```

In this example, `lines()` is a query method that returns the `AtlQueryTransferOrderLines` query. This query is already filtered so that it returns only transfer order lines for the transfer order that the `lines()` method was called on.

### Naming convention

Use the UI names whenever you can. Abbreviations are acceptable if the UI name is too long to be used in test automation.

### Example

```xpp
public AtlQueryWHSLoadLines lines()
{
    return new AtlQueryWHSLoadLines().forLoadId(this.parmLoadId());
}
```

## Additional resources

[Queries in the Acceptance test library](concepts-queries.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
