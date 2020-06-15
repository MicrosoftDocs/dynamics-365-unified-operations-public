---
# required metadata

title: GETENUMVALUEBYNAME ER function
description: This topic provides information about how the GETENUMVALUEBYNAME Electronic reporting (ER) function is used.
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

# <a name="GETENUMVALUEBYNAME">GETENUMVALUEBYNAME ER function</a>

[!include [banner](../includes/banner.md)]

The `GETENUMVALUEBYNAME` function searches for a specific *Enum* value in the specified enumeration data source by using the enumeration name that is specified as a *String* value. If the *Enum* value is found, the function returns it. Otherwise, the function returns the **null** enumeration value.

## Syntax

```vb
GETENUMVALUEBYNAME (enumeration data source path, enumeration value text)
```

## Arguments

`enumeration data source path`: *Enumeration*

The valid path of a data source of one of the following enumeration types:

- Electronic reporting (ER) model enumeration
- ER format enumeration
- Microsoft Dynamics 365 Finance enumeration

`enumeration value text`: *String*

A string value that represents the name of a single enumeration value.

## Return values

Nullable *Enum*

The resulting enumeration value.

## Usage notes

No exception is thrown if an *Enum* value isn't found by using the name of the enumeration value that is specified as a *String* value.

## Example

In the following illustration, the **ReportDirection** enumeration is introduced in a data model. Notice that labels are defined for the enumeration values.

<p><a href="./media/ER-data-model-enumeration-values.PNG"><img src="./media/ER-data-model-enumeration-values.PNG" alt="Available values for a data model enumeration" class="alignnone wp-image-290681 size-full" width="397" height="136" /></a>

The following illustration shows these details:

- The **$Direction** data source is configured in an ER report. This data source is configured based on the **ReportDirection** model enumeration.
- The `$IsArrivals` expression is designed to use the model enumeration–based **$Direction** data source as a parameter of this function.
- The value of this comparison expression is **TRUE**.

<a href="./media/ER-data-model-enumeration-usage.PNG"><img src="./media/ER-data-model-enumeration-usage.PNG" alt="Example of data model enumeration" class="alignnone wp-image-290681 size-full" width="397" height="136" /></a>

## Additional resources

[Text functions](er-functions-category-text.md)
