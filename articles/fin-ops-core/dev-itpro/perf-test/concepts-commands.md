---

title: Acceptance test library commands
description: This topic provides information about how to use commands with the Acceptance test library.
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

# Acceptance test library commands

[!include [banner](../includes/banner.md)]

Command classes are responsible for running business operations. They let you use fluent application programming interfaces (APIs) to set the parameters of these operations.

## Naming convention

`AtlCommand<ModuleName><EntityName><ExecuteBusinessOperation>`

In this naming convention:

+ `<ModuleName>` is based on the names of the modules on the main menu. You should use a short version or an abbreviation to support brevity of test code.
+ `<EntityName>` is optional and is used when the command applies to different types of entities.
+ `<ExecuteBusinessOperation>` is a verb that represents the name of the business operation.

## Examples

```xpp
AtlCommandInventMark

AtlCommandSalesReturnOrderLineRegister
```

## Implementation

Command objects that are returned should implement the `AtlICommand` interface and should inherit from the `AtlCommand` class.

Command objects should provide fluent setter methods that are used to set the parameters of the command.

### Example

```xpp
salesLine.pick().setInventDims([locationOut]).setQty(pickedQty).execute();
```

## Fluent setter methods

Commands allow for two types of fluent setter methods, `for` methods and `set` methods:

+ **for** – These methods are used for command parameters that represent the entities that the command applies to.

    For example, the invoice command can apply to sales orders. Therefore, a `for` method is used to set the sales order that the invoice command applies to.

+ **set** – These methods are used for all other parameters of the command. 

    For example, when you reserve a sales line, you usually specify a quantity. The quantity isn't something that the command applies to but is instead a simple parameter of the command. Therefore, a `set` method is used to specify the quantity parameter of the reservation command.

### Naming convention

`for<CommandParameterName>`

`set<CommandParameterName>`

In this naming convention, `<CommandParameterName>` is the name of the parameter that is being set for the command by using the fluent method.

### Examples

```xpp
onHandAdjustment.forItem(item).setQuantity(10).execute();
	
picking.forSalesLine(salesLine).setInventDims([warehouse, batch1]).setQuantity(10).execute();
```


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]