---
# required metadata

title: Expression constraints and table constraints in product configuration models
description: This article describes the use of expression constraints and table constraints. Constraints control the attribute values that you can select when you configure products for a sales order, sales quotation, purchase order, or production order. You can use expression constraints or table constraints, depending on how you prefer to build the constraints. 
author: t-benebo
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: PCGlobalTableConstraintEdit, PCProductConfigurationModelDetails, PCTableConstraintAttachAttributeTree, PCTableConstraintDefinition
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.assetid: 5c12b1f2-eb89-4648-a755-de412f2eadd6
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: benebotg
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Expression constraints and table constraints in product configuration models

[!include [banner](../includes/banner.md)]

This article describes the use of expression constraints and table constraints. Constraints control the attribute values that you can select when you configure products for a sales order, sales quotation, purchase order, or production order. You can use expression constraints or table constraints, depending on how you prefer to build the constraints. 

Constraints are used to control the attribute values that you can select when you configure products for a sales order, sales quotation, purchase order, or production order. You can use expression constraints or table constraints, depending on how you prefer to build the constraints.

## What are expression constraints?
Expression constraints are characterized by an expression that uses arithmetic and Boolean operators and functions. An expression constraint is written for a specific component in a product configuration model. It can't be reused by or shared with another component. However, the expression constraints for a component can reference attributes of the component's subcomponents.

## What are table constraints?
Table constraints list the combinations of values that are allowed for attributes when you configure a product. Table constraint definitions can be used generically. When you create a table constraint for a component in a product configuration model, you select a table constraint definition. To create the combinations that are allowed, you add attributes of specific types to the components. Each attribute type has a specific value.

### Example of a table constraint

This example shows how you can limit the configuration of a speaker to specific cabinet finishes and fronts. The first table shows the cabinet finishes and fronts that are generally available for configuration. The values are defined for the **Cabinet finish** and **Front grill** attribute types.

| Attribute type | Values                      |
|----------------|-----------------------------|
| Cabinet finish | Black, Oak, Rosewood, White |
| Front grill    | Black, Metal, White         |

The next table shows the combinations that are defined by the **Color and finish** table constraint. By using this table constraint, you can configure a speaker that has an oak finish and a black grill, a Rosewood finish and a white grill, and so on.

| Finish         | Grill                       |
|----------------|-----------------------------|
| Oak            | Black                       |
| Rosewood       | White                       |
| White          | Black                       |
| White          | White                       |
| Black          | Black                       |
| Black          | Metal                       | 

You can create system-defined and user-defined table constraints. For more information, see [System-defined and user-defined table constraints](system-defined-user-defined-table-constraints.md).

## What syntax should be used to write constraints?
You must use Optimization Modeling Language (OML) syntax when you write constraints. The system uses Microsoft Solver Foundation constraint solver to solve the constraints.

## Should I use table constraints or expression constraints?
You can use either expression constraints or table constraints, depending on how you prefer to build the constraints. You build a table constraint as a matrix, whereas an expression constraint is an individual statement. When you configure a product, it doesn't matter what kind of constraint is used. The following example shows how the two methods differ.  

When you configure a product by using the following constraint setups, these combinations are allowed:

-   A product in the color Black, and in size 30 or 50
-   A product in the color Red and in size 20

### Table constraint setup

| Color | Size |
|-------|------|
| Black | 30   |
| Black | 50   |
| Red   | 20   |

### Expression constraint setup

(Color == "Black" & (size == "30" | size == "50")) | (color == "Red" & size = "20")

## Should I use operators or infix notation when I write expression constraints?
You can write an expression constraint by using either the available prefix operators or infix notation. For the **Min**, **Max**, and **Abs** operators, you can't use infix notation. These operators are included as standard operators in most programming languages.

## What operators and infix notation can I use when I write expression constraints?
The following tables list the operators and infix notation that you can use when you write an expression constraint for a component in a product configuration model. The examples in the first table show how to write an expression by using either infix notation or operators.

