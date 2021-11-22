--- 
title: Integers incorrectly rounded in product configuration model calculations 
description: Integer results aren't always rounded correctly when product configuration models are calculated. Fix the issue with an added decimal attribute and calculation. 
author: SmithaNataraj 
ms.date: 06/24/2021 
ms.topic: troubleshooting 
# ms.search.form: 
audience: Application User 
ms.reviewer: kamaybac 
ms.search.region: Global 
ms.author: smnatara 
ms.search.validFrom: 2021-06-24 
ms.dyn365.ops.version: 10.0.20 
--- 

# Integers incorrectly rounded when product configuration models are calculated

## Symptoms

This issue can occur when you perform the following series of actions:

1. Set up these attributes on a production configuration model:

    - Input (integer)
    - Percent (decimal)
    - Result (integer)

2. Create a calculation that has the following expression:

    *Result* = *Input* × *Percent* ÷ 100

In this case, the integer result isn't always correctly rounded. For example, if the input is 1,000, and the percentage is 2.40, you expect the integer result to be 24 because 2.40 percent of 1,000 is 24 (or 24.00 in decimal form). Instead, the result is shown as 23. However, when the percentage is 2.39, the calculation is rounded to 24 instead of 23. When the percentage is 2.50, the calculation is rounded to 25, as expected.

## Cause

This issue occurs because of the way that Microsoft Solver Foundation internally represents numbers by using fractions. For the preceding example, the result of the calculation where the percentage is 2.40 is represented as 27021597764222975 ÷ 1125899906842624 = 23.99999999999999911182158029987476766109466552734375. When .NET casts this value as an integer, it will return 23.

## Resolution

This behavior won't be changed because other scenarios depend on it. For the preceding example, you can fix the issue by introducing an additional decimal attribute and calculations.

For example, set up the following attributes on a production configuration model:

- Input (integer)
- Percent (decimal)
- ResultDecimal (decimal)
- ResultInteger (integer)

You can then add the following calculations:

- *ResultDecimal* = *Input* × *Percent* ÷ 100
- *ResultInteger* = *ResultDecimal*
