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

When you settle advance payments and advance reports that contain transactions made in foreign currencies, the adjustment transactions are created as a continuation of the advance report, based on the setup made in the **General ledger parameters** and the **Advance adjustment parameters**. 
The advance adjustment transactions are displayed in the **Advance holder transactions** form. The amounts on the advance report are based on the exchange rate on the advance payment date, not on the posting date.

  > [!NOTE]
    > The calculation of exchange adjustments on advance payments that are issued or received in foreign currencies is no longer required in business accounting.

Complete the following tasks before you settle advances that are issued to an advance holder:

1.  Set up an advance holder. 

2.  Set up general ledger parameters for exchange adjustment.

Use the following procedure to set up advance adjustment parameters for advance holders.

1.  Click **General ledger** \> **Setup** \> **Advance adjustment parameters**.

2.  Click **Purchases/Advance holders**.

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
