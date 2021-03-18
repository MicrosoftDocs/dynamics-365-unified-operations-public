---
title: Product configuration model calculations
description: This topic describes how to create calculations, which enable product designers to handle decimal values in a product configuration model
author: t-benebo
manager: tfehr
ms.date: 03/18/2021
ms.topic: article
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: benebotg
ms.search.validFrom: 2021-03-18
ms.dyn365.ops.version: 10.0.18
---

# Product configuration model calculations

[!include [banner](../includes/banner.md)]

This topic describes how to create calculations, which enable product designers to handle decimal values in a product configuration model.

## Prerequisites

Calculations are used in a product configuration model to calculate the configuration values for a product. Before you can start to set up calculations, the related product configuration model must exist.  For an overview of the setup process for configuration models and the related tasks, see [Set up a product configuration model](set-up-maintain-product-configuration-model.md).

## Create a calculation

You create a calculation for a product configuration model. A calculation consists of an expression and a target attribute. For more information, see [Calculations for product configuration models FAQ](calculate-product-configuration-models.md).

To create a calculation, follow these steps:

1. Go to **Product information management \> Common \> Product configuration models**.

1. Select a product configuration model, and then select **Edit**.

1. In the **Constraint-based product configuration model details** form, on the **Calculations** FastTab, select **Add** to add a new calculation.

1. In the **Target attribute** field, select one of the attributes that are included in the product configuration model.

1. In the **Expression** field, select the drop-down arrow or press Alt + Down Arrow.

1. In the **Expression constraint editor** form, on the **All symbols** tab, double-click a symbol or press Enter to enter the symbol in the **Expression** field.

1. Use the same method to add attributes, operators, and values to the expression. For more information about how to use attributes, operators, and values, see [Expression constraints and table constraints in product configuration models](expression-constraints-table-constraints-product-configuration-models.md).

## Calculation examples

### Example 1

The target attribute is of the Boolean type, and the calculation uses the following conditional expression:

`If[(decimalAttribute1 / decimalAttribute2) < 1, True, False]`

This expression returns a value of *True* to the target attribute if `decimalAttribute2` is greater than or equal to `decimalAttribute1`. Otherwise, the expression returns a value of *False*.

### Example 2

This example uses the target attribute `textFixedList`, which is of type *Text* and contains the following fixed list:

| Value | Solver value |
|---|---|
| AA | 1aa |
| BB | 2bb |

The following screenshot shows how this could look in your system.

![Attribute type settings for example 2](media/model-calculations-example2.png "Attribute type settings, example 2")

A calculation that uses a conditional statement could look like this:

`If[integerAttribute < 150, 0, 2]`

The expression returns the text value of the first record on the fixed list, which is "A", if the `integerAttribute` is less than 150. Otherwise, it returns the text value of the third record on the fixed list, which is "C".

Note that the fixed list is equivalent to a zero-based enum, and its values are accessed by the right integer value. That's why the first fixed list value ("A") is matched to 0, the second value ("B") is matched to 1 and the third value ("C") to 2.

### Example 3

This example uses the target attribute `textFixedList` from the previous example, and another text attribute `textAttribute`, which contains the following fixed list:

| Value | Solver value |
|---|---|
| A | 1a |
| B | 2b |
| C | 2c |

The following screenshot shows how this could look in your system.

![Attribute type settings for example 3](media/model-calculations-example3.png "Attribute type settings, example 3")

A calculation that uses a conditional statement could look like this:

`If[textAttribute == "1aa", 0, 2]`

This expression returns the text value of the first record on the `textFixedList` fixed list, which is "A" if the `textAttribute` value has a solver value that equals "1aa". Otherwise, it returns the text value of the third record on the `textFixedList` fixed list, which is "C".

Note that in these scenarios, the solver value of the attribute must be used in the conditional statement.

Note that non-fixed list text attributes can't be used in calculations.

## Related tasks

[Add an expression constraint to a product configuration model](tasks/add-expression-constraint-product-configuration-model.md)

## See also

[Product configuration models overview](product-configuration-models.md)
