---
title: Revaluate foreign currency for advance holders (Russia)
description: Learn about foreign currency revaluation for advance holders in Russia in Microsoft Dynamics 365 Finance.
author: evgenypopov
ms.author: evgenypopov
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 08/08/2025
ms.reviewer: johnmichalak
ms.search.region: Russia
ms.search.validFrom: 2018-10-31
---

# Revaluate foreign currency for advance holders (Russia)

[!include [banner](../../includes/banner.md)]

This article provides information about foreign currency revaluation for advance holders in Russia.

When you settle advance payments and advance reports that include transactions that were completed in foreign currencies, adjustment transactions are created as a continuation of the advance report, based on the setup on the **Advance adjustment parameters** page.

> [!NOTE]
> For open advance transactions that are issued or received in foreign currencies, exchange adjustments no longer have to be calculated in business accounting.

## Set up advance adjustment parameters for advance holders

To set up advance adjustment parameters for advance holders, follow these steps.

1. In Dynamics 365 Finance, go to **General ledger** \> **Ledger setup** \> **Advance adjustment parameters**.
1. On the **Purchases/Advance holders** FastTab, in the **Ledger posting** field, select the type of ledger posting:

    - **Invoice accounts**: The advance adjustment that is produced by the settlement of an advance and an advance report for the advance holder should be a continuation of the advance report.
    - **Deviation from the cost price**: The calculation should be processed based on the account's settings for deviation, and the advance adjustment should not be a continuation of the advance report. Depending on the type of advance adjustment, specific ledger accounts are used to adjust the advance payments.

1. In the **Realized loss** field, select the ledger account to post an exchange rate loss for an employee to.
1. In the **Realized gain** field, select the ledger account to post an exchange rate profit for an employee to.

    > [!NOTE]
    > The realized loss and realized gain accounts are used to adjust advance payments only if the inventory is closed.

1. In the **Expense code** field, select a tax dimension expense code.
1. In the **Revenue code** field, select a tax dimension revenue code.
1. In the **Advance adjustment - loss** field, select the ledger account to post an advance adjustment loss in tax accounting to.
1. In the **Advance adjustment - profit** field, select the ledger account to post an advance adjustment profit in tax accounting to.
1. In the **Advance adjustment offset account** field, select the offset ledger account to post an advance adjustment in tax accounting to.
1. Select **Save**.

## Calculate the exchange rate adjustment for advance holders

To calculate the exchange rate adjustment for advance holders, follow these steps.

1. In Dynamics 365 Finance, go to ***Accounts payable** \> **Periodic tasks** \> **Advance holders** \> **Foreign currency revaluation**.
1. Select **Foreign currency revaluation** to open the **Foreign currency revaluation** dialog.
1. In the **Method** field, select **Standard**.
1. In the **Considered date** field, select the date that the general ledger transaction should be made by.
1. In the **Date of rate** field, select the date that determines the currency exchange rate that is used to compute the exchange rate adjustment. If you leave this field blank, the rate that is in effect on the date in the **Considered date** field is used.
1. In the **Description** field, enter the text that should appear in the exchange rate adjustment transaction.
1. In the **Use posting profile from** field, select one of the following values:

    - **Posting**: When a revaluation operation is done, the debt account for an advance holder is selected from the posting profile of the primary operation.
    - **Select**: When a revaluation operation is done, the debt account for an advance holder is selected from the posting profile that is selected in the **Posting profile** field.

    > [!NOTE]
    > The exchange rate adjustment is done for the account that is specified in the selected posting profile. The adjustment isn't done for the account that's specific in the primary operation.

1. The **Dimension** field determines how the dimension is generated in the exchange rate adjustment transaction. Select one of the following values:

    - **No**: The dimension is absent in the entry for the exchange rate adjustment forecast.
    - **Posting**: The dimension is inherited from the transactions for an advance holder.
    - **Table**: In the transaction for the exchange rate adjustment forecast, the dimension is inherited from the advance holder card, unless the dimension is designated for tax accounting.

1. On the **Records to include** FastTab, you can define additional filtering.
1. Select **OK** to calculate the exchange rates adjustment.

    After the calculation is completed, a new line for the exchange adjustment is generated on the **Foreign currency revaluation** page, based on the criteria that you specified. You can now perform the following actions:

    - Select **Voucher** to open the **Voucher transactions** page, where you can review the transactions that were completed for the general ledger.
    - Select **Transactions** to open the **Advance holder transactions** page, where you can review the transactions that were completed for the advance holder.
    - Select **Reviewed** to mark the selected line as reviewed.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
