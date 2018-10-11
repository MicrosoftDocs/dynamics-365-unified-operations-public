---
# required metadata

title: Settle remainder
description: You can settle the amount remaining from settlement activity by applying that amount to a ledger account.
author: mikefalkner
manager: aolson
ms.date: 09/01/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: CustOpenTrans, LedgerJournalTransCustPaym, LedgerJournalTransVendPaym, VendOpenTrans
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: shylaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
# ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: mikefalkner
ms.search.validFrom: 2018-11-30
ms.dyn365.ops.version: 8.1.1

---

# Settle remainder

[!include [banner](../includes/banner.md)]

You can settle the amount remaining from settlement activity by applying that amount to a ledger account or another customer. 
You can settle the remainder when you are settling amounts entered into a journal or when you are only settling open transactions.

## Setting up defaults 
You must enable the Settle remainder feature and set up the default settings before you use Settle remainder

1)  Click on **Accounts receivable > Parameters > Settlements** or **Accounts payable > Parameters > Settlements**
2)  Click on the **Settlement** tab and click on **Enable settle remainder**
3)  In **Default reason code**, select a default reason code. The **Default settle remainder account** will default to the account assigned to the reason code
3)  Update the **Default settle remainder account** as needed
4)  In the **Default journal name**, select a payment journal that will be used if you want to create a payment journal when you only settling open transactions. 

## Settle remainder from a journal
If you do not enable the **Settle remainder** feature, you can still enter a transaction in a payment journal and then settle
transactions against it as you have done in the past. When you click on the Ok button, the open balance on the invoice 
is reduced by the cash amount. If the cash does not fully settle the invoice, the invoice is left open 
with a remaining amount to be settled at a later time.

When the **Settle remainder** feature is enabled, you can settle the remaining amount to a ledger account or another customer instead of leaving the invoices open. 
To settle the remainder from the settlement page, perform the following steps:
1)  In the settlement page, mark the invoices or transactions that you want to settle
2)  Click on Ok
3)  A dialogue will appear. It will show you the amount that will be settled against a ledger account, the date 
that will be used to settle the remainder, the default reason code from the parameters, and the default account from the parameters. 
4)  Select a new settlement reason if you want to change the default reason. The settlement account will be changed to the
account associated with the reason code.
5)  Edit the settlement account if you want to change it.
6)  If you want the remainder to be moved to another customer, then select a customer in the settle remainder against account
6)  Click on Settle remainder.
7)  You will be returned to the journal page. An additional journal line will be added to the journal with the settlement amount as the amount and with the settlment account as the offset amount. If you added a customer to move the settlement amount to, then an additional line will be added to the payment journal to move the settlement amount to that customer.

When you post the payment journal, the open transaction will be fully settled.

## Settle remainder when you are only settling open transactions
You can also settle the remainder when you are settling open transactions without a payment journal.

To settle the remainder, perform the following steps:

1)  In the settlement page, mark the invoices or transactions that you want to settle
2)  Instead of clicking on **Post**, click on **Settle remainder**
3)  A dialogue will appear. It will show you the amount that will be settled against a ledger account, the date 
that will be used to settle the remainder, the default reason code from the parameters, and the default account from the parameters. 
4)  Select a new **settlement reason** if you want to change the default reason. The **settlement account** will be changed to the
account associated with the reason code.
5)  Edit the **settlement account** if you want to change it.
6)  You can also choose to create a payment journal with the settlement remainder or just post it without a journal. Select Yes for **Post journal** to create a payment journal. You will be able to edit the payment journal that you create.
7)  Click on **Settle remainder**. If you chose to create a journal, the button will change to **Create journal**. Click on **Create journal** instead.
8)  If you created a payment journal, you will be returned to the journal page. An journal line will be added to the journal with the adjustment amount as the amount and with the adjustment account as the offset amount. If you added a customer to move the settlement amount to, then an additional line will be added to the payment journal to move the settlement amount to that customer. When you post the journal, the open transaction will be fully settled.
