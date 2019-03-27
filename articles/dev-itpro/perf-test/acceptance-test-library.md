---
# required metadata

title: Acceptance test library
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

# Acceptance test library

[!include [banner](../includes/banner.md)]

The Acceptance test library (ATL) is an X++ test library that:

- Allows you to create consistent test data.
- Increases the readability of test code.
- Provides improved discoverability of the methods used to create test data.
- Hides the complexity of setting up prerequisites.
- Supports high test case performance.

## Example of a test written in the ATL

```
// Get a reference to a well-known warehouse 
var warehouse = data.invent().warehouses().default();
 
// Create a new item with the "default" setup using the item creator class. Adjust the default warehouse before saving the item.
var item = items.defaultBuilder().setDefaultWarehouse(warehouse).create();
        
// Add  on-hand (information about availability of the item in the warehouse) by using the on-hand adjustment command.
onHand.adjust().forItem(item).forInventDims([warehouse]).setQty(100).execute();
        
// Create a sales order with one line using the sales order entity
var salesOrder = data.sales().salesOrders().createDefault();
var salesLine = salesOrder.addLine().setItem(item).setQuantity(10).save();
        
// Reserve 3 units of the item using the reserve() command that is exposed directly on the sales line entity
salesLine.reserve().setQty(3).execute();
        
// Verify inventory transactions that are associated with the sales line using the inventoryTransactions query and specifications
salesLine.inventoryTransactions().assertExpectedLines(
    invent.trans().spec().withStatusIssue(StatusIssue::OnOrder).withInventDims([warehouse]).withQty(-3),
    invent.trans().spec().withStatusIssue(StatusIssue::ReservPhysical).withInventDims([warehouse]).withQty(-7)); 
```

## Concepts
The structure and naming of the classes and methods in the ATL is quite rigid. This increases discoverability and makes it easier to write tests even in domains you are not familiar with. The classes are grouped in these concepts.
- [Navigation](Concepts_Navigation.md)
    
    Discover entities and test data methods in a familiar hierarchy.
- [Test data methods](Concepts_TestDataMethods.md)
    
    Methods to setup test data.
- [Entities](Concepts_Entities.md)
    
    Entities represents data and associated behavior that is perceived as a single unit.
- [Creators](Concepts_Creators.md)

    Creator allow creating specific test data.
- [Commands](Concepts_Commands.md)

    Commands execute business operations.
- [Queries](Concepts_Queries.md)

    Queries finds entities.    
- [Specifications](Concepts_Specifications.md)

    Specifications describe expected entities at the end of the test.

## Code generation
To simplify creating entities, queries and specifications exist. For more information, see [Code generation wizard](code-generation-wizard.md). Creating and updating scenarios are supported by the code generation wizard.

## Further reading
ATL has been used internally by Microsoft for several years as the foundation for thousands of tests. For information see, [Best practices for the Acceptance test library](atl-best-practices.md) and [Frequently asked questions](atl-faq.md).
