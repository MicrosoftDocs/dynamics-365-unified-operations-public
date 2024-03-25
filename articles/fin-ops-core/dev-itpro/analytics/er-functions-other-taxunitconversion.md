---
title: TAXUNITCONVERSION ER function
description: This article provides information about how the TAXUNITCONVERSION Electronic reporting (ER) function is used.
author: johnmichalak
ms.date: 03/25/2024
ms.prod: 
ms.technology: 
audience: IT Pro
ms.reviewer: johnmichalak
ms.search.region: Global
ms.author: epodkolzina
ms.search.validFrom: 2024-04-26
ms.dyn365.ops.version: App AX10.0.40/Plat Update64
ms.assetid: 
ms.search.form: ERDataModelDesigner, ERExpressionDesignerFormula, ERMappedFormatDesigner, ERModelMappingDesigner
---

# TAXUNITCONVERSION ER function

[!include [banner](../includes/banner.md)]

The `TAXUNITCONVERSION` function returns a *Real* value that represents the quantity result of converting the specified unit from transaction to the specified unit in tax configuration. And it should be noticed that this function requires context that from an original sourcing system. The method `ConverUnit` in interface `IExternalAPIProvider` must be implemented in a sourcing ERP environment.

## Syntax

```vb
TAXUNITCONVERSION(itemId, quantity, base unit, tax unit, invent dimension Id, packaging)
```

## Arguments

`itemId`: *String*

The Item Id defined in Finance and Operations Apps.

`quantity`: *Real*

The quantity of original unit.

`base unit`: *String*

The unit of original transaction.

`tax unit`: *String*

The unit defined in tax configuration.

`invent dimension Id`: *String*

The invent dimension defined in Finance and Operations Apps transaction.

`packaging`: *Bool*

The packaging parameter from tax configuration.


## Return values

*Real*

The converted quantity of tax unit.

## Example

`TAXUNITCONVERSION ("D001", 12, "ea", "dz", "", false)` returns the quantity converted from **ea** to **dz** which is **1**.

## Additional resources

[Other (business domain–specific) functions](er-functions-category-other.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
