--- 
# required metadata 
 
title: Set up vendor master and purchase order to be target of consolidated invoice (Japan)
description: In Japan, the vendors usually use consolidated invoice for transactions. 
author: ShylaThompson
manager: AnnBe 
ms.date: 11/14/2016
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
# Set up vendor master and purchase order to be target of consolidated invoice (Japan)

[!include[task guide banner](../../includes/task-guide-banner.md)]

In Japan, the vendors usually use consolidated invoice for transactions. 



This task walks you through configuring a vendor master and purchase order to use the consolidated invoice. 



This task was created using the demo data company JPMF.


## Set up vendor master
1. Go to Accounts payable > Vendors > All vendors.
2. In the list, click the link in the selected row.
3. Expand or collapse the Payment section.
    * Verify that the terms of payment uses the Cutoff day.  
    * Specify a Consolidation day for the vendor.  
    * You might need to click Edit first, before you can update this field.  

## Set a purchase order to be target of consolidated invoice
1. Go to Accounts payable > Purchase orders > All purchase orders.
2. In the list, click the link in the selected row.
3. On the Action Pane, click Options.
4. Click Change view.
5. Click Header view.
    * Verify that the Target of consolidation slider is set to 'Yes'.  

