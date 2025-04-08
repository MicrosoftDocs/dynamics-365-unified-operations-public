---
title: Specification classes
description: Learn about specification classes, including overviews of naming conventions, implementations, and code examples.
author: MichaelFruergaardPontoppidan
ms.author: mfp
ms.topic: article
ms.date: 03/27/2019
ms.custom: 
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2019-03-27
ms.dyn365.ops.version: App Update 10.0.2
---

# Specification classes

[!include [banner](../includes/banner.md)]

A specification class provides fluent application programming interfaces (APIs) that are used to define the set of criteria that an entity should meet. Specifications are often used in validation scenarios. They are usually used together with query classes.

An advantage of specification classes is that the validation code becomes very concise and expressive. Basically, you can do multiple validations in a single line of code.

## Naming convention

`AtlSpec<ModuleName><#EntityName>`

In this naming convention:

- `<ModuleName>` is optional and is based on the names of the modules on the main menu. However, a short version or an abbreviation should be used to support brevity of test code.
- `<#EntityName>` represents the name of the entity that is used throughout the Acceptance test library (ATL).

## Examples

```Console
AtlSpecWHSLoadLine

AtlSpecWHSWorkLine
```

## Implementation

Specification classes should provide fluent setter methods to specify various criteria of the specification.

### Example

The following code verifies that the work contains six lines that meet the specified criteria. For example, the first line should have **1** as the line number of **1**, **Pick** as the work type, **1** as the quantity, **Closed** as the status, and **bulk** as the location.

```xpp
work.lines().assertExpectedLines(
    workLines.spec().withLineNum(1).withWorkType(WHSWorkType::Pick).setQuantity(1)
        .setStatus(WHSWorkStatus::Closed).setLocation(locations.bulk()),
    workLines.spec().withLineNum(2).withWorkType(WHSWorkType::Pick).setQuantity(1)
        .setStatus(WHSWorkStatus::Closed).setLocation(locations.floor()),
    workLines.spec().withLineNum(3).withWorkType(WHSWorkType::Put)
        .setQuantity(2).setStatus(WHSWorkStatus::Closed).setLocation(locations.stage()),
    workLines.spec().withLineNum(4).withWorkType(WHSWorkType::Pick).setQuantity(2)
        .setStatus(WHSWorkStatus::Cancelled).setLocation(locations.stage()),
    workLines.spec().withLineNum(5).withWorkType(WHSWorkType::Put).setQuantity(2).setStatus(WHSWorkStatus::Cancelled)
);
```


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
