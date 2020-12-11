---
# required metadata

title: Base64StringToContainer ER function
description: This topic provides information about how the Base64StringToContainer Electronic reporting (ER) function is used.
author: NickSelin
manager: kfend
ms.date: 12/12/2020
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
# ms.tgt_pltfrm: 
ms.custom: 58771
ms.assetid: 24223e13-727a-4be6-a22d-4d427f504ac9
ms.search.region: Global
# ms.search.industry: 
ms.author: nselin
ms.search.validFrom: 2020-12-01
ms.dyn365.ops.version: 10.0.17

---

# BASE64STRINGTOCONTAINER ER function

[!include [banner](../includes/banner.md)]

The `BASE64STRINGTOCONTAINER` [function](er-formula-language.md#functions) converts the specified input of the *String* type to a data item of the [*Container*](er-functions-category-container.md) type.

## Syntax

```vb
BASE64STRINGTOCONTAINER (input)
```

## Arguments

`input`: *String*

The valid path of a data source of the *String* type.

## Return values

*Container*

The resulting binary value in binary large object (BLOB) format.

## Usage notes

The **Parameter is not valid exception** is thrown when the input string does not provide a correct Base64 group of binary-to-text encoding schemes.

## Example

You define the following data sources in your model mapping:

- The root **DocuTypeGroupEnum** data source of the *Dynamics 365 for Operations / Enumeration* type that refers to the **DocuTypeGroup** application enumeration
- The root **Customer** data source of the *Dynamics 365 for Operations / Table records* type that refers to the **CustTable** application table
- The **#Media** data source of the *Calculated field* type that is configured as follows:
    - Added as a child data source of the **Customer** data source
    - Containing the `WHERE(@.'<Relations'.'<Documents', @.'<Relations'.'<Documents'.'docuType()'.TypeGroup = DocuTypeGroupEnum.Image)` expression
- The **#MediaAsBase64String** data source of the *Calculated field* type that is configured as follows:
    - Added as a child data source of the **Customer.'#Media'** data source
    - Containing the `Customer.'#Media'.'getFileContentAsBase64String()'` expression
- The **#BlobFomBase64** data source of the *Calculated field* type that is configured as follows:
    - Added as a child data source of the **Customer.'#Media'** data source
    - Containing the `Base64StringToContainer(Customer.'#Media'.'#MediaAsBase64String')'` expression

The **#MediaAsBase64String** data source will encode the binary content of the current media attachment to text representing a Base64 group of binary-to-text encoding schemes.
The **#BlobFomBase64** data source will decode the Base64 string returning a binary value in BLOB format.

![ER model mapping designer page presenting saple data sources](./media/er-functions-container-base64stringtocontainer-1.png)

## Additional resources

[Container functions](er-functions-category-container.md)
