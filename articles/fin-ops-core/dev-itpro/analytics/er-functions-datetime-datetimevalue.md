---
# required metadata

title: DATETIMEVALUE ER function
description: This topic provides information about how the DATETIMEVALUE Electronic reporting (ER) function is used.
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

# <a name="DATETIMEVALUE">DATETIMEVALUE ER function</a>

[!include [banner](../includes/banner.md)]

The `DATETIMEVALUE` function returns a *DateTime* value that is converted from a given text value in the specified format and in an optionally specified [culture](https://docs.microsoft.com/bingmaps/rest-services/common-parameters-and-types/supported-culture-codes) to a date/time value. For information about the supported formats, see [standard](https://msdn.microsoft.com/library/az4se3k1(v=vs.110).aspx) and [custom](https://msdn.microsoft.com/library/8kb3ddd4(v=vs.110).aspx).

## Syntax 1

```ER expression
DATETIMEVALUE (text, format)
```

## Syntax 2

```ER expression
DATETIMEVALUE (text, format, culture)
```

## Arguments

`text`: *String*

Text that represents the value to format.

`format`: *String*

The format of the given text.

`culture`: *String*

The culture that is used for formatting of the given text.

## Return values

*DateTime*

The resulting date/time value.

## Usage notes

When the culture isn't defined as an argument of the called function, the value of `culture` is defined by the calling context. For example, if the `DATETIMEVALUE` function is called by using syntax 1 in an Electronic reporting (ER) format for a **FILE** element that is configured to use the German culture, the conversion will be done by using the German culture. The default `culture` value is **EN-US**.

## Example 1

`DATETIMEVALUE ("21-Dec-2016 02:55:00", "dd-MMM-yyyy hh:mm:ss")` returns **2:55:00 AM on December 21, 2016**, based on the specified custom format and the default application's **EN-US** culture.

## Example 2

`DATETIMEVALUE ("21-Gen-2016 02:55:00", "dd-MMM-yyyy hh:mm:ss", "IT")` returns **2:55:00 AM on December 21, 2016**, based on the specified custom format and culture.

However, `DATETIMEVALUE ("21-Gen-2016 02:55:00", "dd-MMM-yyyy hh:mm:ss", "EN-US")` throws an exception to inform the user that the specified string isn't recognized as a valid date/time value for the specified culture.

## Additional resources

[Date and time functions](er-functions-category-datetime.md)
