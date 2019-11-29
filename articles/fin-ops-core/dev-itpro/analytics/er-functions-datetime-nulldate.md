---
# required metadata

title: NULLDATE ER function
description: This topic explains how the NULLDATE ER function is used
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

# <a name="NULLDATE">NULLDATE Function</a>

[!include [banner](../includes/banner.md)]

The `NULLDATE` function returns a *Date* value of the **null** date (Jan 1st, 1900).

## Syntax

```
NULLDATE () as 
```

## Returns

*Date*

The result date value.

## Example 1

`DATEFORMAT (NULLDATE()**, **"yyyy-MM-dd")` returns the **null** date, January 1st, 1900, as **"1900-01-01"**, based on the specified custom format.

## Example 2

`IF( Invoice.DocumentDate = NULLDATE(), true, false)` expression returns **True** when the value of the **DocumentDate** field equals the **null** date. In this example, **Invoice** is an ER data source of the **Finance/Table records** type and refers to the **CustInvoiceJour** table.

## Additional resources

[Date and time functions](er-functions-category-datetime.md)
