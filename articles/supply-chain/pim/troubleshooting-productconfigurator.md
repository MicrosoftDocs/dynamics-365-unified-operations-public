---
# required metadata

title: Troubleshoot the product configurator
description: This topic describes how to fix issues that you might encounter while you work with product configurator.
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

This topic describes how to fix issues that you might encounter while you work with the product configurator.

## Item text is overwritten when I configure a product on a sales order line.

### Issue description

This issue occurs when you create a sales order line for a configurable item and then modify the item text. When you configure the item and then select **OK**, the text is overwritten with the standard text.

### Issue resolution

This behavior is expected. The text field includes the variant name, which is filled in only after you configure the line. Therefore, you must change the text after you've configured the line, not before.

## Integer attributes are incorrectly rounded when product configuration models are calculated.

### Issue description

This issue can occur when you perform the following series of actions:

1. Set up the following attributes on a production configuration model:

    - Input (integer)
    - Percent (decimal)
    - Result (integer)

2. Create a calculation that has the following expression:

    *Result* = *Input* × *Percent* ÷ 100

In this case, the integer result isn't always correctly rounded. For example, the input is 1,000, and the percentage is 2.40. Therefore, you expect the integer result to be 24, because 2.40 percent of 1,000 is 24 (or 24.00 in decimal form). Instead, the result is shown as 23. However, when the percentage is 2.39, the calculation is rounded to 24 instead of 23. When the percentage is 2.50, the calculation is rounded to 25, as expected.

### Issue resolution

This issue occurs because of the way that Microsoft Solver Foundation internally represents numbers by using fractions. For the preceding example, the result of the calculation where the percentage is 2.40 is represented as 27021597764222975 ÷ 1125899906842624 = 23.99999999999999911182158029987476766109466552734375. When .NET casts this value as an integer, it will return 23.

This behavior won't be changed, because other scenarios depend on it. For the preceding example, you can fix the issue by introducing an additional decimal attribute and a calculation.

For example, you can set up the following attributes on a production configuration model:

- Input (integer)
- Percent (decimal)
- ResultDecimal (decimal)
- ResultInteger (integer)

You can then add the following calculations:

- *ResultDecimal* = *Input* × *Percent* ÷ 100
- *ResultInteger* = *ResultDecimal*
