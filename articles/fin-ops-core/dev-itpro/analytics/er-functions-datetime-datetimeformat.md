---
# required metadata

title: DATETIMEFORMAT ER function
description: This topic provides information about how the DATETIMEFORMAT Electronic reporting (ER) function is used.
author: NickSelin
manager: kfend
ms.date: 12/03/2019
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

# <a name="DATETIMEFORMAT">DATETIMEFORMAT ER function</a>

[!include [banner](../includes/banner.md)]

The `DATETIMEFORMAT` function returns a *String* value that presents a given date/time value as text in the specified format and in an optionally specified [culture](https://docs.microsoft.com/bingmaps/rest-services/common-parameters-and-types/supported-culture-codes). For information about the supported formats, see [standard](https://msdn.microsoft.com/library/az4se3k1(v=vs.110).aspx) and [custom](https://msdn.microsoft.com/library/8kb3ddd4(v=vs.110).aspx).

## Syntax 1

```ER expression
DATETIMEFORMAT (datetime, format)
```

## Syntax 2

```ER expression
DATETIMEFORMAT (datetime, format, culture)
```

## Arguments

`datetime`: *DateTime*

A date/time value that represents the date and time to format.

`format`: *String*

The format of the output string.

`culture`: *String*

The culture to use for formatting.

## Return values

*String*

The resulting string value.

## Usage notes

When the culture isn't defined as an argument of the called function, the value of `culture` is defined by the calling context. For example, if the `DATETIMEFORMAT` function is called by using syntax 1 in an Electronic reporting (ER) format for a **FILE** element that is configured to use the German culture, the conversion will be done by using the German culture. The default `culture` value is **EN-US**.

When the `DATETIMEFORMAT` function converts a given date/time value, it considers the time zone setting of the application user who is running the ER format that the function is called in the context of.

## Example 1

`DATETIMEFORMAT (NOW(), "dd-MM-yyyy")` returns the current application server date/time value, December 24, 2015, as **"24-12-2015"**, based on the specified custom format.

## Example 2

`DATETIMEFORMAT (SESSIONNOW(), "d", "DE")` returns the current application session date/time value, December 24, 2015, as **"24.12.2015"**, based on the selected German culture and the specified format.

## Example 3

`DATETIMEFORMAT (DATETIMEVALUE( "2019-11-12T09:00:00.0000000-07:00", "O"), "O")` returns the string value **2019-11-12T08:00:00.0000000-08:00** when it's called during a process that was initiated by an application user who has the time zone value **(GMT-08:00) Pacific Time (US & Canada)** in the **Language and country/region preferences** section.

## Additional resources

[Date and time functions](er-functions-category-datetime.md)
