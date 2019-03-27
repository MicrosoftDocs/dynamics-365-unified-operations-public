---
# required metadata

title: Specification classes
description: This topic provides information about specification classes.
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

# Specification classes

[!include [banner](../includes/banner.md)]

[!include [banner](../includes/preview-banner.md)]

A specification class provides fluent APIs for defining the set of criteria that an entity should meet. Specifications are often used in validation scenarios, usually together with query classes. 

Specification classes provide an advantage in that the validation code becomes very concise and expressive. Basically, you are allowed to make a number of validations in a single line of code.

## Naming convention
`AtlSpec<ModuleName><#EntityName>`

Where:
- ModuleName (optional) is based on the names of the modules in main menu. However a short version or an abbreviation should be used to support brevity of test code.
 - EntityName represents the name of the entity that is used throughout ATL.

## Examples
```
AtlSpecWHSLoadLine
AtlSpecWHSWorkLine
````

## Implementation
Specification classes should provide fluent setter methods to specify various criteria of the specification.

### Examples
The following code verifies that the work contains six lines that meet the specified criteria. For example, the first line should have line number 1, work type pick, quantity 1, status closed, and location bulk.
```
work.lines().assertExpectedLines(
    workLines.spec().withLineNum(1).withWorkType(WHSWorkType::Pick).setQuantity(1).setStatus(WHSWorkStatus::Closed).setLocation(locations.bulk()),
    workLines.spec().withLineNum(2).withWorkType(WHSWorkType::Pick).setQuantity(1).setStatus(WHSWorkStatus::Closed).setLocation(locations.floor()),
    workLines.spec().withLineNum(3).withWorkType(WHSWorkType::Put) .setQuantity(2).setStatus(WHSWorkStatus::Closed).setLocation(locations.stage()),
    workLines.spec().withLineNum(4).withWorkType(WHSWorkType::Pick).setQuantity(2).setStatus(WHSWorkStatus::Cancelled).setLocation(locations.stage()),
    workLines.spec().withLineNum(5).withWorkType(WHSWorkType::Put).setQuantity(2).setStatus(WHSWorkStatus::Cancelled)
);
```
