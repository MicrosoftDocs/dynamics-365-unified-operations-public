---
title: Use formulas as parameters
description: Learn about how to use formulas with the Regression suite automation tool (RSAT) to modify test parameters, including code examples.
author: FrankDahl
ms.author: johnmichalak
ms.topic: article
ms.date: 01/21/2026
ms.custom: 
  - bap-template
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2023-11-17
ms.dyn365.ops.version: AX 7.0.0
---

# Use formulas as parameters

[!include [banner](../../includes/banner.md)]

The Regression suite automation tool (RSAT) uses parameter files where you can change values for tests. You can specify fixed values or even use Microsoft Excel formulas to make values more dynamic. Excel is the client that's used to maintain the parameters, and the most recent versions of RSAT use Power Fx to evaluate formulas during playback.

When you edit parameter files in Excel, always use the **Generate** action to apply changes for playback. This action shows whether there are any compatibility issues with formulas that Power Fx can't process.

Power Fx is almost 100% compatible with Excel. In most cases, you can use Excel parameter files directly with Power Fx without making any changes.

For more information about which formulas are available with Power Fx, see [Power Fx formula reference overview](/power-platform/power-fx/formula-reference-overview).

To ensure that formulas are compatible, be aware of a few limitations. The following sections describe dos and don'ts for using formulas.

## Steps can reference values only from completed steps

Test steps can't reference later steps in a case. For example, step 2 in a test case can't reference a value from the cell for step 3. This limitation exists because step 3 doesn't logically occur when step 2 is running, and the value for step 3 can change before step 3 runs.

As another example, the case that the following illustration shows doesn't work, because the **Inventory unit** cell tries to refer *forward* to and use the value from the **Purchase unit** cell.

:::image type="content" source="media/rsat-reference-forward.png" alt-text="Screenshot of RSAT reference forward.":::

However, the reverse case that the following illustration shows does work, because the **Purchase unit** refers *back* to and uses the value from the **Inventory unit** cell.

:::image type="content" source="media/rsat-reference-backward.png" alt-text="Screenshot of RSAT reference backward.":::

One way to fix this issue is to create a new named cell that holds a value. Both cells (**Inventory unit** and **Purchase unit**) can reference that value.

:::image type="content" source="media/rsat-reference-named.png" alt-text="Screenshot of RSAT reference named cell.":::

## Use saved variables in formulas

You can save variables with recordings. Assign names to these variables and enclose them in double braces, such as `{{PurchCreateOrder_PurchTable_PurchId_16601_Copy}}`.

Variables provide a convenient way to save a value so that you can reuse it later during test execution, both within a single test case and as context that's passed when test cases are connected. You can use variables only in primary test step cells and message validation cells.

Cells that include strings reference variables directly by name within the string. Here's an example.

**"The variable has the value \{\{PurchCreateOrder\_PurchTable\_PurchId\_16601\_Copy\}\} as purchase order ID"**

Cells that include formulas must enclose the variable name in double quotation marks. Here's an example.

`=CONCAT("All field values required for validation are specified for product ", "{{EcoResProductDetailsExtended_InventTable_ItemId_17691_Copy}}")`

You must also enclose variables that have numeric values in double quotation marks when you reference them in formulas. Use the `VALUE` function to get the numeric value. Here's an example.

`=VALUE("{{PurchCreateOrder_PurchLine_Quantity_16601_Copy}}") * 2`

Never use a single quotation mark (') in front of a formula as a workaround. Therefore, don't follow this example, where the variable is referenced in an unsupported way.

`'={{PurchCreateOrder_PurchLine_Quantity_16601_Copy}}") * 2`

In this case, edit the cell so that it's validated and saved without the single quotation mark in front.

The following illustration shows an example of an exception that RSAT presents if a formula has compatibility issues when the **Generate** action is used.

:::image type="content" source="media/rsat-generate-exception.png" alt-text="Screenshot of RSAT Generate exception.":::

## Excel turns TODAY and NOW into decimal numbers

Some common test cases create new records that have unique identifiers. For example, a new product requires a product ID, which must be unique. You typically use formulas to generate unique identifiers of this type. One option is to use the `RAND` or `RANDBETWEEN` functions for this purpose. However, because these functions randomly assign identifiers, there's a risk that they return an existing ID. Another, better option is to use the current time to define the unique identifier. Excel can be helpful for this approach, because it internally maintains dates and times as decimal numbers. Therefore, you can take advantage of this behavior to generate unique identifiers.

Excel sometimes dynamically converts dates and times from functions such as `TODAY` and `NOW` into decimal numbers. However, this approach doesn't work in Power Fx unless you explicitly specify it in the formulas.

For example, for the function `=LEFT(TODAY(),5)`, Excel returns a five-digit number that represents the current date. For the function `=MID(NOW(),7,8)`, Excel returns an eight-digit number that represents the current time of day. You can combine these two values into a unique identifier such as **ITEM 45254 – 0200787**, where the part before the hyphen is the numeric representation of the date, and the part after the hyphen is the numeric representation of the time of day.

Unfortunately, Power Fx doesn't process these functions as decimal numbers. Instead, it processes the text value that the `TODAY` and `NOW` functions return. Therefore, the result resembles the example in the following illustration.

:::image type="content" source="media/rsat-dates-powerfx.png" alt-text="Screenshot of RSAT date and time in Power Fx.":::

To ensure full compatibility with Power Fx, wrap the `TODAY` and `NOW` functions in a `VALUE` function to explicitly request the decimal representation.

`=LEFT(VALUE(TODAY()),5) and =MID(VALUE(NOW()),7,8)`

This approach ensures consistent decimal values, and you can use it to compose unique identifiers that are compatible with Power Fx.

> [!TIP]
> Create a separate cell for each formula. Then, in another separate cell, concatenate the values from those cells into an identifier string. Different Excel versions handle the previously described approach differently. The use of separate cells seems to provide a consistent result across Excel versions.

## Bad practices for formulas

This section provides a list of practices that you should **not** follow when you use formulas, because they cause issues.

Don't use a formula such as the following example to get the first day of a month.

`Date(Year(Today()),Month(Today()),Day(1))`

The issue here's that the `Day` function is taking a date as an input parameter. In Power Fx, day "1" is December 31, 1899. Therefore, the preceding formula above doesn't return the first day of a month, as the user intended. To return the first day of a month, use a formula such as the following example instead.

`Date(Year(Today()),Month(Today()),1))`

Don't start a formula with a plus sign (\+). Don't start a cell value with either =\+ or just \+.
