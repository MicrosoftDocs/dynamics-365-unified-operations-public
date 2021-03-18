---
title: Product configuration model calculations
description: This topic describes how to create calculations for attributes in a product configuration model
author: t-benebo
manager: tfehr
ms.date: 03/18/2021
ms.topic: article
ms.search.form: PCProductConfigurationModelListPage, PCProductConfigurationModelDetails
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: benebotg
ms.search.validFrom: 2021-03-18
ms.dyn365.ops.version: 10.0.18
---

# Product configuration model calculations

[!include [banner](../includes/banner.md)]

This topic describes how to create calculations for attributes in a product configuration model.

## Prerequisites

Calculations are used in a product configuration model to calculate the configuration values for a product. Before you can start to set up calculations, the related product configuration model must exist. For an overview of the setup process for configuration models and the related tasks, see [Set up a product configuration model](set-up-maintain-product-configuration-model.md).

## Create a calculation

A calculation consists of an expression and a target attribute. For more information, see [Calculations for product configuration models FAQ](calculate-product-configuration-models.md).

To create a calculation for an existing product model, follow these steps:

1. Go to **Product information management \> Common \> Product configuration models**.
1. Open a product configuration model, and then select **Edit**.
1. Expand the **Calculations** FastTab, and select **Add** from its toolbar to add a new calculation and make the following settings for it:

    - **Name** - Enter a name for the calculation.
    - **Description** - Enter a description of the calculation.
    - **Target attribute** - Select the attribute that you are making the calculation for.

1. Select **Edit expression** from the **Calculations** FastTab toolbar.
1. The **Enter a calculation** dialog box opens. Add attributes, operators, and values to the expression as needed. For more information about how to work with these elements, see [Expression constraints and table constraints in product configuration models](expression-constraints-table-constraints-product-configuration-models.md).
1. Select **OK** when your expression is ready.

## Calculation examples

This section provides a few examples of how calculations work.

### Example 1

The target attribute is Boolean and the calculation uses the following conditional expression:

`If[(decimalAttribute1 / decimalAttribute2) < 1, True, False]`

This expression returns a value of *True* to the target attribute if `decimalAttribute2` is greater than or equal to `decimalAttribute1`. Otherwise, the expression returns a value of *False*.

### Example 2

This example uses the target attribute `textFixedList`, which is of type text and contains the following fixed list:

| Value | Solver value |
|---|---|
| A | 1a |
| B | 2b |
| C | 2c |

The following screenshot shows how this could look in your system.

![Attribute type settings for example 2](media/model-calculations-example2.png "Attribute type settings, example 2")

The attribute is used in the following conditional statement:

`If[integerAttribute < 150, 0, 2]`

The expression returns the text value of the first record on the fixed list, which is "A", if the `integerAttribute` is less than 150. Otherwise, it returns the text value of the third record on the fixed list, which is "C".

> [!NOTE]
> The fixed list is equivalent to a zero-based enum, and its values are accessed by the right integer value. That's why the first fixed list value ("A") is matched to 0, the second value ("B") is matched to 1 and the third value ("C") to 2.

### Example 3

This example uses the target attribute `textFixedList` from the previous example, and another text attribute `textAttribute`, which contains the following fixed list:

| Value | Solver value |
|---|---|
| AA | 1aa |
| BB | 2bb |

The following screenshot shows how this could look in your system.

![Attribute type settings for example 3](media/model-calculations-example3.png "Attribute type settings, example 3")

The value for the `textFixedList` attribute is calculated using the following conditional statement:

`If[textAttribute == "1aa", 0, 2]`

If the `textAttribute` value has a solver value that equals "1aa", this expression returns the text value of the first record on the `textFixedList` fixed list, which is "A". Otherwise, it returns the text value of the third record on the `textFixedList` fixed list, which is "C".

> [!NOTE]
>
> - The conditional statement must use the solver value of the attribute.
> - Only fixed-list text attributes can be used in calculations.

## See also

- [Calculations for product configuration models FAQ](calculate-product-configuration-models.md)
- [Add an expression constraint to a product configuration model](tasks/add-expression-constraint-product-configuration-model.md)
- [Product configuration models overview](product-configuration-models.md)
