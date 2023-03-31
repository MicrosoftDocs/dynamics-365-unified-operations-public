--- 
# required metadata 
 
title: Create a write-off journal for a customer
description: This task guide will show you how to set up the parameters for write-offs and then write off transactions from the Collections page, the Open customer invoices page, and the Customer page. 
author: ShivamPandey-msft
ms.date: 07/01/2019
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: CustParameters, CustPosting, DefaultDashboard, CustCollectionsPoolsListPage, CustWriteOff, LedgerJournalTable, LedgerJournalTransDaily, CustCollections, CustOpenInvoicesListPage, CustTable   
audience: Application User 
# ms.devlang:  
ms.reviewer: twheeloc
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: shpandey
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Create a write-off journal for a customer

[!include [banner](../../includes/banner.md)]

This task guide will show you how to set up the parameters for write-offs and then write off transactions from the Collections page, the Open customer invoices page, and the Customer page. This task uses the USMF demo company.


## Set up the write off parameters
1. Go to **Navigation pane > Modules > Credit and collections > Setup > Accounts receivable parameters**.
2. Click the **Collections** tab.
3. Expand or collapse the **Write-off** section.
    - The **Write-off journal** is the general journal that will hold the write-off transactions that you create.  
    - You can attach a reason code to every write-off. You can override this default at the time of the write-off.  
    - Set the **Separate sales tax** to Yes if you want to separate the sales tax from the original transaction in the write-off.  
4. Close the page.
5. Go to **Credit and collections > Setup > Customer posting profiles**. The write-off account will be used as the expense account or reserve adjustment in the general journal.
6. Close the page.

## Write off a customer balance from the aged balances page
1. Go to **Credit and collections > Collections > Aged balances**.
2. Mark the row for the customer that you want to write off. For example, mark the line with Birch Company on it.
3. On the **Action Pane**, click **Collect**.
4. Click **Write off**.
5. Click **OK**.
6. Close the page.
7. Go to **Navigation pane > Modules > General ledger > Journal entries > General journals**.
8. Select the journal batch number for the journal that contains your write-off. One line is created to reverse the customer balance. One or more lines are created to post the write-off to the write-off account.  
9. Close the page.


## Write off transactions from the collections page
1. Go to **Credit and collections > Collections > Aged balances**.
2. Select the name of the customer that has the transactions that you want to write off. For example, select Cave Wholesales (US-004).
3. Mark the row for the first transaction.
4. Mark the row for the second transaction.
5. Click **Write off**.
6. In the **Reason comment** field, type 'Bad debts'.
7. Click **OK**.
8. Close the page.
9. Close the page.
10. Go to **General ledger > Journal entries > General journals**.
11. Select the journal batch number for the journal that contains your write-off. One line is created to reverse the customer balance. One or more lines are created to post the write-off to the write-off account.  
12. Close the page.


## Write off an invoice from the Open customers invoices page
1. Go to **Navigation pane > Modules > Accounts receivable > Invoices > Open customer invoices**.
2. Mark the line for an invoice. For example, mark the line for CIV-000667.
3. On the **Action Pane**, click **Invoice**.
4. Click **Write off**.
5. Click **OK**.
6. Close the page.

## Write off a customer balance from the customer page
1. Go to **Accounts receivable > Customers > All customers**.
2. Select a customer account. For example, select US-001 (Contoso Retail San Diego).
3. On the **Action Pane**, click **Collect**.
4. Click **Write off**.
5. Click **OK**.
6. Close the page.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
