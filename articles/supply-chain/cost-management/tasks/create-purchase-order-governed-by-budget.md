--- 
# required metadata 
 
title: Create a purchase order governed by budget
description: Use this procedure to create a purchase order that is checked for available budget. 
author: JennySong-SH
ms.date: 06/20/2017
ms.topic: business-process 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
# ms.search.form:   
audience: Application User 
# ms.devlang:  
ms.reviewer: kamaybac
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: yanansong
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Create a purchase order governed by budget

[!include [banner](../../includes/banner.md)]

Use this procedure to create a purchase order that is checked for available budget. This recording uses the USMF demo data company.


## Review the budget control configuration
1. Go to Budgeting > Setup > Budget control > Budget control configuration.
2. Click the Budget funds available tab.
3. Click the Documents and journals tab.
4. Click the Define budget control rules tab.
5. Click the Define budget groups tab.
6. Close the page.

## Create the purchase order header
1. Go to Procurement and sourcing > Purchase orders > All purchase orders.
2. Click New.
3. In the Vendor account field, enter or select a value.
4. Expand the General section.
5. In the Accounting date field, set the date to '2016-01-01'.
6. Click OK.

## Add a purchase order line
1. In the Procurement category field, enter or select a value.
2. Set Quantity to '2'.
3. In the Unit field, enter or select a value.
4. Set Unit price to '10000'.
5. Click Financials.
6. Click Distribute amounts.
7. In the Ledger account field, specify the value '601300-001-023--'.
8. Close the page.

## Perform budget checking
1. Click Financials.
2. Click Perform budget checking.
3. Click Financials.
4. Click Budget check errors or warnings.
5. Click Close.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]