---
title: SPLIT ER function
description: This article provides information about how the SPLIT Electronic reporting (ER) function is used.
author: kfend
ms.date: 04/01/2021
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

# SPLIT ER function

[!include [banner](../includes/banner.md)]

The `SPLIT` function splits the specified input string into substrings and returns the result as a new *Record list* value.

## Syntax 1

```vb
SPLIT (input, length)
```

This syntax is used to split the specified input string into substrings, each of which has the specified length.

## Syntax 2

```vb
SPLIT (input, delimiter)
```

This syntax is used to split the specified input string into substrings, based on the specified delimiter.

## Arguments

`input`: *String*

The text to split.

`length`: *Integer*

The maximum length of a single substring.

`delimiter`: *String*

A delimiter that is used to separate substrings.

## Return values

*Record list*

The resulting list of records.

## Usage notes

The record structure of the list that is returned consists of the **Value** field of the *String* type. Every record of the list that is returned contains generated substrings in this field.

If the `delimiter` argument is empty, the new list that is returned consists of one record that has the **Value** field of the *String* type. This field contains the input text.

If the `input` argument is empty, a new empty list is returned. If either the `input` or `delimiter` argument is unspecified (null), an application exception is thrown.

## Example 1

`SPLIT ("abcd", 3)` returns a new list that consists of two records that have the **Value** field of the *String* type. The **Value** field in the first record contains the text **"abc"**, and the **Value** field in the second record contains the text **"d"**.

## Example 2

`SPLIT ("XAb aBy", "aB")` returns a new list that consists of three records that have the **Value** field of the *String* type. The **Value** field in the first record contains the text **"X"**, the **Value** field in the second record contains the text **"&nbsp;"**, and the **Value** field in the third record contains the text **"y"**. 

## Example 3

Yo can use the [INDEX](er-functions-list-index.md) function to access individual elements of the specified input string. If you enter the **MyList** data source of the **Calculated field** type and configure for it the `SPLIT("abc", 1)` expression, the expression `INDEX(MyList,2).Value` returns the text **"b"**.

## Example 4

The [ENUMERATE](er-functions-list-enumerate.md) function can also help you access individual elements of the specified input string. If you first enter the **MyList** data source of the **Calculated field** type and configure for it the `SPLIT("abc", 1)` expression, and then enter the **EnumeratedList** data source of the **Calculated field** type and configure for it the `ENUMERATE(MyList)` expression, the expression `FIRSTORNULL(WHERE(EnumeratedList, EnumeratedList.Number=2)).Value` returns the text **"b"**.

## Additional resources

[List functions](er-functions-category-list.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
