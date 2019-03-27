---
# required metadata

title: Acceptance test library creators
description: This topic provides information about acceptance test library creators.
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

# Acceptance test library creators

[!include [banner](../includes/banner.md)]

[!include [banner](../includes/preview-banner.md)]

# Creators
Creator classes provide fluent APIs for creating test data. 

## Naming convention
The naming convention is:

```AtlCreator<ModuleName><EntityName>```

+ `ModuleName` (optional) is based on the names of the modules in main menu. You should use a short version or an abbreviation to support brevity of test code.
+ `EntityName` (optional) is used when the command applies to different types of entities.

## Examples
```
AtlCreatorCostGroup
AtlCreatorCustomer
```

## Fluent setter methods
Creator classes should provide fluent setter methods for setting the properties of the entity that is being constructed.

Creators should provide fluent `set` methods for the properties of the entity that is being constructed.

### Naming convention
```set<EntityPropertyName>```

`EntityPropertyName` is the name of the property of the entity that is being set using the fluent method.

### Example
```
item = new AtlCreatorProductItem()
        .setItemId('DemoItem')
        .setItemGroup(invent.itemGroups().carAudio())
        .setItemModelGroup(invent.modelGroups().fifo())                           
        .setStorageDimGroup(invent.storageDimGroups().siteWarehousePhysical())
        .setTrackingDimGroup(invent.trackingDimGroups().serialControlled())
        .setDefaultWarehouse(invent.warehouses().default())
        .create();

```

#### When creators should be used instead of entites?
To choose between entities and creators, read [Should I implement an Entity or a Creator class](atl-faq#should-i-implement-an-entity-or-a-creator-class).
