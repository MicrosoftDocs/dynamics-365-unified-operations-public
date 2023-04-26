---
# required metadata

title: Settle remainder
description: You can settle the amount remaining from settlement activity by applying that amount to a ledger account.
author: angelad116
ms.date: 01/29/2023
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: CustOpenTrans, LedgerJournalTransCustPaym, LedgerJournalTransVendPaym, VendOpenTrans
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
# ms.custom: 
# ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: angelading
ms.search.validFrom: 2018-12-01
ms.dyn365.ops.version: 8.1.3

---

# Settle remainder

[!include [banner](../includes/banner.md)]

You can settle the amount remaining from settlement activity by applying that amount to a ledger account or another customer. 
You can settle the remainder when you are settling amounts entered into a journal or when you are only settling open transactions.

## Setting up defaults 
You must enable the **Settle remainder** feature and set up the default settings before you use **Settle remainder**.

1)  Click **Accounts receivable > Parameters > Settlements** or **Accounts payable > Parameters > Settlements**.
2)  Select the **Settlement** tab and click **Enable settle remainder**.
3)  In **Default reason code**, select a default reason code. The reason codes must have already been set up in **Accounts receivable > Setup > Customer write-off reason codes** or **Accounts payable > Setup > Vendor write-off reason codes**. The **Default settle remainder account** will default to the account assigned to the write-off reason code.
3)  Update the **Default settle remainder account** as needed.
4)  In the **Default journal name**, select a payment journal that will be used if you want to create a payment journal when you only settle open transactions. If you enable the settle remainder feature, you must add a default journal name.

## Settle remainder from a journal
If you don't enable the **Settle remainder** feature, you can still enter a transaction in a journal and then settle transactions against it as you have done in the past. When you click the **OK** button, the open balance on the invoice is reduced by the cash amount. If the cash does not fully settle the invoice, the invoice is left open with a remaining amount to be settled at a later time.

When the **Settle remainder** feature is enabled, you can settle the remaining amount to a ledger account. You can also transfer the remainder to another customer account (for customer transactions) or another vendor (for vendor transactions) instead of leaving the invoices open. 

To settle the remainder from the **Settlement** page, perform the following steps:

1)  On the **Settlement** page, mark the invoices or transactions that you want to settle.
2)  Click the **Settle remainder** button.
3)  A dialog box will display, showing the amount that will be settled against a ledger account, the date that will be used to settle the remainder, the default reason code from the parameters, and the default account from the parameters. 
4)  Select a new settlement reason if you want to change the default reason. The settlement account will be changed to the account associated with the reason code.
5)  Edit the settlement account if you want to change it.
6)  If you are settling customer transactions and you want the remainder to be moved to another customer, then select a customer in the **Settle remainder against customer account**. If you are settling vendor transactions and you want the remainder to be moved to another vendor, then select a vendor in the **Settle remainder against vendor account**.
6)  Click **Settle remainder**.
7)  The **Journal** page will display. An additional journal line will be added to the journal with the settle remainder amount as the amount and with the settlement remainder account as the offset account. If you added a customer or vendor so that you can move the settlement amount to another customer or vendor, then an additional line will be added to the journal to move the settlement amount to that customer or vendor.

When you post the journal, the open transaction will be fully settled. 

## Settle remainder when you are only settling open transactions
You can also settle the remainder when you are settling open transactions without a journal.

To settle the remainder, perform the following steps:

1)  On the **Settlement** page, mark the invoices or transactions that you want to settle.
2)  Click on **Settle remainder**.
3)  A dialog box will display, showing the amount that will be settled against a ledger account, the date that will be used to settle the remainder, the default reason code from the parameters, and the default account from the parameters. 
4)  Select a new settlement reason if you want to change the default reason. The settlement account will be changed to the account associated with the reason code.
5)  Edit the **settlement account** if you want to change it.
6)  If you are settling customer transactions and you want the remainder to be moved to another customer, then select a customer in the **Settle remainder against customer account**. If you are settling vendor transactions and you want the remainder to be moved to another vendor, then select a vendor in the **Settle remainder against vendor account**
7)  You can also choose to create a payment journal with the settlement remainder or just post it without a journal. Select **Yes** for **Edit in journal** to create a payment journal. You will be able to edit the payment journal that you create.
8)  Click **Settle remainder**. If you chose to create a journal, the button will change to **Create journal**. Click **Create journal** instead.
9)  If you created a payment journal, the journal page will open after you click **Settle remainder**. A journal line will be added to the journal with the settle remainder amount as the amount and with the settlement remainder account as the offset account. If you added a customer or vendor so that you can move the settlement amount to another customer or vendor, then an additional line will be added to the journal to move the settlement amount to that customer or vendor.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
