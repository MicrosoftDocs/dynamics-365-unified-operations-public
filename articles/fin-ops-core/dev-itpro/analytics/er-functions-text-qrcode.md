---
title: QRCODE ER function
description: Learn about how the QRCODE Electronic reporting (ER) function is used, including syntax strings, arguments, return values, and examples.
author: kfend
ms.author: filatovm
ms.topic: article
ms.date: 04/08/2026
ms.reviewer: johnmichalak
audience: IT Pro
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.search.form: ERDataModelDesigner, ERExpressionDesignerFormula, ERMappedFormatDesigner, ERModelMappingDesigner
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 24223e13-727a-4be6-a22d-4d427f504ac9
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

You can configure an Electronic reporting (ER) format to generate an outbound document in Microsoft Office format (Excel workbooks or Word documents) by using a predefined template. This template might contain a **Picture** object (Excel workbook) or a **Picture Content Control** (Word document) as a placeholder for a QR code image. Add a **Cell** element to the configured ER format that fills this placeholder. To specify what information the QR code stores, define a binding for this **Cell** element. For example, you can configure the binding to contain the following expression:

```vb
QRCODE (model.ListOfShelfLabels.LabelText)`
```

When you run the configured ER format, the text value of the **LabelText** field of the **model.ListOfShelfLabels** data source generates a QR code image. This image replaces a QR code image placeholder in the document template that you use to generate an outbound document. When you scan this image of the generated document, it returns the text that was taken from the **LabelText** field of the **model.ListOfShelfLabels** data source. For more information, see [Embed images and shapes in documents that you generate by using ER](electronic-reporting-embed-images-shapes.md).

## Additional resources

[Text functions](er-functions-category-text.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
