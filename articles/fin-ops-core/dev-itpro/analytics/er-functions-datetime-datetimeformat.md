---
# required metadata

title: DATETIMEFORMAT ER function
description: This topic provides information about how the DATETIMEFORMAT ER function is used.
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

# <a name="DATETIMEFORMAT">DATETIMEFORMAT Function</a>

[!include [banner](../includes/banner.md)]

The `DATETIMEFORMAT` function returns a *String* value that presents a given datetime value as a text in the specified format and an optionally specified [culture](https://docs.microsoft.com/en-us/bingmaps/rest-services/common-parameters-and-types/supported-culture-codes). For information about the supported formats, see [standard](https://msdn.microsoft.com/library/az4se3k1(v=vs.110).aspx) and [custom](https://msdn.microsoft.com/library/8kb3ddd4(v=vs.110).aspx).

## Syntax 1

```
DATETIMEFORMAT (datetime, format)
```

## Syntax 2

```
DATETIMEFORMAT (datetime, format, culture)
```

## Arguments

`datetime` : *DateTime*

A datetime that represents the datetime for formatting.

`format` : *String*

The format of the outputted string.

`culture` : *String*

The culture for formatting.

## Returns

*String*

The result string value.

## Usage notes

When the culture is not defined as an argument of the called function, the value of the culture is defined by the calling context. For example, when the **DATETIMEFORMAT** function is called by using the syntax 1 in an ER format for a **FILE** element configured to use the German culture, the conversion will be performed by using the German culture. The default culture value is EN-US.

The **DATETIMEFORMAT** function converts a given datetime value considering the time zone setting of an application user who is running an ER format in the context of which the function is called.

## Example 1

`DATETIMEFORMAT (NOW(), "dd-MM-yyyy")` returns the current application server datetime, December 24, 2015, as **"24-12-2015"**, based on the specified custom format.

## Example 2

`DATETIMEFORMAT (SESSIONNOW(), "d", "DE")` returns the current application session datetime, December 24, 2015, as **"24.12.2015"**, based on the selected German culture the specified format.

## Example 3

`DATETIMEFORMAT (DATETIMEVALUE( "2019-11-12T09:00:00.0000000-07:00", "O"), "O")` returns the **2019-11-12T08:00:00.0000000-08:00** string value when this function is called in the process that has been initiated by an application user having the **(GMT-08:00) Pacific Time (US & Canada)** time zone value in the **Language and country/region preferences** section.

## Additional resources

[Date and time functions](er-functions-category-datetime.md)
