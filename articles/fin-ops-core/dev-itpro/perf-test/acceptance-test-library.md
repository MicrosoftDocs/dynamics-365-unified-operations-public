---
title: Acceptance test library resources
description: Learn about the Acceptance test library and its benefits, including an example of a test that is written in ATL, concepts, and further reading.
author: MichaelFruergaardPontoppidan
ms.author: mfp
ms.topic: article
ms.date: 07/23/2019
ms.custom: 
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2019-03-27
ms.dyn365.ops.version: App Update 10.0.2
---

# Acceptance test library resources

[!include [banner](../includes/banner.md)]


The Acceptance test library (ATL) is an X++ test library that offers the following benefits:

- It lets you create consistent test data.
- It increases the readability of test code.
- It provides improved discoverability of the methods that are used to create test data.
- It hides the complexity of setting up prerequisites.
- It supports high performance of test cases.

## Example of a test that is written in ATL

```xpp
// Create the data root node
var data = AtlDataRootNode::construct();

// Get a reference to a well-known warehouse 
var warehouse = data.invent().warehouses().default();
 
// Create a new item with the "default" setup using the item creator class. Adjust the default warehouse before saving the item.
var item = items.defaultBuilder().setDefaultWarehouse(warehouse).create();

// Add on-hand (information about availability of the item in the warehouse) by using the on-hand adjustment command.
onHand.adjust().forItem(item).forInventDims([warehouse]).setQty(100).execute();

// Create a sales order with one line using the sales order entity
var salesOrder = data.sales().salesOrders().createDefault();
var salesLine = salesOrder.addLine().setItem(item).setQuantity(10).save();

// Reserve 3 units of the item using the reserve() command that is exposed directly on the sales line entity
salesLine.reserve().setQty(3).execute();

// Verify inventory transactions that are associated with the sales line using the inventoryTransactions query and specifications
salesLine.inventoryTransactions().assertExpectedLines(
    invent.trans().spec().withStatusIssue(StatusIssue::OnOrder).withInventDims([warehouse]).withQty(-7),
    invent.trans().spec().withStatusIssue(StatusIssue::ReservPhysical).withInventDims([warehouse]).withQty(-3)); 
```

## Concepts

The structure and naming of the classes and methods in ATL are quite rigid. This rigidity helps improve discoverability and also makes it easier to write tests, even in domains that you're unfamiliar with.

The classes are grouped into the following concepts:

- [Navigation](concepts-navigation.md) – Discover entities and test data methods in a familiar hierarchy.
- [Test data methods](test-data-methods.md) – These methods are used to set up test data.
- [Entities](concepts-entities.md) – Entities represent data and associated behavior that is perceived as a single unit.
- [Creators](concepts-creators.md) – Creators let you create specific test data.
- [Commands](concepts-commands.md) – Commands run business operations.
- [Queries](concepts-queries.md) – Queries find entities.
- [Specifications](concepts-specifications.md) – Specifications describe expected entities at the end of the test.

## Code generation

Queries and specifications help simplify the process of creating entities. For more information, see [Acceptance test library Code generation wizard](code-generation-wizard.md). The **Code generation** wizard can be used to create scenarios and update them.

## Further reading

Microsoft has used ATL internally for several years, as the foundation for thousands of tests. For more information see, [Best practices for the Acceptance test library](atl-best-practices.md) and [Acceptance test library FAQ](atl-faq.md).


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
