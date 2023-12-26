---
title: Setup fixed asset depreciation allocation
description: In Japan, the depreciation expenses of a particular fixed asset can be shared among multiple departments.
author: kfend
ms.date: 08/29/2018
ms.topic: how-to
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: China (PRC), Japan
ms.author: kfend
ms.search.validFrom: 2016-06-30
ms.dyn365.ops.version: Version 7.0.0
ms.search.form: 
  - AssetAllocationRuleSetup_CN
  - AssetPosting
---
# Setup fixed asset depreciation allocation

[!include [banner](../../includes/banner.md)]

In Japan, the depreciation expenses of a particular fixed asset can be shared among multiple departments. 



This task walks you through setting up fixed asset depreciation allocation. 



This task was created using the demo data company JPMF.


## Create a Fixed asset allocation rule
1. Go to Fixed assets > Setup > Depreciation allocation rules.
2. Click New.
3. In the Rule ID field, type a value.
4. In the Description field, type a value.
5. In the Dimension name field, type a value.
6. Click Add.
7. In the BusinessUnit field, type a value.
    * Enter the information for the first allocation target.  
8. In the Percentage field, enter a number.
    * The total of all the allocation target must be 100.  
9. In the Offset account field, specify the desired values.
10. Click Add.
11. In the BusinessUnit field, type a value.
12. In the Percentage field, enter a number.
    * The total of all the allocation target must be 100.  
13. In the Offset account field, specify the desired values.
14. Click Save.

## Assign a fixed asset allocation rule to a posting profile
1. Go to Fixed assets > Setup > Fixed asset posting profiles.
2. Click Edit.
3. In the Transaction type field, select 'Depreciation'.
4. In the list, find and select the desired record.
    * Select the record that you want to link the allocation rule to.  
5. Expand the Depreciation allocation rules section.
6. In the Asset allocation rule for depreciation field, type a value.
7. Click Save.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
