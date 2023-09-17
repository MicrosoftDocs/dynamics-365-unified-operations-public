---
title: Maintain fixed-asset master data files for deductible expenses
description: This task walks you through maintaining fixed asset master data files for deductible expenses.
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
  - AssetGroup, AssetGroupBookSetup
  - AssetTable, AssetBook
---
# Maintain fixed-asset master data files for deductible expenses

[!include [banner](../../includes/banner.md)]

This task walks you through maintaining fixed asset master data files for deductible expenses.



This task was created using the demo data company JPMF.


## Setups in Fixed asset groups
1. Go to Fixed assets > Setup > Fixed asset groups.
2. Click New.
3. In the Fixed asset group field, type a value.
4. In the Name field, type a value.
5. Select Yes in the Autonumber fixed assets field.
6. Select a number sequence code to autogenerate the fixed asset number.
7. Select the default  location for new fixed assets.
8. Click Books.
9. Click New.
10. In the Book field, type a value.
    * Example: 200RED_CUR  
11. Expand the General section.
    * Configure the options.  
    * Refer other materials for the details of each of the options.  
12. Click Save.
13. Click New.
14. In the Book field, type a value.
    * Example: 250NDB_TAX  
15. Expand the General section.
    * Configure the options.  
    * Refer other materials for the details of each of the options.  
16. Click Save.

## Creation of Fixed asset
1. Go to Fixed assets > Fixed assets > Fixed assets.
2. Click New.
3. In the Fixed asset group field, type a value.
    * You can use the fixed asset group that you have just created, or you can use BUIL-M.  
4. Click Books.
    * Verify that the books were created automatically.  



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
