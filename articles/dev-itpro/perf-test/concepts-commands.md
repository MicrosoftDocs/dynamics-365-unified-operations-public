
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

Command classes are responsible for executing business operations and allow setting parameters of these operations using fluent APIs.

## Naming convention
The naming convention is:

`AtlCommand<ModuleName><EntityName><ExecuteBusinessOperation>`

+ `ModuleName` is based on the names of the modules in main menu. You should use a short version or an abbreviation to support brevity of test code.
+ `EntityName` is optional and used in case the command applies to different types of entities.
+ `ExecuteBusinessOperation` is a verb that represents the name of the business operation.

## Example
```
AtlCommandInventMark
AtlCommandSalesReturnOrderLineRegister
```

## Implementation
Command objects that are returned should implement the `AtlICommand` interface. It's preferable to inherit from the `AtlCommand` class.

Command objects should provide [fluent setter methods](#fluent-setters) for setting parameters of the command.

### Example
```
salesLine.pick().setInventDims([locationOut]).setQty(pickedQty).execute();
```

## Fluent setters
Commands allow two types of fluent setter methods:

+ `for` methods are used for command parameters that represent the entities that the command applies to. For example, the invoice command can apply to sales orders thus a `for` method would be used to set the sales order that the invoice command applies to.
+ `set` methods are used for all other parameters of the command. For example, when you are reserving a sales line you usually specify quantity. Quantity is not something that the command applies to but rather a simple parameter of the command. Thus a `set` method would be used to specify the quantity parameter of the reservation command.

### Naming convention
The naming convention is:

`for<CommandParameterName>`

`set<CommandParameterName>`

`CommandParameterName` is the name of the parameter of the command that is being set using the fluent method.

### Example
```
onHandAdjustment.forItem(item).setQuantity(10).execute();
	
picking.forSalesLine(salesLine).setInventDims([warehouse, batch1]).setQuantity(10).execute();
```
