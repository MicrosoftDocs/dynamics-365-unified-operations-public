--- 
# required metadata 
 
title: MY-00006 02 Print GST customer invoices with a relief clause
description: This article explains how to print GST customer invoices that include a relief clause. 
author: EvgenyPopovMBS
ms.date: 08/29/2018
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: TaxGSTReliefCategory_MY, TaxGSTReliefGroup_MY   
audience: Application User 
# ms.devlang:  
ms.reviewer: kfend
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Malaysia
# ms.search.industry: 
ms.author: epopov
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# MY-00006 02 Print GST customer invoices with a relief clause

[!include [banner](../../includes/banner.md)]

After you complete these procedures, when you generate a tax invoice for a customer who has bought a GST relieved item or service, the relief clause is automatically included in the final printed invoice. You must be in the Accounting supervisor role to complete these procedures. This procedure was created using the demo data company MYMF.


## Create GST relief categories
1. Go to Tax > Setup > Sales tax > GST relief category.
2. Click New.
3. In the Relief item number field, type a value.
4. In the Relief schedule field, type a value.
    * Repeat the last two steps for each additional GST relief category that you want to create.  
5. Click Save.

## Create GST relief groups
1. Go to Tax > Setup > Sales tax > GST relief group.
2. Click New.
3. In the Name field, type a value.
4. In the Description field, type a value.
5. Expand or collapse the GST relief category section.
6. Click Add.
7. In the list, mark the selected row.
8. In the GST relief category field, click the drop-down button to open the lookup.
9. In the list, find and select the desired record.
10. In the list, click the link in the selected row.
    * Repeat this procedure to create additional GST relief groups if necessary.  
11. Click Save.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
