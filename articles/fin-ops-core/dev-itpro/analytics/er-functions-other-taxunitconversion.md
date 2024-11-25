---
title: TAXUNITCONVERSION ER function
description: Learn about how the TAXUNITCONVERSION Electronic reporting (ER) function is used, including syntax strings, arguments, return values, and examples.
author: johnmichalak
ms.author: epodkolzina
ms.topic: conceptual
ms.date: 03/25/2024
ms.custom: 
  - bap-template
ms.reviewer: johnmichalak
audience: IT Pro
ms.search.region: Global
ms.search.validFrom: 2024-04-26
ms.search.form: ERDataModelDesigner, ERExpressionDesignerFormula, ERMappedFormatDesigner, ERModelMappingDesigner
ms.dyn365.ops.version: App AX10.0.40/Plat Update64
---

# TAXUNITCONVERSION ER function

[!include [banner](../includes/banner.md)]

The `TAXUNITCONVERSION` function returns a *Real* value that represents the quantity result of converting the specified unit from transaction to the specified unit in tax configuration. And it should be noticed that this function requires context that from an original sourcing system. The method `ConverUnit` in interface `IExternalAPIProvider` must be implemented in a sourcing Enterprise resource planning (ERP) environment.

## Syntax

```vb
TAXUNITCONVERSION(itemId, quantity, base unit, tax unit, invent dimension ID, packaging)
```

## Arguments

`itemId`: *String*

The Item ID defined in Finance and Operations Apps.

`quantity`: *Real*

The quantity of the original unit.

`base unit`: *String*

The unit of the original transaction.

`tax unit`: *String*

The unit is defined in the tax configuration.

`invent dimension Id`: *String*

The **invent dimension** is defined in the finance and operations apps transaction.

`packaging`: *Bool*

The packaging parameter is from the tax configuration.


## Return values

*Real*

The converted quantity of the tax unit.

## Example

`TAXUNITCONVERSION ("D001", 12, "ea", "dz", "", false)` returns the quantity converted from **"ea"** to **"dz"** which is **1**.

## Additional resources

[Other (business domain–specific) functions](er-functions-category-other.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
