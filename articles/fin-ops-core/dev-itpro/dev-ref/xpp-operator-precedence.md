---
title: Operator precedence
description: Learn about operator precedence, including an overview of the order of operator precedence with a table that provides syntax for operators in precedence order.
author: pvillads
ms.author: pvillads
ms.topic: language-reference
ms.custom: 
  - bap-template
ms.date: 06/13/2024
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
---

# Operator precedence

[!include [banner](../includes/banner.md)]

This article describes operator precedence.

The order in which a compound expression is evaluated is important. If you do not explicitly tell the compiler the order that you want operations to be performed in, the order is based on operator precedence. You can use parentheses `( )` to explicitly tell the X++ compiler how you want an expression to be evaluated.

Consider the expression `x + y / 100`, which gives a different result depending on whether the addition or the division is performed first.  Because the division operator has a higher precedence than the addition operator, the compiler evaluates `y/100` first. So, `x + y / 100` is equivalent to `x + (y / 100)`. If you add parentheses to make the expression `(x + y)/ 100`, then `x + y` is evaluated first.

To make your code easy to read and maintain, be explicit, and indicate with parentheses which operators should be evaluated first.

## Order of operator precedence

The operators in the following table are listed in precedence order. The higher in the table an operator appears, the higher precedence it has. Operators with higher precedence are evaluated before operators with a lower precedence. The operator precedence of X++ is not the same as other languages, for example C# and Java.


|              Operators in precedence order               |                 Syntax                 |
|----------------------------------------------------------|----------------------------------------|
| unary operators                                          | `- ~ !`                  |
| multiplicative, shift, bitwise AND, bitwise exclusive OR | `* / % DIV << >> & ^`    |
| additive, bitwise inclusive OR                           | `+ -`                   |
| relational, equality                                     | `< <= == != > >= like as is` |
| logical operators (AND, OR)                              | `&& ||`             |
| conditional                                              | `? :`                   |

Operators on the same line in the table have equal precedence. If there are more than one of these operators in an expression, the expression is evaluated from left to right unless assignment operators are used. Assignment operators are evaluated from right to left. For example, `&&` (logical AND) and `||` (logical OR) have the same precedence and are evaluated from left to right. This means that `0 && 0 || 1 == 1`, and `1 || 0 && 0 == 0`


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
