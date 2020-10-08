---
# required metadata

title: Troubleshoot Product Configurator
description: This topic describes how to fix issues that you might encounter while working with Product Configurator.
author: SmithaNataraj
manager: tfehr
ms.date: 05/07/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: smnatara
ms.search.validFrom: 2020-5-7
ms.dyn365.ops.version: AX 10.0.14

---
# Troubleshoot Product Configurator
This topic describes how to fix common issues that you might encounter while working with Product Configurator.

## Configuring a product in a sales order line overwrites item text 
This issue happens when a sales order line for a configurable item is created and the item text is modified. When the item is configured and the ok is selected, the text is overwritten with the standard text.

**Resolution**
This is working as expected. The text field includes the variant name that is populated only after the line is configured. Therefore, if the text needs to be changed, it must be done after the line is configured and not before.

## Incorrect rounding with integer attributes when doing calculations in Product Configuration Models
**Business scenario**
1. Set up some attributes in a Production Configuration Model - an input field which is an integer, a percent field which is a decimal, and a result field which is also an integer. 

2. Create a calculation which has the following expression: Expected Result = Input*Percent/100. 

3. The integer result doesn't seem to always round correctly - sometimes it does, but not always. 
For example: When the input number is 1000 and the percentage is 2.40, the expectation is that the integer result would be 24, as 2.40% of 1000 is 24 (24.00 when decimalized). However instead the result is 23. When it is 2.50 it does round to 25 as expected. If the percentage is 2.39 it would round to 24 instead of being 23.

**Resolution**
This is happening because of the way Microsoft solver foundation is representing numbers internally by using fractions, the result of the calculation for the 2.4 example is represented as 27021597764222975 / 1125899906842624 = 23.99999999999999911182158029987476766109466552734375 and .NET will return 23 when casting this value to an Integer.

This behavior will not be changed as other scenarios depend on it. In the given example, the problem can be solved by introducing and additional Decimal attribute and a calculation. 

Attributes:
Input (integer)
Percent (decimal)
ResultDecimal (decimal)
ResultInteger (integer)

ResultDecimal = Input*Percent/100
ResultInteger = ResultDecimal

