---
title: Acceptance test library commands
description: Learn about how to use commands with the Acceptance test library, including overviews on naming conventions, examples, and implementations.
author: MichaelFruergaardPontoppidan
ms.author: mfp
ms.topic: article
ms.date: 03/16/2026
ms.custom: 
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2019-03-27
ms.dyn365.ops.version: App Update 10.0.2
---

# Acceptance test library commands

[!include [banner](../includes/banner.md)]

Command classes run business operations. Use fluent APIs to set the parameters for these operations.

## Naming convention

`AtlCommand<ModuleName><EntityName><ExecuteBusinessOperation>`

In this naming convention:

+ Use a short version or abbreviation of the module name from the main menu for `<ModuleName>`. This choice keeps your test code brief.
+ Use `<EntityName>` when the command applies to different types of entities. This part is optional.
+ Use a verb for `<ExecuteBusinessOperation>` that clearly represents the business operation.

## Examples

```xpp
AtlCommandInventMark

AtlCommandSalesReturnOrderLineRegister
```

## Implementation

Return command objects that implement the `AtlICommand` interface and inherit from the `AtlCommand` class.

Command objects should provide fluent setter methods to set the command parameters.

### Example

```xpp
salesLine.pick().setInventDims([locationOut]).setQty(pickedQty).execute();
```

## Fluent setter methods

Commands support two types of fluent setter methods: `for` methods and `set` methods.

+ **for** – Use these methods for command parameters that represent the entities that the command applies to.

    For example, the invoice command can apply to sales orders. Therefore, use a `for` method to set the sales order that the invoice command applies to.

+ **set** – Use these methods for all other parameters of the command. 

    For example, when you reserve a sales line, you usually specify a quantity. The quantity isn't something that the command applies to but is instead a simple parameter of the command. Therefore, use a `set` method to specify the quantity parameter of the reservation command.

### Naming convention

`for<CommandParameterName>`

`set<CommandParameterName>`

In this naming convention, `<CommandParameterName>` is the name of the parameter that the fluent method sets for the command.

### Examples

```xpp
onHandAdjustment.forItem(item).setQuantity(10).execute();
	
picking.forSalesLine(salesLine).setInventDims([warehouse, batch1]).setQuantity(10).execute();
```


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
