---
# required metadata

title: Calculations for product configuration models FAQ
description: This article describes calculations for product configuration models and explains how to use calculations together with constraints.
author: t-benebo
ms.date: 11/03/2017
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: PCConstraintEditor, PCProductConfigurationModelDetails, PCRuntimeConfigurator
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.assetid: 8993f9a1-d1c0-49f5-afd3-5e1077ded0fe
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: benebotg
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Calculations for product configuration models FAQ

[!include [banner](../includes/banner.md)]

This article describes calculations for product configuration models and explains how to use calculations together with constraints.

Calculations can be used for arithmetic or logical operations. They complement expression constraints in product configuration models. You can define calculations on the **Constraint-based product configuration model details** page and then build expressions for the calculations in the expression editor. For more information, see Create calculations.

## What is a calculation?
A calculation is an element that you can use in a product configuration model. Calculations complement constraints by letting you use decimal numbers to calculate values when you configure a product. Additionally, calculations have a larger set of available operators than constraints have.  

Like a constraint, a calculation is associated with a specific component in a product configuration model, and can’t be reused by or shared with another component. One important difference between calculations and constraints is that calculations are imperative (unidirectional), whereas constraints are declarative (bi-directional). For more information about constraints, see [Expression constraints and table constraints in product configuration models](expression-constraints-table-constraints-product-configuration-models.md).  

A calculation consists of a target attribute and a calculation expression.

## What is a target attribute?
A target attribute is an attribute that receives the result of the calculation expression.  

In the following expression, the target attribute is a tablecloth measurement:  

**Expression:** If\[decimalAttribute1 &lt;= decimalAttribute2, True, False\]  

**DecimalAttribute1** is the table length, and **decimalAttribute2** is the tablecloth length. The expression returns the value **True** to the target attribute if **decimalAttribute2** is greater than or equal to **decimalAttribute1**. Otherwise, the expression returns **False**. Therefore, the tablecloth measurement is acceptable if the tablecloth length is the same as or exceeds the length of the table.

## What attribute types can be set to target attributes?
All attribute types that the product configurator supports can be set to target attributes, except text without a fixed list.

## Can the value of a target attribute restrict the values of the input attributes in a calculation?
No, the value of a target attribute can’t restrict the values of the input attributes, because calculations are unidirectional. Therefore, the value of the target attribute is set based on changes in the value of the input attributes, but a change in the value of the target doesn’t affect the value of the input attributes. This behavior differs from the behavior for constraints. Constraints occur in both directions.

### Example

In the following expression, the target for the calculation is the length of a power cord, and the input value is a color:  

**Expression:** \[If Color == "Green", 1.5, 1.0\]  

When you configure the item, the length of the power cord is set to **1.5** if you specify **Green** as the value of color attribute. If you specify any other color, the length is set to **1.0**. However, because calculations are unidirectional, the calculation doesn't set the value of the color attribute to **Green** if you specify a length of **1.5**.

## What happens if a calculation has a target attribute of the integer type but a calculation generates a decimal number?
If a target attribute is of the integer type, but a calculation generates a decimal number, only the integer part of the calculated result is returned. The decimal part is removed, and the result isn't rounded. For example, a result of 12.70 is shown as 12.

## When do calculations occur?
Calculations occur when a value has been provided for all input attributes.

## Can I overwrite the value that is calculated for the target attribute?
You can overwrite the value that is calculated for the target attribute, unless the target attribute is set as hidden or read-only.

## How do I set a target attribute as hidden or read-only?
To set an attribute as hidden or read-only, follow these steps.

1.  Click **Product information management** &gt; **Products** &gt; **Product configuration models**.
2.  Select a product configuration model, and then, on the Action Pane, click **Edit**.
3.  On the **Constraint-based product configuration model details** page, select the attribute to use as a target attribute.
4.  On the **Attributes** FastTab, select **Hidden** or **Read-only**.

## Can a calculation overwrite the values that I set?
No. The values that you set when you configure a product are the values that are used. The calculation that occurs when the input values in a calculation are changed can’t overwrite the values that you provide for a specific attribute.

## What happens if I remove an input value in a calculation?
If you remove an input value in a calculation, the value of the target attribute is also removed.

## Why do I receive an error message that says that my model is in contradiction?
This message is shown when a calculation includes an error, or when a contradiction exists in one or more constraints. For more information about contradictions in constraints, see [Expression constraints and table constraints in product configuration models](expression-constraints-table-constraints-product-configuration-models.md). Here are some situations where errors can occur in calculations:

-   A value is divided by 0 (zero).
-   A conflict exists between the following two elements:
    -   The values that are available for an attribute and are limited by a constraint
    -   A value that is generated by a calculation
-   The values that are returned by the calculation are outside the domain of the attribute. An example is an integer from \[1..10\] that is calculated to 0.

## Why do I receive an error message even though I successfully validated my product model?
Calculations aren't included in the validation. You must test the product configuration model to find errors in calculations. To test a product configuration model, follow these steps.

1.  Click **Product information management** &gt; **Products** &gt; **Product configuration models**.
2.  Select a product configuration model, and then, on the Action Pane, in the **Run** group, click **Test**.






[!INCLUDE[footer-include](../../includes/footer-banner.md)]