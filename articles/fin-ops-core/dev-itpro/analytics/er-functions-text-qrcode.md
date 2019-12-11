---
# required metadata

title: QRCODE ER function
description: This topic provides information about how the QRCODE Electronic reporting (ER) function is used.
author: NickSelin
manager: kfend
ms.date: 12/10/2019
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

# <a name="QRCODE">QRCODE ER function</a>

[!include [banner](../includes/banner.md)]

The `QRCODE` function returns a *Container* value that presents the Quick Response code (QR code) image for the specified string in binary format.

## Syntax

```
QRCODE (text)
```

## Arguments

`text`: *String*

A *String* value that represents the original text.

## Return values

*Container*

The resulting binary stream.

## Example

You can add the `QRCODE ("Sample text")` expression as a binding of a **Cell** element of an Electronic reporting (ER) format that contains a template that is bound to either an image (for a template in Microsoft Excel format) or a picture content control (for a template in Microsoft Word format) as a placeholder of the QR code image. Then, when the ER format is run, the generated document will contain the corresponding QR code image in the placeholder in the template. For more information, see [Embed images and shapes in documents that you generate by using ER](electronic-reporting-embed-images-shapes.md).

## Additional resources

[Text functions](er-functions-category-text.md)
