---
title: EEU-00047 Advance payment to employee
description: This procedure demonstrates how to set up and register transactions for an advance holder.
author: kfend
ms.date: 08/29/2018
ms.topic: how-to
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: Czech Republic, Estonia, Hungary, Latvia, Lithuania, Poland, Russia
ms.author: kfend
ms.search.validFrom: 2016-06-30
ms.dyn365.ops.version: Version 7.0.0
ms.search.form: RCashTable, LedgerJournalSetup, HcmWorkerGroup_RU, EmplPosting_RU, VendParameters, RCashPosting, BankParameters, PaymTerm, HcmWorker, HcmWorkerNewWorker, HcmWorkerAdvHolderTableListPage_RU, HcmWorkerAdvHolderTable_RU, PurchTable, PurchCreateOrder, HcmAdvHolderLookup_RU, InventItemIdLookupPurchase, VendEditInvoice, VendEditInvoiceDefaultQuantityForLinesDropDialog, EmplTrans_RU, EmplBalance_RU
---
# EEU-00047 Advance payment to employee

[!include [banner](../../includes/banner.md)]

This procedure demonstrates how to set up and register transactions for an advance holder. This procedure was created using the demo data company DEMF with a primary address in Lithuania. This task only works for legal entities with a primary address in Poland, Lithuania, Latvia, Estonia, Czech Republic, or Hungary. This procedure is for a feature that was added in Dynamics 365 for Operations version 1611.


## Create a new cash account
1. Go to Cash and bank management > Bank accounts > Cash accounts.
2. Click New.
3. In the Cash field, type a value.
4. In the Name field, type a value.
5. In the Number sequence group field, enter or select a value.
6. Expand the Validation section.
7. In the Currency field, enter or select a value.
8. Select Yes in the Negative cash field.
9. Click Save.

## Create a new journal
1. Go to General ledger > Journal setup > Journal names.
2. Click New.
3. In the Name field, type a value.
4. In the Voucher series field, enter or select a value.
5. Click Save.
6. Click New.
7. In the Name field, type a value.
8. In the Journal type field, select an option.
9. In the Voucher series field, enter or select a value.
10. Click Save.

## Create an advance holder group
1. Go to Accounts payable > Setup > Advance holders > Advance holder groups.
2. Click New.
3. In the Group field, type a value.
4. In the Description field, type a value.
5. Click Save.

## Create an employee posting profile
1. Go to Accounts payable > Setup > Advance holders > Employee posting profiles.
2. Click New.
3. In the Posting profile field, type a value.
4. In the Description field, type a value.
5. In the list, mark the selected row.
6. In the Valid for field, select an option.
7. In the Summary account field, specify the desired values.
8. Click Save.

## Set up advance holder parameters
1. Go to Accounts payable > Setup > Accounts payable parameters.
2. Click the Advance holders tab.
3. In the Posting profile field, enter or select a value.
4. In the Name field, enter or select a value.
5. In the Cash field, enter or select a value.
6. In the Name field, enter or select a value.
7. In the Account type field, select an option.
8. In the Main account field, specify the desired values.
9. Click the Number sequences tab.
10. Click Save.

## Set up a cash posting profile
1. Go to Cash and bank management > Setup > Cash posting profiles.
2. Click New.
3. In the Cash posting field, type a value.
4. In the Description field, type a value.
5. In the list, mark the selected row.
6. In the Valid for field, select an option.
7. In the Main account field, specify the desired values.
8. Click Save.

## Set up cash and bank parameters
1. Go to Cash and bank management > Setup > Cash and bank management parameters.
2. Click the Cash tab.
3. In the Cash field, enter or select a value.
4. In the Cash posting field, enter or select a value.
5. Click Save.
6. Click the Number sequences tab.
7. In the list, find and select the desired record.
8. In the Number sequence code field, enter or select a value.
9. In the list, find and select the desired record.
10. In the Number sequence code field, enter or select a value.
11. Click Save.

## Set up terms of payment
1. Go to Accounts payable > Payment setup > Terms of payment.
2. Click Edit.
3. Select Yes in the From advance holder field.
4. Click Save.

## Create a new worker
1. Go to Human resources > Workers > Workers.
2. Click New.
3. In the First name field, type a value.
4. In the Last name field, type a value.
5. In the Worker ID field, type a value.
6. Click Hire new worker.
7. Click Save.

## Set up a worker as an advance holder
1. Go to Accounts payable > Advance holders > Advance holders.
2. Click Edit.
3. In the Group field, enter or select a value.
4. Select Yes in the Advance holder field.
5. Click Save.

## Create and post a purchase order invoice
1. Go to Accounts payable > Purchase orders > All purchase orders.
2. Click New.
3. In the Vendor account field, enter or select a value.
4. Click OK.
5. In the Lines or header field, select an option.
6. Expand the Price and discount section.
7. In the Terms of payment field, enter or select a value.
8. In the Advance holder field, enter or select a value.
9. In the Lines or header field, select an option.
10. In the list, mark the selected row.
11. In the Item number field, enter or select a value.
12. In the Quantity field, enter a number.
13. In the Unit price field, enter a number.
14. Click Save.
15. On the Action Pane, click Purchase.
16. Click Confirm.
17. On the Action Pane, click Invoice.
18. Click Invoice.
19. Click Default from: Product receipt quantity to open the drop dialog.
20. In the Default quantity for lines field, select an option.
21. Click OK.
22. In the Number field, type a value.
23. In the Invoice description field, type a value.
24. In the Invoice date field, enter a date.
25. In the Date of VAT register field, enter a date.
26. In the Receive document date field, enter a date.
27. Click Post.

## Balance and close advance holders transactions
1. Go to Accounts payable > Advance holders > Advance holders.
2. Click Transactions.
3. Close the page.
4. Click Balance.
5. Click Close via bank.
6. Select Yes in the Automatic field.
7. In the Amount to be transferred. field, enter a number.
8. Click OK.
9. Click Close via cash.
10. Select Yes in the Automatic field.
11. Click OK.
12. Close the page.
13. Click Transactions.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
