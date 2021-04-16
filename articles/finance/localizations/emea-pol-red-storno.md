---
# required metadata

title: Activate Storno accounting for Poland
description: This topic provides information about storno accounting for Poland.
author: ShylaThompson
ms.date: 09/11/2018
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Poland
# ms.search.industry: 
ms.author: roschlom
ms.dyn365.ops.version: AX 7.0.1
ms.search.validFrom: 2016-05-31

---


# Activate storno accounting for Poland

[!include [banner](../includes/banner.md)]

Use these procedures to set up storno accounting. In storno accounting, you reverse the sign on amounts to reverse incorrect original transactions. For example, the following transactions are incorrectly recorded.

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

1. Click **General ledger** > **Setup** > **General ledger parameters**.
2. In the **Ledger** area, on the **Accounting rules** FastTab, in the **Transaction reversal** field group, set the **Correction** option to **Yes**.

## Set up storno accounting
After you activate storno accounting, you can set up parameters in the application modules. The parameters that are specific to a module typically use storno accounting by default for various processes in the module. You can change the default setting when it appears on a page. However, the setting does not appear on all pages. Some pages always use the default setting during processing, and you cannot change the setting.

### Set up storno accounting in Accounts payable
On the  **Accounts payable parameters** page, in the **Invoice** area, set the **Credit note as correction** option to **Yes**. By default, credit notes are now posted as storno transactions.

### Set up storno accounting in Accounts receivable
1. Go to the **Accounts receivable parameters** page.
2. In the **Updates** area, in the **Advance invoice** field group, set the **Credit note as correction** option to **Yes**. By default, credit notes for advance invoices are now posted as storno transactions.
3. Set the **Reversal as correction** option to **Yes**. By default, reversals for advance invoices are now posted as storno transactions.
4. In the **Invoice** field group, set the **Credit note as correction** option to **Yes**. By default, credit notes for invoices are now posted as storno transactions.

### Set up storno accounting in Inventory and warehouse management
1. Go to the **Inventory and warehouse management parameters** page.
2. In the **General** area, in the **Correction** field group, set the **Inventory adjustment – correction** option to **Yes**. By default, adjustments to inventory are now posted as storno transactions.

### Set up storno accounting in Project management and accounting
1. Go to the **Project management and accounting parameters** page.
2. In the **General** area, in the **Adjustment** field group, set the **Adjustment of project transactions – correction** option to  **Yes**. By default, adjustments to project transactions are now posted as storno transactions.
3. In the **Journals** area, in the **Ledger posting** field group, set the **Negative transactions – correction** option to **Yes**. By default, project journal entries that have a negative cost amount are now posted as storno transactions.

### Create an Invoice storno credit note   
 1. For a confirmed purchase order, on the Action Pane, click **Invoice**.  
 2. Click **Invoice**.  
 3. On the Action Pane, click **Default from: Product receipt quantity**.  
 4. In the **Default quantity for lines** field, select an option.  
 5. Click **OK**.  
 6. Set the **Credit correction** option to **Yes**.  
 7. In the **Number** field, type a value.  
 8. In the **Invoice date** field, enter a date.  
 9. Click **Post**.  



[!INCLUDE[footer-include](../../includes/footer-banner.md)]