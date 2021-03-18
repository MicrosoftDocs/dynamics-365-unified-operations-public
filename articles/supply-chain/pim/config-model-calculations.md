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

The following table shows the prerequisites that must be in place before you start.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Category</p></th>
<th><p>Prerequisite</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Related setup tasks</p></td>
<td><p>Calculations can be used in a product configuration model to calculate the configuration values for a product. For an overview of the setup process for configuration models and the related tasks, see <a href="setting-up-and-maintaining-product-configuration-models.md">Setting up and maintaining product configuration models</a>.</p></td>
</tr>
</tbody>
</table>


## Create a calculation

You create a calculation for a product configuration model. A calculation consists of an expression and a target attribute. For more information, see [Calculations for product configuration models](calculations-for-product-configuration-models.md).

To create a calculation, follow these steps:

1.  Click **Product information management** \> **Common** \> **Product configuration models**.

2.  Select a product configuration model, and then click **Edit**.

3.  In the **Constraint-based product configuration model details** form, on the **Calculations** FastTab, click **Add** to add a new calculation.

4.  In the **Target attribute** field, select one of the attributes that are included in the product configuration model.

5.  In the **Expression** field, click the drop-down arrow or press Alt, Down Arrow.

6.  In the **Expression constraint editor** form, on the **All symbols** tab, double-click a symbol or press Enter to enter the symbol in the **Expression** field.

7.  Use the same method to add attributes, operators, and values to the expression. For more information about how to use attributes, operators, and values, see [Expression constraints and table constraints](expression-constraints-and-table-constraints.md).

## Example of a calculation

In the following example, the target attribute is of the Boolean type, and the calculation uses an If expression:

If\[(decimalAttribute1 / decimalAttribute2) \< 1, True, False\]

This expression returns a value of “True” to the target attribute if decimalAttribute2 is greater than or equal to decimalAttribute1. Otherwise, the expression returns a value of “False.”

## Related tasks

[Create an expression constraint for a product component](create-an-expression-constraint-for-a-product-component.md)

## Technical information for system administrators

If you don't have access to the pages that are used to complete this task, contact your system administrator and provide the information that is shown in the following table.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Category</p></th>
<th><p>Prerequisite</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Configuration keys</strong></p></td>
<td><p>No configuration key is needed for this task.</p></td>
</tr>
<tr class="even">
<td><p><strong>Security roles</strong></p></td>
<td><p>To use calculations, you must be a member of the Product designer (BOMProductDesigner) security role.</p></td>
</tr>
</tbody>
</table>


## See also

[About product configuration models](about-product-configuration-models.md)

  

