---
title: Navigation concepts for test data
description: This topic provides information about how to use navigation to simplify the discoverability of test data generation methods.
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

# Navigation concepts for test data

[!include [banner](../includes/banner.md)]

To simplify the discoverability of generation methods for test data, a set of navigation objects is introduced. For more information about the generation methods, see [Test data methods](test-data-methods.md).

Navigation should start from the root object, the module must be specified, and then the entity must be specified together with the test data methods.

```xpp
data.module().entity().testDataMethod();
```

### Examples

```xpp
modelGroup = data.invent().modelGroups().fifo();

itemBuilder = data.products().items().whsBuilder();

data.sales().salesOrders().ensureCanCreate();

data.invent().parameters().enableQualityManagement();
```

### Advantages

- Discoverability of data creation application programming interfaces (APIs). IntelliSense helps you get to the helper methods that are relevant for the entity.
- Local references to frequently used nodes (for example, `items.whsBuilder()`). Therefore, long names aren't required.

## Root navigation object

The root navigation object is the starting point for finding the test data methods that are required. The root navigation object exposes modules where test data methods are defined.

### Variable naming

The suggested name for variables that reference the navigation root is `data`.

### Class naming

The root class is named `AtlDataRootNode`.

## Module navigation object

The module navigation objects let you group test data methods by relevant modules. Module navigation objects can expose entity navigation objects.

### Navigation node naming

Module names should be based on the names of the modules on the main menu. However, a short version or an abbreviation should be used to support brevity of test code.

#### Examples

- **Sales and marketing** module: `data.sales()`
- **Inventory management** module: `data.invent()`

### Class naming

`AtlData<ModuleName>`

#### Examples

- **Sales and marketing** module: `AtlDataSales`
- **Procurement and sourcing** module: `AtlDataPurch`
- **Inventory management** module: `AtlDataInvent`
- **Accounts receivable** module: `AtlDataCust`
- **Accounts payable** module: `AtlDataVend`

## Entity navigation objects

Entity navigation objects let you group [test data methods](test-data-methods.md) by relevant entities.

### Navigation node naming

The plural of the entity name should be used as the name of the entity navigation node.

#### Examples

```xpp
data.products().items();

data.whs().warehouses();
```

### Class naming 

`AtlData<ModuleName><EntityNamePlural>`

#### Examples

```xpp
AtlDataProductsItems

AtlDataInventChargeGroups
```

### Notes

The same entity navigation object can be exposed from multiple modules when this approach makes sense. For example, `AtlDataProductsItems` is exposed from both `data.product()` and `data.invent()`.

## Helper navigation objects

Sometimes, a [test data method](test-data-methods.md) isn't specific to any entity. In this case, a helpers node can be exposed at the module level. 

### Navigation node naming

The helpers navigation node should be named `helpers`.

#### Examples

```xpp
data.helpers();

data.whs().helpers();
```

### Class naming

`AtlData<ModuleName>Helpers`

#### Examples

```xpp
AtlDataHelpers

AtlDataWHSHelpers
```


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]