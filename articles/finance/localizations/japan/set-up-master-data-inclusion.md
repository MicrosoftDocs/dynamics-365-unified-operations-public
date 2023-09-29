---
title: Set up master data for inclusion of deductible expenses for multiple posting layers
description: This procedure walks you through creating fixed asset rules with required master data for inclusion of deductible expenses for multiple posting layers.
author: kfend
ms.date: 08/29/2018
ms.topic: how-to
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: Japan
ms.author: kfend
ms.search.validFrom: 2016-06-30
ms.dyn365.ops.version: Version 7.0.0
ms.search.form: 
  - AssetAdvancedRule_JP, AssetAdvancedRuleCreateEdit_JP
  - AssetBookTable
---
# Set up master data for inclusion of deductible expenses for multiple posting layers

[!include [banner](../../includes/banner.md)]

This procedure walks you through creating fixed asset rules with required master data for inclusion of deductible expenses for multiple posting layers. Before you can complete this procedure, the Fixed Assets configuration key must be selected. This procedure was created using the demo data company JPMF.


## Depreciation settlement rules
1. Go to Fixed assets > Setup > Depreciation settlement rules.
    * Optional: If the settlement rule table is empty, you will be asked if you want to import the default set of rules. Click OK to import the default set of rules.  
2. Click New.
3. In the Over depreciation field, select an option.
    * Select Over depreciation = Ordinary depreciation.  
4. In the Under depreciation field, select an option.
    * Select Under depreciation = Additional depreciation (reserve).  
5. Click OK.
6. In the Filter by rule type field, select an option.
    * Select Filter by rule type = Carry forward of over depreciation or under depreciation amount.  
7. Click Edit rule.
8. In the Periods to carry forward(years) field, enter a number.
    * For this example, enter 5.  
9. Click OK.

## Book
1. Go to Fixed assets > Setup > Books.
2. Click New.
3. In the Book field, type a value.
    * For this example, Book = RB.  
4. In the Description field, type a value.
5. Expand the General section.
    * Configure the parameters according to the core fixed asset features.  
6. Expand the Derived books section.
7. Select the book on the tax layer that will be referencing this one.
    * If you add a derived book for the Acquisition type, it will simplify the operation by automatically acquiring the tax layer book.  Example: NSL_TAX  
8. Click Save.
9. Use the Quick Filter to find records. For example, filter on the Book field with a value of 'NSL_TAX'.
    * Search for the Tax layer book that you want to run settlement with the Current layer book.  
10. Expand the General section.
11. In the Referenced book field, type a value.
    * Type the book that you have just created.  
12. Click Save.
13. Close the page.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
