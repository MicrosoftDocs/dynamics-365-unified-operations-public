---
# required metadata

title: Set up advance adjustment parameters for advance holders
description: 
author: 
manager: AnnBe
ms.date: 09/07/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: shylaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Russia
# ms.search.industry: 
ms.author: 
ms.dyn365.ops.version: 8.1
ms.search.validFrom: 2018-10-31

---

# Foreign currency revaluation for advance holders in Russia

[!include [banner](../includes/banner.md)]

This topic provides information about foreign currency revaluation procedure for advance holders in Russia.

When you settle advance payments and advance reports that contain transactions made in foreign currencies, the adjustment transactions are created as a continuation of the advance report, based on the setup made in the **Advance adjustment parameters**. 

  > [!NOTE]
    > The calculation of exchange adjustments of open advance transactions that are issued or received in foreign currencies is no longer required in business accounting.

Use the following procedure to set up advance adjustment parameters for advance holders.

1.  Go to **General ledger** \> **Ledger setup** \> **Advance adjustment parameters**.

2.  Go to **Purchases/Advance holders** FastTab.

3.  In the **Ledger posting** field, select the type of ledger posting from the following options:
    
      - **Invoice accounts** – Confirm that the advance adjustment that results from the settlement of an advance and an advance report for the advance holder is a continuation of the advance report.
    
      - **Deviation from the cost price** – Confirm that the calculation should be processed according to the settings of the account for deviation, and that the advance adjustment is not a continuation of the advance report. Depending on the advance adjustment type, specific ledger accounts are used for the adjustment of the advance payments.

4.  In the **Realized loss** field, select the ledger account to post an exchange rate loss for an employee to.

5.  In the **Realized gain** field, select the ledger account to post an exchange rate profit for an employee to.
    
    > [!NOTE]
    > The realized loss and realized profit accounts are used for the adjustment of advance payments only if the inventory is closed.

6.  In the **Expense code** field, select a tax dimension expense code.

7.  In the **Revenue code** field, select a tax dimension revenue code.

8.  In the **Advance adjustment - loss** field, select the ledger account to post an advance adjustment loss in tax accounting to.

9.  In the **Advance adjustment - profit** field, select the ledger account to post an advance adjustment profit in tax accounting to.

10. In the **Advance adjustment offset account** field, select the offset ledger account to post an advance adjustment in tax accounting to.

11. Click **Save** button.

To compute the exchange rates adjustment for advance holders, perform the following actions:

1.  Go to **Accounts payable** \> **Periodic tasks** \> **Advance holders** \> **Foreign currency revaluation**.

2.  Click **Foreign currency revaluation** button to open **Foreign currency revaluation** form.

3.  In the **Method** field, select the value **Standard**.

4.  In the **Considered date** field, select the date by which the general ledger transaction should be made.

5.  In the **Date of rate** field, select the date that determines the currency exchange rate for computing the exchange rate adjustment. If the field is not populated, the rate in the **Considered date** will be used.

6.  In the **Description** field, enter the text that should be displayed in the exchange rate adjustment transaction.

7.  In the **Use posting profile from** field, select the value:
    
      - **Posting** – When performing a revaluation operation, the debt account for an advance holder will be selected from the posting profile of the primary operation.
    
      - **Select** – When performing a revaluation operation, the debt account for an advance holder will be selected from the posting profile indicated in the **Posting profile** field.
       > [!NOTE]
    > The exchange rate adjustment will be made for the account indicated in the selected posting profile, and not for the account in the primary operation.

8.  The value in the **Dimension** field determines how the dimension is generated in the transaction for exchange rate adjustment.

     - **No** – Dimension is absent in the entry for exchange rate adjustment forecast.

     - **Posting** – Dimension is inherited from the transactions for an advance holder.

     - **Table** – In the transaction for exchange rate adjustment forecast, dimension is inherited from the advance holder card, except for the dimension designated for tax accounting.

9.  You can define additional filtering in  **Records to include** FastTab.

10. Click **OK** button to compute the exchange rates adjustment.

As a result, in the **Foreign currency revaluation** form, a new line will be generated for the exchange adjustment according to the specified criteria. You can perform the following actions:

1.  Click the **Voucher** button to open the voucher transactions form to review the transactions completed for the general ledger.

2.  Click the **Transactions** button to open the Advance holder transactions form to review the transactions completed for the advance holder.

3.  Click the **Reviewed** button to mark the selected line as reviewed.
