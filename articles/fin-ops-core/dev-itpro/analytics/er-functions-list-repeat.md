---
title: REPEAT ER function
description: Learn about how to use the REPEAT Electronic reporting (ER) function, including syntax strings, arguments, return values, usage notes, and examples.
author: kfend
ms.author: kfend
ms.topic: article
ms.date: 08/01/2022
ms.custom:
ms.reviewer: johnmichalak
audience: IT Pro
ms.assetid: 
ms.search.region: Global
ms.search.validFrom: 2022-06-01
ms.search.form: ERDataModelDesigner, ERExpressionDesignerFormula, ERMappedFormatDesigner, ERModelMappingDesigner
ms.dyn365.ops.version: AX 10.0.29
---

# REPEAT ER function

[!include [banner](../includes/banner.md)]

The `REPEAT` function builds a record that contains the field that has a value that matches the specified input. It then returns a new *Record list* of a record that is repeated a specified number of times.

## Syntax

```vb
REPEAT (item, number)
```

## Arguments

`item`: Any supported [primitive](er-formula-supported-data-types-primitive.md) or [composite](er-formula-supported-data-types-composite.md) data type

The value to repeat.

`number`: *Integer*

The number of repeats.

## Return values

*Record list*

The resulting list of records.

## Usage notes

The list of repeated records that is returned exposes the following fields:

- The specified value (`Item` field)
- The current record index (`Number` field)

> [!NOTE]
> Because one-based numbering is used for this function, the `Number` field has the value **1** for the first record of the resulting list.

You can use this function to multiply existing data so that you can do performance and volume testing of [Electronic reporting (ER)](general-electronic-reporting.md) solutions by using the [Regression suite automation tool (RSAT)](../perf-test/rsat/rsat-overview.md).

## Example

You want to generate a document in XML format that must contain as many `Party` XML elements as you specify in a data entry field in the dialog box at runtime, before the execution of an ER format begins.

The following illustration shows the ER [format](er-overview-components.md#format-component). In this format, the single `Party` XML element is added to expose the properties of a single party.

<a href="./media/er-repeat-function-1.png"><img src="./media/er-repeat-function-1.png" alt="Format structure on the Format tab of the Format designer page." class="alignnone size-full" width="929" height="548" /></a>

The next illustration shows the following configured data sources:

- The `Party` data source that represents a single party. The `Party.Value` field is used to expose a single text value.
- The `NumberOfRepeats` [data source](er-user-input-parameter-data-sources.md) that is used to offer a data entry field in the dialog box at runtime, so that you can specify the number of parties that should be entered in the generated document.
- The `Party2` data source that repeats the `Party` record the number of  times that you specified in the `NumberOfRepeats` data source.

<a href="./media/er-repeat-function-2.png"><img src="./media/er-repeat-function-2.png" alt="Configured data sources on the Mapping tab of the Format designer page." class="alignnone size-full" width="1044" height="411" /></a>

The next illustration shows data bindings of the editable ER format that are created to generate output in XML format. This output presents individual parties as enumerated nodes.

<a href="./media/er-repeat-function-3.png"><img src="./media/er-repeat-function-3.png" alt="Configured data bindings on the Mapping tab of the Format designer page." class="alignnone size-full" width="1051" height="417" /></a>

The following illustration shows the result when the designed format is run and the value of the `NumberOfRepeats` data source is specified as **5**.

<a href="./media/er-repeat-function-4.png"><img src="./media/er-repeat-function-4.png" alt="Result of running the format on a new web browser tab." class="alignnone wp-image-290711 size-full" width="400" height="380" /></a>

## Additional resources

[List functions](er-functions-category-list.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
