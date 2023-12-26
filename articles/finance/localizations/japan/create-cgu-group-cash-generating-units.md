---
title: Create CGU group and cash generating units
description: In Japan, an impairment on fixed assets can be based on either individual fixed assets or cash generating units.
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
ms.search.form: AssetImpairmentCashGenUnitGroup_JP, SysQueryForm, AssetImpairmentCashGenUnit_JP
---
# Create CGU group and cash generating units

[!include [banner](../../includes/banner.md)]]

In Japan, an impairment on fixed assets can be based on either individual fixed assets or cash generating units. When measuring impairment based on cash generating units, the first step is to group the fixed assets into cash generating units. 



Multiple sets of cash generating units are allowed so that you can choose the most appropriate CGU. This is achieved through the creation of CGU groups. 



This procedure walks you through creating CGU groups and cash generating units. You will also learn how to assign fixed assets to cash generating units and how to assign shared assets and goodwill to CGU groups. 



In order to complete this task, the Fixed Asset configuration key must be selected.



This procedure was created using the demo data company JPMF.


## Create a CGU group
1. Go to Fixed assets > Setup > Impairment > CGU groups.
2. Click New.
    * You can create multiple CGU groups for testing if you are not sure about the appropriate combinations of fixed assets and cash generating units.  
3. In the CGU group field, type a value.
4. In the Description field, type a value.
5. In the Impairment of goodwill and shared asset field, select an option.
    * Select the method according to your corporate policy.  
6. Click Save.

## Create cash generating units under the CGU group
1. Click New.
2. In the Name field, type a value.
3. Note the value in the Cash generating unit number field to reference later
    * You will need to reference this value when you configure the cash generating unit.  
4. Click New.
5. In the Name field, type a value.
6. Note the value in the Cash generating unit number field to reference later
    * You will need to reference this value when you configure the cash generating unit.  

## Assign shared assets and goodwill to the CGU group
1. Expand the Shared assets and goodwill section.
2. Click Massive import.
    * We recommend that you specify a condition that adds all the assets with that hit with the condition at once.   You can also enter asset one by one in the grid.  
3. In the Criteria field, type a value.
4. Click OK.

## Configure cash generating units
1. Click Assign fixed assets.
2. Use the Quick Filter to find the CGU to edit.
    * Enter the first cash generating unit number that you noted previously.  
3. Click Massive import.
    * We recommend you to specify a condition that adds all the assets with that hit with the condition at once.   You can also enter asset one by one in the grid.  
4. In the Criteria field, type a value.
    * For example: Location = FUKUOKA  
5. Click OK.
6. In the Undiscounted cash flow field, enter a number.
7. In the Recoverable value field, enter a number.
8. Click Save.
9. Use the Quick Filter to find the cash generating unit to edit.
    * Enter the second cash generating unit number that you noted previously.  
10. Click Massive import.
11. In the Criteria field, type a value.
    * For example: Location = OSAKA  
12. Click OK.
13. In the Undiscounted cash flow field, enter a number.
14. In the Recoverable value field, enter a number.
15. Click Save.

## Activate the CGU group
1. Click Activate.
    * Only active CGU groups are allowed to run recognition tests.  
2. Click Yes.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
