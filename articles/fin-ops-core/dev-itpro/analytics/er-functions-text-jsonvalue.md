---
title: JSONVALUE ER function
description: This article provides information about how the JSONVALUE Electronic reporting (ER) function is used.
author: kfend
ms.date: 10/25/2021
ms.prod: 
ms.technology: 
audience: Application User, IT Pro
ms.reviewer: kfend
ms.search.region: Global
ms.author: filatovm
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 24223e13-727a-4be6-a22d-4d427f504ac9
ms.search.form: ERDataModelDesigner, ERExpressionDesignerFormula, ERMappedFormatDesigner, ERModelMappingDesigner
---

# JSONVALUE ER function

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

The identifier of a scalar value of JSON data. Use a forward slash (/) to separate the names of related JSON nodes. Use the bracket (\[\]) notation to specify the index of a particular value in a JSON array. Note that zero-based numbering is used for this index.

## Return values

*String*

The resulting text value.

## Example 1

The **JsonField** data source contains the following data in JSON format: **{"BuildNumber":"7.3.1234.1", "KeyThumbprint":"7366E"}**. In this case, the expression `JSONVALUE (JsonField, "BuildNumber")` returns the following value of the *String* data type: **"7.3.1234.1"**.

## Example 2

The **JsonField** data source of the *Calculated field* type contains the following expression: `"{""workers"": [ {""name"": ""Adam"", ""age"": 30, ""emails"": [""AdamS@Contoso.com"", ""AdamS@Hotmail.com"" ]}, { ""name"": ""John"", ""age"": 21, ""emails"": [""JohnS@Contoso.com"", ""JohnS@Aol.com""]}]}"`

This expression configured to return a [*String*](er-formula-supported-data-types-primitive.md#string) value that represents the following data in JSON format.

```json
{
    "workers": [
        {
            "name": "Adam",
            "age": 30,
            "emails": [ "AdamS@Contoso.com", "AdamS@Hotmail.com" ]
        },
        {
            "name": "John",
            "age": 21,
            "emails": [ "JohnS@Contoso.com", "JohnS@Aol.com" ]
        }
    ]
}
```

In this case, the expression `JSONVALUE(json, "workers/[1]/emails/[0]")` returns the following value of the *String* data type: `JohnS@Contoso.com`.

## Additional resources

[Text functions](er-functions-category-text.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
