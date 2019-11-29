---
# required metadata

title: QRCODE ER function
description: This topic explains how the QRCODE ER function is used
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

# <a name="QRCODE">QRCODE Function</a>

[!include [banner](../includes/banner.md)]

The `QRCODE` function returns a *Container* value of the Quick Response Code (QR code) image in binary format for the specified string.

## Syntax

```
QRCODE (text)
```

## Arguments

`text` : *String*

A *String* value representing the original text.

## Returns

*Container*

The result binary stream.

## Example

You can add the `QRCODE ("Sample text")` expression as a binding of a **Cell** element of an ER format containing a template that is bound to either an image (for a template in Excel format) or to a picture content control (for a
template in Word format) as a placeholder of the QR code image. When such ER format is executed, the generated document will contain the corresponding QR code image in its placeholder in using template. See [Embed images and shapes in
documents that you generate by using
ER](electronic-reporting-embed-images-shapes.md) for more details.

## Additional resources

[Text functions](er-functions-category-text.md)
