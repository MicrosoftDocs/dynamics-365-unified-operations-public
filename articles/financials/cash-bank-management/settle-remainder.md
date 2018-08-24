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

You can settle the amount remaining from settlement activity by applying that amount to a ledger account. 
You can settle the remainder when you are settling amounts entered into a journal or when you are only settling open transactions.

## Setting up defaults 
When you settle the remaining amount, you are prompted for a reason code and a ledger account for the remainder. 
You can setup a default reason code and a default account in the Accounts receivable and Accounts payable parameters

1)  Click on Accounts receivable > Parameters > Settlements or on Accounts payable > Parameters > Settlements
2)  In Default reason code for settle remainder, select a default reason code.   CHECK THIS
3)  The Account number associated with the reason code will be populated in the Default account number for settle remainder. 
You can change this default value.  CHECK THIS

## Settle remainder from a journal
You can enter a transaction in a journal like the payment journal or general journal and then settle transactions against it. 
For example, you can enter cash in a payment journal and then open the settlement page to apply that cash against an invoice. 
When you click on the Ok button, the open balance on the invoice is reduced by the cash amount. If the cash does not fully 
settle the invoice, the invoice is left open with a remaining amount to be settled at a later time.

To settle the remaining to a ledger account instead of leaving the invoices open, perform the following steps:
1)  In the settlement page, mark the invoices or transactions that you want to settle
2)  Instead of clicking on Ok, click on Settle remainder
3)  A dialogue will appear. It will show you the amount that will be settled against a ledger account, the date 
that will be used to settle the remainder, the default reason code from the parameters, and the default account from the parameters. 
4)  Select a new Adjustment reason if you want to change the default reason. The default Adjustment account will be changed to the
account associated with the reason code.
5)  Edit the Adjustment account if you want to change it.
6)  Click on Settle remainder.
7)  You will be returned to the journal page. An additional journal line will be added to the journal with the adjustment amount as the amount and with the adjustment account as the offset amount.

When you post the journal, the open transaction will be fully settled.

## Settle remainder when you are only settling open transactions
You can settle open transactions and also settle the remainder just as you can with a journal by performing the following steps.

1)  In the settlement page, mark the invoices or transactions that you want to settle
2)  Instead of clicking on Ok, click on Settle remainder
3)  A dialogue will appear. It will show you the amount that will be settled against a ledger account, the date 
that will be used to settle the remainder, the default reason code from the parameters, and the default account from the parameters.
4)  Select a new Adjustment reason if you want to change the default reason. The default Adjustment account will be changed to the
account associated with the reason code.
5)  Edit the Adjustment account if you want to change it.
6)  You can also specify whether you want to create a payment journal with the settlement remainder or just post it without a journal. Select Yes for Edit in journal to create a payment journal. You will be able to edit the payment journal that you create.
7)  Click on Settle remainder.
8)  If you created a payment journal, you will be returned to the journal page. An journal line will be added to the journal with the adjustment amount as the amount and with the adjustment account as the offset amount. When you post the journal, the open transaction will be fully settled.
