---
# required metadata

title: Operator precedence
description: This article describes operator precedence in Microsoft Dynamics 365 for Operations.
author: pvillads
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: annbe
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 6174
ms.assetid: dd4a4971-c35a-466d-9c24-244cd75f9020
ms.search.region: Global
# ms.search.industry: 
ms.author: pvillads
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Operator precedence

[!include[banner](../includes/banner.md)]


This article describes operator precedence in Microsoft Dynamics 365 for Operations.

The order in which a compound expression is evaluated is important. For example, (x + y / 100) gives a different result depending on whether the addition or the division is performed first. You can use parentheses ( ) to explicitly tell the X++ compiler how you want an expression to be evaluated. For example, (x + y)/ 100. If you do not explicitly tell the compiler the order that you want operations to be performed in, the order is based on the precedence assigned to the operators. For example, the division operator has a higher precedence than the addition operator. For x + y / 100, the compiler would evaluate y/100 first. So, x + y / 100 is equivalent to x + (y / 100). To make your code easy to read and maintain, be explicit. Indicate with parentheses which operators should be evaluated first.

## Order of Operator Precedence
The operators in the following table are listed in precedence order. The higher in the table an operator appears, the higher precedence it has. Operators with higher precedence are evaluated before operators with a lower precedence. Note that the operator precedence of X++ is not the same as other languages, for example C\# and Java.

| Operators in precedence order                            | Syntax                                 |
|----------------------------------------------------------|----------------------------------------|
| unary operators                                          | - ~ !                                  |
| multiplicative, shift, bitwise AND, bitwise exclusive OR | \* / % DIV &lt;&lt; &gt;&gt; & ^       |
| additive, bitwise inclusive OR                           | + - |                                  |
| relational, equality                                     | &lt; &lt;= == != &gt; &gt;= like as is |
| logical operators (AND, OR)                              | && ||                                  |
| conditional                                              | ? :                                    |

Operators on the same line have equal precedence. If there is more than one of these operators in an expression, the expression is evaluated from left to right unless assignment operators are used (these are evaluated from right to left).For example, && (logical AND) and || (logical OR) have the same precedence and are evaluated from left to right. This means that:0&&0||1 == 1, and 1||0&&0 == 0

## See also
[Assignment Operators](http://msdn.microsoft.com/library/d4e86b9c-be82-4f19-ad86-7722344a05f3(AX.60).aspx)

[Arithmetic Operators](http://msdn.microsoft.com/library/cffbc613-3875-4520-9dea-046dc99aab99(AX.60).aspx)

[Relational Operators](http://msdn.microsoft.com/library/702af366-4d46-445e-bd4b-722c9845199f(AX.60).aspx)




