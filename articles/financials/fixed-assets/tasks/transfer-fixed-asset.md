--- 
# required metadata 
 
title: Transfer a fixed asset
description: This task guide will transfer the financial information for a fixed asset book from one financial dimension set to a new financial dimension set. 
author: saraschi2
manager: AnnBe 
ms.date: 02/23/2017
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
# ms.search.form:   
audience: Application User 
# ms.devlang:  
ms.reviewer: twheeloc
ms.search.scope: Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: saraschi
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Transfer a fixed asset

[!include[task guide banner](../../includes/task-guide-banner.md)]

This task guide will transfer the financial information for a fixed asset book from one financial dimension set to a new financial dimension set.  It uses the Accountant role and demo data for the USMF legal entity.

1. Go to Fixed assets > Fixed assets > Fixed assets.
2. In the list, find and select the fixed asset to transfer.
3. On the Action Pane, click Fixed asset.
4. Click Transfer fixed assets.
5. In the Transfer date field, enter a date.
6. Enter comments to describe the transfer.
    * This list shows all books for the fixed asset.  
7. Mark the books you want to transfer to a new financial dimension set.
    * This list shows the existing financial dimension values for the selected book.  
    * Select the financial dimension you want to update for the selected fixed asset book.  
8. In the Financial dimension field, click the drop down button to open the lookup.
    * Set other financial dimension values as appropriate.  
    * All financial dimension values change when a transfer occurs, whether a value has been entered or left blank. For example, if you entered a value for the BusinessUnit and left the CostCenter and Department financial dimensions blank. If your account structure allows blank values for CostCenter and Department, the transfer would result in each value model having the new value for BusinessUnit and a blank value for CostCenter and Department.  
9. Click Update.
    * You have the opportunity to preview the changes before finalizing the transfer.  
    * Review results before transferring the fixed asset books.  
10. Click Transfer.

