--- 
title: Set up mandatory payment references
description: Learn how to set up a mandatory payment reference for a specific ledger account and post a payment in Microsoft Dynamics 365 Finance.
author: kfend
ms.author: johnmichalak
ms.topic: how-to
ms.date: 12/05/2025
ms.custom: 
  - bap-template
ms.reviewer: johnmichalak  
ms.search.region: Iceland
ms.search.validFrom: 2016-06-30
ms.search.form: MainAccount, LedgerJournalTable, LedgerJournalTransDaily
---

# Set up mandatory payment references

[!include [banner](../../includes/banner.md)]

This article explains how to set up a mandatory payment reference for a specific ledger account and post a payment. 

When you select the ledger account in the journal, you must specify a payment reference for the journal line. 

The functionality described in the following procedures is available for legal entities whose primary address is in Iceland.

## Set up the main account

To set up the main account, follow these steps.

1. In Dynamics 365 Finance, go to **General ledger \> Chart of accounts \> Accounts \> Main accounts**.
1. Use the **Quick Filter** to find records. For example, filter on the **Main account** field with a value of "170150".
1. In the list, select the link in the row you want to update.
1. Select **Edit**.
1. Select or clear the **Require payment reference** checkbox, and then select **Save**.

## Create a payment with a payment reference

To create a payment with a payment reference, follow these steps.

1. In Dynamics 365 Finance, go to **General ledger \> Journal entries \> General journals**.
1. Select **New**.
1. In the list, mark the selected row.
1. In the **Name** field, select the drop-down, and in the list, select the link in the selected row.
1. Select **Lines** and in the list, and then mark the selected row.
1. In the **Account** field, enter a value.
1. In the **Debit** field, enter a number.
1. In the **Offset account** field, specify a value.
1. On the **Payment** tab, in the **Payment reference** field, enter a value.
1. Select **Save**.
1. Select **Post**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
