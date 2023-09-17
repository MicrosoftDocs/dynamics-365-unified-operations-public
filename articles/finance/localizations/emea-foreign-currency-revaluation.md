---
# required metadata

title: Foreign currency revaluation for bank accounts
description: This article provides information about foreign currency revaluation for bank accounts.
author: panolte
ms.date: 03/28/2018
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form:
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.search.region: Czech Republic, Estonia, Latvia, Lithuania, Poland
# ms.search.industry: 
ms.author: panolte
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Foreign currency revaluation for bank accounts

[!include [banner](../includes/banner.md)]

## Revalue foreign currency amounts for bank account transactions

> [!IMPORTANT]
> This section applies only to legal entities that have a primary address in Poland.

You can revalue foreign currency amounts for bank transactions. You can then create a report to view the bank transactions that have adjustments for foreign currency revaluations.

1. Select **Cash and bank management** &gt; **Periodic tasks** &gt; **Bank - Exchange adjustment (FIFO/LIFO)**.
2. In the **On date** field, enter an end date for the revaluation. The calculation includes only transactions that have a date that is before the specified date.
3. Select **Records to include** &gt; **Filter** &gt; **Add** to add a bank account. If you don't specify a bank account, amounts are revalued for all bank accounts.
4. Select **OK** to close the query page.
5. On the **Foreign currency revaluation** page, select the **Recalculation** check box to revalue foreign currency amounts for all open periods.

## Create a report to view bank transactions that have adjustments for foreign currency revaluations

> [!IMPORTANT]
> This section applies only to legal entities that have a primary address in Poland.

1. Select **Cash and bank management** &gt; **Inquiries and reports** &gt; **Bank - Exchange adjustment report**.
2. Select **Records to include** &gt; **Filter** to find one or more bank accounts to view information for.
3. Optional: In the **Bank account** field, select a bank account. If you leave this field blank, the report includes bank transaction details for all bank accounts.
4. Select **OK** to generate the report. 

## Calculate exchange rate adjustments for bank account transactions

> [!IMPORTANT]
> This section applies only to legal entities that have a primary address in the Czech Republic, Estonia, Lithuania, or Latvia.

You must revalue and adjust bank accounts if there is a difference in the exchange rate between the accounting currency and the reporting currency. This task helps you calculate the correct balance in both the accounting currency and the reporting currency for the bank accounts.

1. Select **Cash and bank management** &gt; **Setup** &gt; **Cash and bank management parameters**.
2. On the **Number sequences** tab, in the **Reference** field, select a number sequence for the **Bank - Exchange adjustment** reference.
3. Close the page.
4. Select **General ledger** &gt; **Setup** &gt; **Currency** &gt; **Currency exchange rates**. On the **Currency exchange rates** page, you can define the exchange rate between two currencies or a currency pair.
5. When you've finished, close the page.
6. Select **General ledger** &gt; **Setup** &gt; **Ledger**. In the **Unrealized gain** and **Unrealized loss** fields, select the main account that the exchange rates are posted for.
7. Close the page.
8. Select **Cash and bank management** &gt; **Periodic tasks** &gt; **Foreign currency revaluation**.
9. In the **On date** field, select the revaluation date or adjustment date.
10. In the **From currency** field, select the current currency code. In the **To currency** field, select the currency that the adjustment should be made to.
11. Select **Records to include** &gt; **Filter** to find the bank account, and then select **OK**.
12. On the **Foreign currency revaluation** page, select **OK**. The adjustment for the bank account transactions on the selected date is calculated.

> [!NOTE]
> In the general ledger, you can view two separate transactions: one for the accounting currency and one for the reporting currency.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]