<table>
<colgroup>
<col width="25%" />
<col width="25%" />
<col width="25%" />
<col width="25%" />
</colgroup>
<thead>
<tr class="header">
<th>Operator</th>
<th>Description</th>
<th>Syntax</th>
<th>Examples</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Implies</td>
<td>If condition a is true, then apply the contraint b.</td>
<td>Implies[a, b], infix: a -: b</td>
<td><ul>
<li><strong>Operator:</strong> Implies[x != 0, y &gt;= 0]</li>
<li><strong>Infix notation:</strong> x != 0 -: y &gt;= 0</li>
</ul></td>
</tr>
<tr class="even">
<td>And</td>
<td>This is true only if all conditions are true. If the number of conditions is 0 (zero), it produces <strong>True</strong>.</td>
<td>And[args], infix: a &amp; b &amp; ... &amp; z</td>
<td><ul>
<li><strong>Operator:</strong> And[x == 2, y &lt;= 2]</li>
<li><strong>Infix notation:</strong> x == 2 &amp; y &lt;= 2</li>
</ul></td>
</tr>
<tr class="odd">
<td>Or</td>
<td>This is true if any condition is true. If the number of conditions is 0 (zero), it produces <strong>False</strong>.</td>
<td>Or[args], infix: a | b | ... | z</td>
<td><ul>
<li><strong>Operator:</strong> Or[x == 2, y &lt;= 2]</li>
<li><strong>Infix notation:</strong> x == 2 | y &lt;= 2</li>
</ul></td>
</tr>
<tr class="even">
<td>Plus</td>
<td>This sums its conditions. If the number of conditions is 0 (zero), it produces <strong>0</strong>.</td>
<td>Plus[args], infix: a + b + ... + z</td>
<td><ul>
<li><strong>Operator:</strong> Plus[x, y, 2] == z</li>
<li><strong>Infix notation:</strong> x + y + 2 == z</li>
</ul></td>
</tr>
<tr class="odd">
<td>Minus</td>
<td>This negates its argument. It must have exactly one condition.</td>
<td>Minus[expr], infix: -expr</td>
<td><ul>
<li><strong>Operator:</strong> Minus[x] == y</li>
<li><strong>Infix notation:</strong> -x == y</li>
</ul></td>
</tr>
<tr class="even">
<td>Abs</td>
<td>This takes the absolute value of its condition. It must have exactly one condition.</td>
<td>Abs[expr]</td>
<td><strong>Operator:</strong> Abs[x]</td>
</tr>
<tr class="odd">
<td>Times</td>
<td>This takes the product of its conditions. If the number of conditions is 0 (zero), it produces <strong>1</strong>.</td>
<td>Times[args], infix: a * b * ... * z</td>
<td><ul>
<li><strong>Operator:</strong> Times[x, y, 2] == z</li>
<li><strong>Infix notation:</strong> x * y * 2 == z</li>
</ul></td>
</tr>
<tr class="even">
<td>Power</td>
<td>This takes an exponential. It applies exponentiation from right to left. (In other words, it&#39;s right-associative.) Therefore, <strong>Power[a, b, c]</strong> is equivalent to <strong>Power[a, Power[b, c]]</strong>. <strong>Power</strong> can be used only if the exponent is a positive constant.</td>
<td>Power[args], infix: a ^ b ^ ... ^ z</td>
<td><ul>
<li><strong>Operator:</strong> Power[x, 2] == y</li>
<li><strong>Infix notation:</strong> x ^ 2 == y</li>
</ul></td>
</tr>
<tr class="odd">
<td>Max</td>
<td>This produces the largest condition. If the number of conditions is 0 (zero), it produces <strong>Infinity</strong>.</td>
<td>Max[args]</td>
<td><strong>Operator:</strong> Max[x, y, 2] == z</td>
</tr>
<tr class="even">
<td>Min</td>
<td>This produces the smallest condition. If the number of conditions is 0 (zero), it produces <strong>Infinity</strong>.</td>
<td>Min[args]</td>
<td><strong>Operator:</strong> Min[x, y, 2] == z</td>
</tr>
<tr class="odd">
<td>Not</td>
<td>This produces the logical inverse of its condition. It must have exactly one condition.</td>
<td>Not[expr], infix: !expr</td>
<td><ul>
<li><strong>Operator:</strong> Not[x] &amp; Not[y == 3]</li>
<li><strong>Infix notation:</strong> !x!(y == 3)</li>
</ul></td>
</tr>
</tbody>
</table>

The examples in the next table show how to write infix notation.


|  Infix notation   |                                          Description                                          |
|-------------------|-----------------------------------------------------------------------------------------------|
|     x + y + z     |                                           Addition                                            |
|    x \* y \* z    |                                        Multiplication                                         |
|       x - y       | Binary subtraction is translated the same as binary addition where there is a negated second. |
|     x ^ y ^ z     |                          Exponentiation that has right associativity                          |
|        !x         |                                          Boolean not                                          |
|      x -: y       |                                      Boolean implication                                      |
|         x         |                                               y                                               |
|     x & y & z     |                                          Boolean and                                          |
|    x == y == z    |                                           Equality                                            |
|    x != y != z    |                                           Distinct                                            |
|  x &lt; y &lt; z  |                                           Less than                                           |
|  x &gt; y &gt; z  |                                         Greater than                                          |
| x &lt;= y &lt;= z |                                     Less than or equal to                                     |
| x &gt;= y &gt;= z |                                   Greater than or equal to                                    |
|        (x)        |                           Parentheses override default precedence.                            |

## Why aren't my expression constraints validated correctly?
You can't use reserved keywords as solver names for attributes, components, or subcomponents in a product configuration model. Here is a list of the reserved keywords that you can't use:

-   Ceiling
-   Element
-   Equal
-   Floor
-   If
-   Less
-   Greater
-   Implies
-   Log
-   Max
-   Min
-   Minus
-   Plus
-   Power
-   Times
-   Slot
-   Model
-   Decision
-   Goal


## Additional resources

[Create an expression constraint](tasks/add-expression-constraint-product-configuration-model.md)

[Add a calculation to a product configuration model](tasks/add-calculation-product-configuration-model.md)





[!INCLUDE[footer-include](../../includes/footer-banner.md)]
