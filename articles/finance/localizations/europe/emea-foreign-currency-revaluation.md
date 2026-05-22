---
title: Foreign currency revaluation for bank accounts
description: Learn about the process of creating a report to view bank transactions with adjustments for foreign currency revaluations.
author: panolte
ms.author: johnmichalak
ms.topic: how-to
ms.date: 03/06/2026
ms.reviewer: johnmichalak
ms.search.region: Czech Republic, Estonia, Latvia, Lithuania, Poland
ms.search.validFrom: 2016-02-28
ms.custom: 
  - bap-template
---

# Foreign currency revaluation for bank accounts

[!include [banner](../../includes/banner.md)]

## Revalue foreign currency amounts for bank account transactions

> [!IMPORTANT]
> This section applies only to legal entities that have a primary address in Poland.

You can revalue foreign currency amounts for bank transactions. You can then create a report to view the bank transactions that have adjustments for foreign currency revaluations.

1. Select **Cash and bank management** > **Periodic tasks** > **Bank - Exchange adjustment (FIFO/LIFO)**.
1. In the **On date** field, enter an end date for the revaluation. The calculation includes only transactions that have a date that is before the specified date.
1. Select **Records to include** > **Filter** > **Add** to add a bank account. If you don't specify a bank account, the system revalues amounts for all bank accounts.
1. Select **OK** to close the query page.
1. On the **Foreign currency revaluation** page, select the **Recalculation** check box to revalue foreign currency amounts for all open periods.

## Create a report to view bank transactions that have adjustments for foreign currency revaluations

> [!IMPORTANT]
> This section applies only to legal entities that have a primary address in Poland.

1. Select **Cash and bank management** > **Inquiries and reports** > **Bank - Exchange adjustment report**.
1. Select **Records to include** > **Filter** to find one or more bank accounts to view information for.
1. (Optional) In the **Bank account** field, select a bank account. If you leave this field blank, the report includes bank transaction details for all bank accounts.
1. Select **OK** to generate the report. 

## Calculate exchange rate adjustments for bank account transactions

> [!IMPORTANT]
> This section applies only to legal entities that have a primary address in the Czech Republic, Estonia, Lithuania, or Latvia.

You must revalue and adjust bank accounts if there's a difference in the exchange rate between the accounting currency and the reporting currency. This task helps you calculate the correct balance in both the accounting currency and the reporting currency for the bank accounts.

1. Select **Cash and bank management** > **Setup** > **Cash and bank management parameters**.
1. On the **Number sequences** tab, in the **Reference** field, select a number sequence for the **Bank - Exchange adjustment** reference.
1. Close the page.
1. Select **General ledger** > **Setup** > **Currency** > **Currency exchange rates**. On the **Currency exchange rates** page, define the exchange rate between two currencies or a currency pair.
1. When you finish, close the page.
1. Select **General ledger** > **Setup** > **Ledger**. In the **Unrealized gain** and **Unrealized loss** fields, select the main account that the exchange rates post to.
1. Close the page.
1. Select **Cash and bank management** > **Periodic tasks** > **Foreign currency revaluation**.
1. In the **On date** field, select the revaluation date or adjustment date.
1. In the **From currency** field, select the current currency code. In the **To currency** field, select the currency that you want to adjust to.
1. Select **Records to include** > **Filter** to find the bank account, and then select **OK**.
1. On the **Foreign currency revaluation** page, select **OK**. The adjustment for the bank account transactions on the selected date is calculated.

> [!NOTE]
> In the general ledger, you can view two separate transactions: one for the accounting currency and one for the reporting currency.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]