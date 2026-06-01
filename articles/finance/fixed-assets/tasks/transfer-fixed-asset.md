--- 
title: Transfer a fixed asset
description: Learn how to transfer the financial information for a fixed asset book from one financial dimension set to a new financial dimension set.
author: moaamer
ms.author: moaamer
ms.topic: how-to
ms.date: 03/28/2023
ms.custom:
ms.reviewer: twheeloc   
audience: Application User  
ms.search.region: Global
ms.search.validFrom: 2016-06-30
ms.search.form: AssetTable, AssetTransfer, DimensionLookup, AssetTransferConfirmation 
ms.dyn365.ops.version: Version 7.0.0 
---

# Transfer a fixed asset

[!include [banner](../../includes/banner.md)]

This article describes how to transfer the financial information for a fixed asset book from one financial dimension set to a new financial dimension set.  

1. Go to **Fixed assets > Fixed assets > Fixed assets**.
1. In the list, find and select the fixed asset to transfer.
1. On the Action Pane, select **Fixed asset**.
1. Select **Transfer fixed assets**.
1. In the **Transfer date** field, enter a date.
1. Enter comments to describe the transfer.
    
    This list shows all books for the fixed asset.  
1. Mark the books you want to transfer to a new financial dimension set.
    * This list shows the existing financial dimension values for the selected book.  
    * Select the financial dimension you want to update for the selected fixed asset book.  
1. In the **Financial dimension** field, select the dropdown button to open the lookup.
    * Set other financial dimension values as appropriate.  
    * All financial dimension values change when a transfer occurs, whether a value is entered or left blank. For example, if you enter a value for the BusinessUnit and leave the CostCenter and Department financial dimensions blank. If your account structure allows blank values for CostCenter and Department, the transfer results in each value model having the new value for BusinessUnit and a blank value for CostCenter and Department.  
1. Select **Update**.
    * You can preview the changes before finalizing the transfer.  
    * Review results before transferring the fixed asset books.  
1. Select **Transfer**.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
