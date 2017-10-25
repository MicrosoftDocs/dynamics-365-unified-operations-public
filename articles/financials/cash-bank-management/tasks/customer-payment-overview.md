--- 
# required metadata 
 
title: Customer payment overview
description: This task guide walks through various methods used to enter customer payments. 
author: kweekley
manager: AnnBe 
ms.date: 11/11/2016
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
# ms.search.form:   
audience: Application User 
# ms.devlang:  
ms.reviewer: twheeloc
ms.search.scope: Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: kweekley
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Customer payment overview

[!include[task guide banner](../../includes/task-guide-banner.md)]

This task guide walks through various methods used to enter customer payments. This task uses the USMF demo company.

1. Go to Accounts receivable > Payments > Payment journal.
2. Click New.
3. Select the payment journal which the customer payments will be saved.
4. Select or manually enter the journal.
5. Click Enter customer payments.
    * Enter customer payments is used to record one customer payment at a time. You enter the payment information at the top, and then you can mark the invoices that were paid by the payment, all from the same page.  
6. Enter the customer from whom you received the payment.
    * If you don't know the customer but do know a transaction that was paid, you can use the Transaction field to enter the payment. Enter or select the invoice in the Transaction field. The customer will automatically default after you select the transaction.  
7. In the Payment reference field, enter a payment reference.
    * The payment reference could be the customer's check number or a reference from the customer's electronic payment. The payment reference is only required if you mark to include the payment on a deposit slip.  
8. Select whether the payment will be included on a deposit slip. 
9. Enter the amount of the customer payment.
    * The payment amount will not default. It must be manually entered.  
10. Mark the invoices that were paid by the customer.
    * If the payment is a prepayment, you are not required to mark any invoices for settlement. The payment can still be saved and posted. Settlement to an invoice can happen at a later time.  
11. Enter the amount of the payment that should be settled to the marked invoice. 
    * This field can be used when the payment is for a partial payment. If you don't enter an amount, the amount to settle will automatically be determined for you.  
12. Click Save in journal.
    * Before you save the payment to the journal, make sure that the offset account is defined. Using Save in journal will save the payment and move it to the journal. You can then continue entering the next payment.  
13. Close the page.
14. Click Lines.
    * When opening Lines, you will see any payments you recorded on the Enter customer payments page and saved into the journal. You can also use this page to enter new customer payments, or edit existing customer payment before they are posted.  
15. Click New to create another payment. 
16. Select the customer from whom you received the payment.
    * If you don't know the customer but know an invoice paid by the payment, use the Invoice field to manually enter or select the invoice. The customer will default after the invoice is selected.  
17. Click Settle transctions to mark invoices that were paid.
    * You are not required to settle the payment to any invoices. If this is a prepayment or if you don't know what invoice was paid, you can enter and post the payment. The payment can be settled to an invoice at a later point.  
18. Mark the invoices paid by the payment. 
19. Enter the amount of the payment that will be settled to the invoice.
20. Click OK.
21. In the Payment reference field, Enter a payment reference. .
    * The payment reference is only required if you mark to include the payment on a deposit slip.  
22. Post the customer payments. 

