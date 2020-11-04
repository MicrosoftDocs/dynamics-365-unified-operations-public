---
# required metadata

title: Troubleshoot the product configurator
description: This topic describes how to fix issues that you might encounter while working with Product Configurator.
author: SmithaNataraj
manager: tfehr
ms.date: 11/04/2020
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
ms.search.validFrom: 2020-11-04
ms.dyn365.ops.version: 10.0.15

---
# Troubleshoot the product configurator

This topic describes how to fix common issues that you might encounter while working with the product configurator.

## Item text is overwritten when I configure a product on a sales order line.

### Issue description

This issue happens when you create a sales order line for a configurable item and then modify the item text. When you configure the item and then select **OK**, the text is overwritten with the standard text.

### Issue resolution

This is working as expected. The text field includes the variant name, which is only populated after you configure the line. Therefore, you must only change the text after you have configured the line, not before.

## While calculating product configuration models, integer attributes a rounded incorrectly.

### Issue description

This issue can occur when you do the following series of actions:

1. Set up the following attributes on a production configuration model:
    - Input (integer)
    - Percent (decimal)
    - Result (integer)

2. Create a calculation that has the following expression:<br>*Result = Input \* Percent/100*.

3. The integer result doesn't always round correctly&mdash;sometimes it does, but not always. For example: When the input is 1000 and the percentage is 2.40, you would expect the integer result to be 24 because 2.40% of 1000 is 24 (24.00 when decimalized). However, the result is instead shown as 23. When the percentage is 2.50, the calculation rounds to 25 as expected, but when the percentage is 2.39, it rounds to 24 instead 23.

### Issue resolution

This happens because of the way Microsoft Solver Foundation represents numbers internally by using fractions. The result of the calculation for the 2.4 example is represented as 27021597764222975 / 1125899906842624 = 23.99999999999999911182158029987476766109466552734375 and .NET will return 23 when casting this value to an integer.

This behavior will not be changed because other scenarios depend on it. In the given example, the problem can be solved by introducing and additional decimal attribute and a calculation.

For example, you could set up the following attributes on a production configuration model:

- Input (integer)
- Percent (decimal)
- ResultDecimal (decimal)
- ResultInteger (integer)

And then add these calculations:

- *ResultDecimal = Input \* Percent/100*
- *ResultInteger = ResultDecimal*
