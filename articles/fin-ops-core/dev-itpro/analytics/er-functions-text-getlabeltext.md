---
# required metadata

title: GETLABELTEXT ER function
description: This topic provides information about how the GETLABELTEXT Electronic reporting (ER) function is used.
author: NickSelin
ms.date: 12/23/2021
ms.prod: 
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
ms.search.validFrom: 2022-01-01
ms.dyn365.ops.version: AX 10.0.25

---

# GETLABELTEXT ER function

[!include [banner](../includes/banner.md)]

The `GETLABELTEXT` function searches for a specific label to return a *[String](er-formula-supported-data-types-primitive.md#string)* value that represents the translation of the specified label to the specified language.

## Syntax

```vb
GETLABELTEXT (label id, language)
```

## Arguments

### Label id

`label id`: *String* or *Label Id*

The valid id of one of the following label types:

- [Electronic reporting (ER)](general-electronic-reporting.md) label
- Microsoft Dynamics 365 Finance label

#### Usage notes

This argument can be only defined as a constant by using one of the following supported patterns:

- for ER labels:
    - `@"GER_LABEL:<LABEL ID>"`
    - `"GER_LABEL:<LABEL ID>"`
- for Finance labels:
    - `@"<LABEL ID>"`
    - `"<LABEL ID>"`

> [!NOTE]
> An exception is thrown at design time if no label has been found by using the provided label id.

### Language

`language`: *String*

A string value that represents a language code.

#### Usage notes

This argument can be defined either as a text constant or as a path to a data source field that returns a *String* value.

> [!NOTE]
> An exception is thrown at design time if no language code has been found by using the provided `language` argument when it has been specified as a text constant.
>
> The translation for the `EN-US` system language is returned at runtime for a specified label if no language code has been found by using the provided `language` argument.

## Return values

*String*

The resulting text value.

## <a name=example-1></a>Example 1: System label

The `GETLABELTEXT (@"SYS70894", "en-us")` and `GETLABELTEXT ("SYS70894", "en-us")` expressions return the "Nothing to print" English translation of the `@SYS70894` application label.

## <a name=example-2></a>Example 2: ER label

If you started editing an ER [configuration](general-electronic-reporting.md#Configuration) that has been [derived](er-quick-start2-customize-report.md#DeriveProvidedFormat) from the **ISO20022 Credit transfer (DE)** one, entered a new data source of the [Calculated field](er-calculated-field-ds-performance.md) type, and configured for this data source the `GETLABELTEXT(@"GER_LABEL:VendorName", "de")` expression, this data source returns at runtime the "Kreditorenname" German translation of the `@GER_LABEL:VendorName` ER label that has been initially configured in the base **ISO20022 Credit transfer (DE)** ER configuration.

## Additional resources

[Text functions](er-functions-category-text.md)

[Design multilingual reports in Electronic reporting](er-design-multilingual-reports.md)



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
