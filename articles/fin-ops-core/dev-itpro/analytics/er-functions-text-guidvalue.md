---
# required metadata

title: GUIDVALUE ER function
description: This topic provides information about how the GUIDVALUE Electronic reporting (ER) function is used.
author: NickSelin
manager: kfend
ms.date: 12/12/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

ms.search.form: ERDataModelDesigner, ERExpressionDesignerFormula, ERMappedFormatDesigner, ERModelMappingDesigner
# ROBOTS: 
audience: Application User, IT Pro
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 58771
ms.assetid: 24223e13-727a-4be6-a22d-4d427f504ac9
ms.search.region: Global
# ms.search.industry: 
ms.author: nselin
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# <a name="GUIDVALUE">GUIDVALUE ER function</a>

[!include [banner](../includes/banner.md)]

The `GUIDVALUE` function converts the specified input of the *String* type to a data item of the *GUID* type.

## Syntax

```
GUIDVALUE (input)
```

## Arguments

`input`: *String*

The valid path of a data source of the *String* type.

## Return values

*GUID*

The resulting globally unique identifier (GUID) value.

## Usage notes

To do a conversion in the opposite direction (that is, to convert specified input of the *GUID* data type to a data item of the *String* data type), you can use the [TEXT](er-functions-text-text.md) function.

## Example

You define the following data sources in your model mapping:

- A **myID** data source of the *Calculated field* type that contains the expression `GUIDVALUE ("AF5CCDAC-F728-4609-8C8B- A4B30B0C0AA0")`
- A **Users** data source of the *Table records* type that refers to the UserInfo table

You can then use an expression such as `FILTER (Users, Users.objectId = myID)` to filter the UserInfo table by the **objectId** field of the *GUID* data type.

## Additional resources

[Text functions](er-functions-category-text.md)
