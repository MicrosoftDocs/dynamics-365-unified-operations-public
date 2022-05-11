---
title: Creators in the Acceptance test library
description: This topic provides information about Acceptance test library creators.
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

# Creators in the Acceptance test library

[!include [banner](../includes/banner.md)]

Creator classes provide fluent application programming interfaces (APIs) that are used to create test data.

## Naming convention

`AtlCreator<ModuleName><EntityName>`

In this naming convention:

+ `<ModuleName>` is optional and is based on the names of the modules on the main menu. You should use a short version or an abbreviation to support brevity of test code.
+ `<EntityName>` is optional and is used when the command applies to different types of entities.

## Examples

```xpp
AtlCreatorCostGroup

AtlCreatorCustomer
```

## Fluent setter methods

Creator classes should provide fluent setter methods that are used to set the properties of the entity that is being constructed.

### Naming convention

`set<EntityPropertyName>`

In this naming convention, `<EntityPropertyName>` is the name of the property that is being set for the entity by using the fluent method.

### Example

```xpp
item = new AtlCreatorProductsReleasedVariant()
    .setItemId('DemoItem')
    .setColor(ecoResColor)
    .setStyle(ecoResStyle)
    .setConfig(ecoResConfig)
    .setSize(ecoResSize)
    .create();
```

## When should creators be used instead of entities?

For information that will help you choose between entities and creators, see [Should I implement an entity or a creator class](atl-faq.md#should-i-implement-an-entity-or-a-creator-class).


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]