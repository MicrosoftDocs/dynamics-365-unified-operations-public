---
title: Activate Storno accounting for Poland
description: Learn how to activate and set up storno accounting for Poland in Microsoft Dynamics 365 Finance.
author: AdamTrukawka
ms.author: atrukawk
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 06/19/2025
ms.reviewer: johnmichalak
ms.search.region: Poland
ms.search.validFrom: 2016-05-31
---


# Activate storno accounting for Poland

[!include [banner](../../includes/banner.md)]

This article explains how to activate and set up storno accounting for Poland in Microsoft Dynamics 365 Finance.

Use the following procedures to set up storno accounting. In storno accounting, you reverse the sign on amounts to reverse incorrect original transactions. For example, the following transactions are incorrectly recorded.

|Description        | Debit |Credit  |
|-------------------|-------|--------|
|Sales revenue      |       |100.00  |
|Accounts receivable|100.00 |        |

To reverse the transactions and post the reversing transactions as storno transactions, you enter the following information.

|Description        | Debit  |Credit   |
|-------------------|--------|---------|
|Sales revenue      |        |-100.00  |
|Accounts receivable|-100.00 |         |

Each reversing transaction appears in the same debit or credit column as the original transaction. By keeping amounts in their original columns and reversing the sign on the amounts, you effectively “zero out” the original transaction.

After you complete the following procedure, a transaction is created that automatically reverses storno transactions.

## Activate storno accounting

You must activate storno accounting in General ledger before you can set up storno parameters in any other module.

To activate storno accounting, follow these steps.

1. In Dynamics 365 Finance, go to **General ledger** \> **Setup** \> **General ledger parameters**.
1. In the **Ledger** area, on the **Accounting rules** FastTab, in the **Transaction reversal** field group, set the **Correction** option to **Yes**.

## Set up storno accounting

After you activate storno accounting, you can set up parameters in the application modules. The parameters that are specific to a module typically use storno accounting by default for various processes in the module. You can change the default setting when it appears on a page. However, the setting doesn't appear on all pages. Some pages always use the default setting during processing, and you can't change the setting.

### Set up storno accounting in Accounts payable

On the  **Accounts payable parameters** page, in the **Invoice** area, set the **Credit note as correction** option to **Yes**. By default, credit notes are now posted as storno transactions.

### Set up storno accounting in Accounts receivable

To set up storno accounting in Accounts receivable, follow these steps.

1. In Dynamics 365 Finance, go to **Accounts receivable parameters**.
1. In the **Updates** area, in the **Advance invoice** field group, set the **Credit note as correction** option to **Yes**. By default, credit notes for advance invoices are now posted as storno transactions.
1. Set the **Reversal as correction** option to **Yes**. By default, reversals for advance invoices are now posted as storno transactions.
1. In the **Invoice** field group, set the **Credit note as correction** option to **Yes**. By default, credit notes for invoices are now posted as storno transactions.

### Set up storno accounting in Inventory and warehouse management

To set up storno accounting in Inventory and warehouse management, follow these steps.

1. In Dynamics 365 Finance, go to **Inventory and warehouse management parameters**.
1. In the **General** area, in the **Correction** field group, set the **Inventory adjustment – correction** option to **Yes**. By default, adjustments to inventory are now posted as storno transactions.

### Set up storno accounting in Project management and accounting

To set up storno accounting in Project management and accounting, follow these steps.

1. In Dynamics 365 Finance, go to **Project management and accounting parameters**.
1. In the **General** area, in the **Adjustment** field group, set the **Adjustment of project transactions – correction** option to  **Yes**. By default, adjustments to project transactions are now posted as storno transactions.
1. In the **Journals** area, in the **Ledger posting** field group, set the **Negative transactions – correction** option to **Yes**. By default, project journal entries that have a negative cost amount are now posted as storno transactions.

### Create an Invoice storno credit note

To create an invoice storno credit note, follow these steps.

 1. For a confirmed purchase order, on the Action Pane, select **Invoice**.  
 1. Select **Invoice**.  
 1. On the Action Pane, select **Default from: Product receipt quantity**.  
 1. In the **Default quantity for lines** field, select an option.  
 1. Select **OK**.  
 1. Set the **Credit correction** option to **Yes**.  
 1. In the **Number** field, enter a value.  
 1. In the **Invoice date** field, enter a date.  
 1. Select **Post**.  



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
