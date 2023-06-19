--- 
# required metadata 
 
title: Customer payment overview
description: This procedure walks through the various methods used to enter customer payments. 
author: kweekley
ms.date: 05/23/2023
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: LedgerJournalTable, CustPaymEntry, CustTableLookup, LedgerJournalTransCustPaym, CustOpenTrans, BankAccountTableLookUp   
audience: Application User 
# ms.devlang:  
ms.reviewer: twheeloc
# ms.tgt_pltfrm:  
ms.collection: get-started
ms.search.region: Global
# ms.search.industry: 
ms.author: kweekley
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Customer payment overview

[!include [banner](../../includes/banner.md)]

This procedure walks through the various methods used to enter customer payments. This task uses the USMF demo company.

1. Go to **Accounts receivable > Payments > Payment journal**.
2. Click **New**.
3. Select the payment journal where the customer payments will be saved.
4. Select or manually enter the journal.
5. Click **Enter customer payments**. **Enter customer payments** is used to record one customer payment at a time. You enter the payment information at the top. You can mark the invoices that were paid by the payment.  
6. Enter the customer from whom you received the payment. If you don't know the customer but do know a transaction that was paid, use the **Transaction** field to enter the payment. Enter or select the invoice in the **Transaction** field. The customer will automatically default after you select the transaction.
7. In the **Payment reference** field, enter a payment reference. The payment reference could be the customer's check number or a reference from the customer's electronic payment. The payment reference is only required if you mark to include the payment on a deposit slip.  
8. In the **Deposit slip** field, select if the payment will be included on a deposit slip. 
9. In the **Amount** field, enter the amount of the customer payment. The payment amount won't default and must be manually entered. 
10. Mark the invoices that were paid by the customer. If the payment is a prepayment, you're not required to mark any invoices for settlement. The payment can still be saved and posted. Settlement to an invoice can happen at a later time.
11. Enter the amount of the payment that should be settled to the marked invoice. This field can be used when the payment is for a partial payment. If you don't enter an amount, the amount to settle will automatically be determined for you.
12. Click **Save in journal**. Before you save the payment to the journal, confirm that the offset account is defined. Using **Save in journal** will save the payment and move it to the journal. You can then continue entering the next payment.
13. Close the page.
14. Click **Lines**. When opening **Lines**, you will see any payments you recorded on the **Enter customer payments** page and saved into the journal. You can also use this page to enter new customer payments, or edit existing customer payment before they are posted.
15. Click **New** to create another payment. 
16. Select the customer from whom you received the payment. If you don't know the customer but know an invoice paid by the payment, use the **Invoice** field to manually enter or select the invoice. The customer will default after the invoice is selected.  
17. Click **Settle transactions** to mark invoices that were paid. You're not required to settle the payment to any invoices. If this is a prepayment or if you don't know what invoice was paid, you can enter and post the payment. The payment can be settled to an invoice at a later point.  
18. Mark the invoices paid by the payment. 
19. In the **Amount** field, enter the amount of the payment that will be settled to the invoice.
20. Click **OK**.
21. In the **Payment reference** field, enter a payment reference. The payment reference is only required if you mark to include the payment on a deposit slip.  
22. On **Action pane**, click **Post** to post the customer payments. 



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
