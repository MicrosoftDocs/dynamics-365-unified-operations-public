--- 
# required metadata 
 
title: Set up mandatory payment references
description: This article explains how to set up a mandatory payment reference for a specific ledger account and post a payment. 
author: EvgenyPopovMBS
ms.date: 08/01/2023
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: MainAccount, LedgerJournalTable, LedgerJournalTransDaily   
audience: Application User 
# ms.devlang:  
ms.reviewer: kfend
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Iceland
# ms.search.industry: 
ms.author: epopov
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Set up mandatory payment references

[!include [banner](../../includes/banner.md)]

This article explains how to set up a mandatory payment reference for a specific ledger account and post a payment. When you select the ledger account in the journal you must specify a payment reference for the journal line. This functionality is available for legal entities whose primary address is in Iceland.

## Set up the main account
1. Go to **General ledger** > **Chart of accounts** > **Accounts** > **Main accounts**.
2. Use the **Quick Filter** to find records. For example, filter on the **Main account** field with a value of '170150'.
3. In the list, select the link in the row you want to update.
4. Select **Edit**.
5. Select or clear the **Require payment reference** check box and then select **Save**.

## Create a payment with a payment reference
1. Go to **General ledger** > **Journal entries** > **General journals** and then select **New**.
2. In the list, mark the selected row.
3. In the **Name** field, select the drop-down, and in the list, select the link in the selected row.
4. Select **Lines** and in the list, mark the selected row.
5. In the **Account** field, specify a value.
6. In the **Debit** field, enter a number.
7. In the **Offset account** field, specify a value.
8. On the **Payment** tab, in the **Payment reference** field, enter a value.
9. Select **Save** and then select **Post**.




[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
