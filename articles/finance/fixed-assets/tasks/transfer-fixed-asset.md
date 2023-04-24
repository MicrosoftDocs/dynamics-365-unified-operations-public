--- 
# required metadata 
 
title: Transfer a fixed asset
description: This task guide will transfer the financial information for a fixed asset book from one financial dimension set to a new financial dimension set. 
author: moaamer
ms.date: 03/28/2023
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: AssetTable, AssetTransfer, DimensionLookup, AssetTransferConfirmation   
audience: Application User 
# ms.devlang:  
ms.reviewer: twheeloc
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: moaamer
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Transfer a fixed asset

[!include [banner](../../includes/banner.md)]

This task guide will transfer the financial information for a fixed asset book from one financial dimension set to a new financial dimension set.  

1. Go to **Fixed assets > Fixed assets > Fixed assets**.
2. In the list, find and select the fixed asset to transfer.
3. On the Action Pane, click **Fixed asset**.
4. Click **Transfer fixed assets**.
5. In the **Transfer date** field, enter a date.
6. Enter comments to describe the transfer.
    
    This list shows all books for the fixed asset.  
7. Mark the books you want to transfer to a new financial dimension set.
    * This list shows the existing financial dimension values for the selected book.  
    * Select the financial dimension you want to update for the selected fixed asset book.  
8. In the **Financial dimension** field, click the drop down button to open the lookup.
    * Set other financial dimension values as appropriate.  
    * All financial dimension values change when a transfer occurs, whether a value has been entered or left blank. For example, if you entered a value for the BusinessUnit and left the CostCenter and Department financial dimensions blank. If your account structure allows blank values for CostCenter and Department, the transfer would result in each value model having the new value for BusinessUnit and a blank value for CostCenter and Department.  
9. Click **Update**.
    * You have the opportunity to preview the changes before finalizing the transfer.  
    * Review results before transferring the fixed asset books.  
10. Click **Transfer**.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
