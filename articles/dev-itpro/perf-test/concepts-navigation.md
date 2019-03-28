---
# required metadata

title: Navigation concepts
description: This topic provides information about using navigation to simplify the discoverability of test data generation methods.
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

# Navigation concepts

[!include [banner](../includes/banner.md)]

[!include [banner](../includes/preview-banner.md)]

To simplify the discoverability of test data generation methods, a set of navigation objects is introduced. 
For more information about the generation methods, see [Test data generation methods](Concepts_TestDataMethods.md).
Navigation should start from the root object, the module must be specified, and then the entity with the test data methods:

```	
data.module().entity().testDataMethod();
```

### Examples
```
modelGroup = data.invent().modelGroups().fifo();
itemBuilder = data.products().items().whsBuilder();
data.sales().salesOrders().ensureCanCreate();
data.invent().parameters().enableQualityManagement();
```

### Advantages

- Discoverability of data creation APIs. Intellisense helps you to get to the helper methods that are relevant for the entity.
- Local references to frequently used nodes so that long names aren't required. For example, `items.whsBuilder()`.

## Root navigation object
The root navigation object is the starting point when locating the required test data methods. The root navigation object exposes modules with test data methods defined.

### Variable naming
Suggested name for variables referencing the navigation root is `data`. 

### Class naming
The root class is called `AtlDataRootNode`.

## Module navigation object
The module navigation objects allow test data methods to be grouped by relevant modules. Module navigation objects can expose entity navigation objects.

### Navigation node naming
Module names should be based on the names of the modules in main menu. However, a short version or an abbreviation should be used to support brevity of test code.

### Examples

- Sales and marketing -> data.sales()
- Inventory -> data.invent()

### Class naming
`AtlData<ModuleName>`

### Examples:
- AtlDataSales - Sales and marketing module
- AtlDataPurch - Procurement and sourcing module	
- AtlDataInvent - Inventory management module	
- AtlDataCust - Accounts receivable module	
- AtlDataVend - Accounts payable module

## Entity navigation objects
Entity navigation objects allow to group [test data methods](Concepts_TestDataMethods.md) by relevant entities.
### Navigation node naming
Plural of the entity name should be used as the entity navigation node name.
### Examples
```	
data.products().items();
data.whs().warehouses();
```
### Class naming 
`AtlData<ModuleName><EntityNamePlural>`

### Examples	
- AtlDataProductsItems
- AtlDataInventChargeGroups

### Notes
It is allowed to expose the same entity navigation object from multiple modules when it makes sense. For example AtlDataProductsItems is exposed both from data.product() and from data.invent().

## Helper navigation objects
Sometimes a [test data method](Concepts_TestDataMethods.md) is not specific to any entity in particular. In this case a helpers node can be exposed on the module level. 

### Navigation node naming
Helpers navigation node should be called helpers. 

For example:
```
data.helpers();
data.whs().helpers();
```
### Class naming 
`AtlData<ModuleName>Helpers`

### Examples
- AtlDataHelpers
- AtlDataWHSHelpers
