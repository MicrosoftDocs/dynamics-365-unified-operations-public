(---
# required metadata

title: Foreign currency revaluation for bank accounts
description: This article provides information about foreign currency revaluation for bank accounts.
author: ShylaThompson
manager: AnnBe
ms.date: 03/01/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:
audience: Application User
# ms.devlang: 
ms.reviewer: shylaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 11464
ms.search.region: Global
# ms.search.industry: 
ms.author: shylaw
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Currency revaluation for bank account transactions

[!include[banner](../includes/banner.md)]

## (PL) Revalue foreign currency amounts for bank account transactions

You can revalue foreign currency amounts for bank transactions, and you can create a report to view the bank transactions that have adjustments for foreign currency revaluations. 

1. Click Cash and bank management > Periodic tasks > Bank - Exchange adjustment (FIFO/LIFO). 
2. In the On date field, enter an end date for the revaluation. Only transactions that have a date that is before the date that is specified here are included in the calculation. 
3. Click Records to include, then Filter, and then click Add to add a bank account. 
4. If you do not specify a bank account, amounts are revaluated for all bank accounts. 
5. Click OK to close the query form. In the Foreign currency revaluation form, select the Recalculation check box to revalue foreign currency amounts for all open periods. 

## (PL) Create a report to view bank transactions that have adjustments for foreign currency revaluations

1. Click Cash and bank management > Inquiries and Reports > Bank - Exchange adjustment report. 
2. Click Records to include, then Filter to select one or more bank accounts to view information for. 
3. If you leave the Bank account field blank, you can view the bank transaction details for all bank accounts. 
4. Click OK to generate the report. 

## (LT, LV, EE, CZ) Calculate exchange rate adjustments for bank account transactions

You must revalue and adjust bank accounts if there is a difference in the exchange rate between the accounting currency and the reporting currency. This helps you to calculate the correct balance in the accounting currency and the reporting currency for the bank accounts. 

1. Click Cash and bank management > Setup > Cash and bank management parameters. 
2. In the left pane, click Number sequences. 
3. In the Number sequences area, in the Reference field, select a number sequence for the Bank - Exchange adjustment parameter. 
4. Close the form. 
5. Click General ledger > Setup > Currency > Currency exchange rates. In the Currency exchange rates form, you can define the exchange rate between two currencies or a currency pair. For more information, see Currency exchange rates (form) and Exchange rate types (form). 
6. Close the form. 
7. Click General ledger > Setup > Ledger. Select the main account in the Unrealized gain and the Unrealized loss fields that the exchange rates are posted for. 
8. Close the form. 
9. Click Cash and bank management > Periodic tasks > Foreign currency revaluation. 
10. In the On date field, select the revaluation or the adjustment date. 
11. In the From currency and the To currency fields, select the current currency code and the currency to which the adjustment is made. 
12. Click Records to Include, then Filter to set up the bank account, and then click OK. 
13. In the Foreign currency revaluation form, click OK. The adjustment for the bank account transactions on the selected date is calculated. 
   > [!NOTE]
   > You can view two separate transactions for the accounting currency and the reporting currency in the general ledger. For more information, see Bank transactions (form) and Voucher transactions (form). 
