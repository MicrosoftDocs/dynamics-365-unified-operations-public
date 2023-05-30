---
title: QRCODE ER function
description: This article provides information about how the QRCODE Electronic reporting (ER) function is used.
author: kfend
ms.date: 12/10/2019
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

# QRCODE ER function

[!include [banner](../includes/banner.md)]

The `QRCODE` function returns a *Container* value that presents the Quick Response code (QR code) image for the specified string in binary format.

## Syntax

```vb
QRCODE (text)
```

## Arguments

`text`: *String*

A *String* value that represents the original text.

## Return values

*Container*

The resulting binary stream.

## Example

You can configure an Electronic reporting (ER) format to generate an outbound document in Microsoft Office format (Excel workbooks or Word documents) by using a predefined template. This template may contain a **Picture** object (Excel workbook) or a **Picture Content Control** (Word document) as a placeholder for a QR code image. You need to add to the configured ER format a **Cell** element that will be used to fill this placeholder in. To specify what information will be stored in a QR code, you need to define a binding for this **Cell** element. For example, you can configure such binding as containing the following expression:

```vb
QRCODE (model.ListOfShelfLabels.LabelText)`
```

When you run the configured ER format, the text value of the **LabelText** field of the **model.ListOfShelfLabels** data source will be used to generate a QR code image. This image will replace a QR code image placeholder in the document template using to generate an outbound document. When this image of the generated document is scanned, it returns the text that was taken from the **LabelText** field of the **model.ListOfShelfLabels** data source. For more information, see [Embed images and shapes in documents that you generate by using ER](electronic-reporting-embed-images-shapes.md).

## Additional resources

[Text functions](er-functions-category-text.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
