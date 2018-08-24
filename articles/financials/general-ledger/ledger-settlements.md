---
# required metadata

title: Ledger settlements
description: You can settle ledger transactions with this form.
author: mikefalkner
manager: aolson
ms.date: 08/24/2018
ms.topic: index-page
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form:  LedgerTransSettlement
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
ms.search.validFrom: 2018-10-31
ms.dyn365.ops.version: 8.1

---

# Ledger settlements

[!include [banner](../includes/banner.md)]

Ledger settlements allows you to match debit and credit transactions in the general ledger to ensure that related transactions have been cleared. You can also reverse your settlements if they were made in error.

## Settling transactions

To settle ledger transactions, perform the following tasks:
1)  Click on General ledger, Periodic, Ledger settlements
2)  You will see a list of all the unsettled transactions in the general ledger. They will have a status of "Not settled".
3)  Select one or more lines that you are considering for settlement. You will see the total Selected amount at the top of the form increase or decrease by the amount on the line that you selected
4)  When you have selected all of the transactions that you want to mark, Click on Mark selected. All of the Marked check boxes will be checked. You will see the total Marked amount at the top of the form increase or decrease by the amount on the line that you marked.
5)  You can also click on the Mark check box directly to mark a transaction for settlement. In a future release, we will also be adding a rules engine that will mark transactions based on column values that you specify.  
6)  When the Marked amount is zero, click on Settle marked transactions. The marked transactions will be given a status of "Settled"

## Reversing a settlement

You can reverse a settlement that was made in error. 
1)  Click on General ledger, Periodic, Ledger settlements
2)  You will see a list of all the unsettled transactions in the general ledger. Use the Status drop down filter to select Settled.
3)  Select one or more lines that you are considering for reversal. You will see the total Selected amount at the top of the form increase or decrease by the amount on the line that you selected
4)  When you have selected all of the transactions that you want to mark, Click on Mark selected. All of the Marked check boxes will be checked. You will see the total Marked amount at the top of the form increase or decrease by the amount on the line that you marked.
5)  You can also click on the Mark check box directly to mark a transaction for settlement. 
6)  When the Marked amount is zero, click on Reverse marked transactions. The marked transactions will be given a status of "Unsettled"

## Making it easier for you to find transactions

There are additional capabilities on the Ledger settlement page that make it easier to find information:
1)  The Mark selected button will check the Marked box for all lines that are selected
2)  The Unmark selected button will uncheck the Marked box for all lines that are selected
3)  The Marked filter will filter your transactions by the boxes that are marked or unmarked
4)  The Status filter will filter your transactions by Settled or Not settled
5)  The Sort by amount button allows you to sort the amounts by absolute value so that you can group debits and credits with the same amount together
6)  The Posting layer filter allows you to select the posting layer for the transactions that you want to display
7)  The Financial dimension set drop down allows you to add the financial dimensions as a column so you can filter on each dimension

You will also see a second grid at the bottom of the form that is identical to the first grid on the page. This second grid allows you to search for different combinations of transactions without changing the filters or settings that you are using in the first grid. You can select lines, mark transactions, and perform the same tasks in both grids. 

