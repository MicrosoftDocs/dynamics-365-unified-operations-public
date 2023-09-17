---
title: GETLABELTEXT ER function
description: This article provides information about how the GETLABELTEXT Electronic reporting (ER) function is used.
author: kfend
ms.date: 03/18/2022
ms.prod: 
ms.technology: 
audience: Application User, IT Pro
ms.reviewer: kfend
ms.search.region: Global
ms.author: filatovm
ms.search.validFrom: 2022-01-01
ms.dyn365.ops.version: AX 10.0.25
ms.assetid: 24223e13-727a-4be6-a22d-4d427f504ac9
ms.search.form: ERDataModelDesigner, ERExpressionDesignerFormula, ERMappedFormatDesigner, ERModelMappingDesigner
---

# GETLABELTEXT ER function

[!include [banner](../includes/banner.md)]

The `GETLABELTEXT` function searches for a specific label to return a *[String](er-formula-supported-data-types-primitive.md#string)* value that represents the translation of the specified label in the specified language.

## Syntax

```vb
GETLABELTEXT (label id, language)
```

## Arguments

### Label ID

`label id`: *String* or *Label Id*

The valid ID of one of the following label types:

- [Electronic reporting (ER)](general-electronic-reporting.md) label
- Microsoft Dynamics 365 Finance label

#### Usage notes

This argument can be defined only as a constant, by using one of the following supported patterns:

- For ER labels:

    - `@"GER_LABEL:<LABEL ID>"`
    - `"GER_LABEL:<LABEL ID>"`

- For Finance labels:

    - `@"<LABEL ID>"`
    - `"<LABEL ID>"`

> [!NOTE]
> At design time, a validation error message is shown on the **[Formula designer](er-advanced-formula-editor.md)** page if no label can be found by using the provided label ID.

### Language

`language`: *String*

A string that represents a language code.

#### Usage notes

This argument can be defined either as a text constant or as the path of a data source field that returns a *String* value.

> [!NOTE]
> At design time, a validation error message is shown if no language code can be found by using the provided `language` argument when it has been defined as a text constant.
>
> At runtime, the translation for the `EN-US` system language is returned for a specified label if no language code has been found by using the provided `language` argument.

## Return values

*String*

The resulting text value.

## <a name=example-1></a>Example 1: System label

The expressions `GETLABELTEXT (@"SYS70894", "en-us")` and `GETLABELTEXT ("SYS70894", "en-us")` return the English translation "Nothing to print" for the `@SYS70894` application label.

## <a name=example-2></a>Example 2: ER label

You start to edit an ER [configuration](general-electronic-reporting.md#Configuration) that has been [derived](er-quick-start2-customize-report.md#DeriveProvidedFormat) from the **ISO20022 Credit transfer (DE)** configuration, enter a new data source of the *[Calculated field](er-calculated-field-ds-performance.md)* type, and configure the expression `GETLABELTEXT(@"GER_LABEL:VendorName", "de")` for this data source. In this case, at runtime, the data source returns the German translation "Kreditorenname" for the `@GER_LABEL:VendorName` ER label that was initially configured in the base **ISO20022 Credit transfer (DE)** ER configuration.

## Additional resources

[Text functions](er-functions-category-text.md)

[Design multilingual reports in Electronic reporting](er-design-multilingual-reports.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
