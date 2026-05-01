---
title: Creators in the Acceptance test library
description: Learn about Acceptance test library creators, including naming conventions, code examples, and fluent setter methods.
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

# Creators in the Acceptance test library

[!include [banner](../includes/banner.md)]

Creator classes provide fluent application programming interfaces (APIs) that you can use to create test data.

## Naming convention

`AtlCreator<ModuleName><EntityName>`

In this naming convention:

+ `<ModuleName>` is optional. Use the names of the modules on the main menu. Use a short version or an abbreviation to keep test code brief.
+ `<EntityName>` is optional. Use it when the command applies to different types of entities.

## Examples

```xpp
AtlCreatorCostGroup

AtlCreatorCustomer
```

## Fluent setter methods

Creator classes should provide fluent setter methods that set the properties of the entity that you're constructing.

### Naming convention

`set<EntityPropertyName>`

In this naming convention, `<EntityPropertyName>` is the name of the property that the fluent method sets for the entity.

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

## When should you use creators instead of entities?

For information that helps you choose between entities and creators, see [Should I implement an entity or a creator class](atl-faq.md#should-i-implement-an-entity-or-a-creator-class).


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
