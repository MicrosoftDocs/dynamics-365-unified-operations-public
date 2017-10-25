--- 
# required metadata 
 
title: Configure depreciation profile and posting profile for additional depreciation (Japan)
description: Use this procedure to learn how to configure a depreciation profile and a posting profile for special depreciation. 
author: ShylaThompson
manager: AnnBe 
ms.date: 11/11/2016
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
# ms.search.form:   
audience: Application User 
# ms.devlang:  
ms.reviewer: shylaw
ms.search.scope: Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Japan
# ms.search.industry: 
ms.author: shylaw
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Configure depreciation profile and posting profile for additional depreciation (Japan)

[!include[task guide banner](../../includes/task-guide-banner.md)]

Use this procedure to learn how to configure a depreciation profile and a posting profile for special depreciation.

In Japan, special depreciation is permitted under certain conditions. It is treated as extraordinary depreciation. 

In order to complete this procedure, the Fixed Assets configuration key must be selected.

This procedure was created using the demo data company JPMF.




## Configure a depreciation profile
1. Go to Fixed assets > Setup > Depreciation profiles.
2. Click New.
3. In the Depreciation profile field, type a value.
4. In the Name field, type a value.
5. In the Method field, select 'Special depreciation'.
6. In the Accounting method field, select an option.
    * Choose Reserve for reserve method, choose direct-off for direct off method for journalization. Reserve method is usually a more preferred representation on the financial statement.  
7. In the Apply number of periods field, enter a number.
8. In the Base ratio field, enter a number.
    * Enter 1 for 100%. The actual value can vary depending on the fixed asset.  
9. In the Special depreciation rate field, enter a number.
    * The special depreciation amount is calculated as the product of Acquisition cost, Base ratio and Special depreciation rate.  Enter 0.3 for 30%. The actual value can vary depending on the fixed asset.  
10. Click Save.

## Configure a posting profile
1. Go to Fixed assets > Setup > Fixed asset posting profiles.
2. Click Edit.
3. In the Transaction type field, select 'Extraordinary depreciation'.
    * Special depreciation is posted as extraordinary depreciation.  
    * Optional: configure the Main account and Offset account.  
    * You must click Edit before you can modify these account fields.  

