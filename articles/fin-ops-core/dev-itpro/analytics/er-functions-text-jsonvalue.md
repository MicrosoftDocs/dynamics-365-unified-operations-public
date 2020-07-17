---
# required metadata

title: JSONVALUE ER function
description: This topic provides information about how the JSONVALUE Electronic reporting (ER) function is used.
author: NickSelin
manager: kfend
ms.date: 12/11/2019
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

# <a name="JSONVALUE">JSONVALUE ER function</a>

[!include [banner](../includes/banner.md)]

The `JSONVALUE` function parses data in JavaScript Object Notation (JSON) format that is accessed at the specified path, and it extracts a scalar value that has the specified ID. It then returns the extracted scalar value as a *String* value.

## Syntax

```vb
JSONVALUE (input, path)
```

## Arguments

`input`: *String*

The valid path of a data source of the *String* type that contains JSON data.

`path`: *String*

The identifier of a scalar value of JSON data.

## Return values

*String*

The resulting text value.

## Example

The **JsonField** data source contains the following data in JSON format: **{"BuildNumber":"7.3.1234.1", "KeyThumbprint":"7366E"}**. In this case, the expression `JSONVALUE (JsonField, "BuildNumber")` returns the following value of the *String* data type: **"7.3.1234.1"**.

## Additional resources

[Text functions](er-functions-category-text.md)
