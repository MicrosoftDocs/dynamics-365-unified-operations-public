---
# required metadata

title: JSONVALUE ER function
description: This topic explains how the JSONVALUE ER function is used
author: NickSelin
manager: kfend
ms.date: 11/29/2019
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

# <a name="JSONVALUE">JSONVALUE Function</a>

[!include [banner](../includes/banner.md)]

The `JSONVALUE` function returns a *String* value as the result of parsing data in JavaScript Object Notation (JSON) format that is accessed by the specified path to extract a scalar value that is based on the specified ID.

## Syntax

```
JSONVALUE (input, path)
```

## Arguments

`input`: *String*

A valid path to a data source of the *String* type containing JSON data.

`path` : *String*

An identification of a scalar value of JSON data.

## Returns

*String*

The result text value.

## Example

If the data source **JsonField** contains the **{"BuildNumber":"7.3.1234.1", "KeyThumbprint":"7366E"}** data in JSON format, the expression `JSONVALUE (JsonField, "BuildNumber")` returns the value **“7.3.1234.1”** of the *String* data type.

## Additional resources

[Text functions](er-functions-category-text.md)
