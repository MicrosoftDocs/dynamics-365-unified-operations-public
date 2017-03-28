---
# required metadata

title: Adjustment inflation declaration report
description: Microsoft Dynamics 365 for Operations users can process inflation adjustments by using INPC rates, various methods (such as opening balance, balance, monthly balance, and transaction date), and various dimensions.
author: ShylaThompson
manager: AnnBe
ms.date: 2015-09-16 21 - 49 - 34
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

ms.search.form: InflationAdjJournal_MX, InpcRateTable_MX, LedgerParameters, MainAccount
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: ShylaThompson
ms.search.scope: AX 7.0.0, Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 9391
ms.assetid: 9076bf16-0021-47ad-a3b9-1bab75c583ec
ms.search.region: Mexico
# ms.search.industry: 
ms.author: sndray
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Adjustment inflation declaration report

Microsoft Dynamics 365 for Operations users can process inflation adjustments by using INPC rates, various methods (such as opening balance, balance, monthly balance, and transaction date), and various dimensions.

All companies in Mexico are required to apply the NIF B-10 process to inflation recognition in financial statements if the cumulative inflation rate during the last three years equals or exceeds 26 percent. By using the Índice Nacional de Precios al Consumidor (INPC) index rates every month, you can express the transaction values at the closing date of the general balance sheet. When the inflation adjustment process is run, the ledger balances are adjusted, and voucher entries are posted according to the INPC rates. Adjustment methods are defined, and you can view the effect of the inflation adjustment by generating simulation reports before you run the actual process.

## Prerequisites
The following table lists the configuration that must be in place before you start registration of inflationary effects in your general ledger.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Setup</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>INPC rates</td>
<td>Create or edit the INPC rate table to register the inflation rate per year and month to calculate the inflation adjustment amounts. You can change the amounts only when there is no adjustment inflation for the particular year and month, and when the status of the inflation adjustment process is open and reversed. This table is available on the government site (SAT).</td>
</tr>
<tr class="even">
<td>Inflation parameters</td>
<td>In the general ledger parameters, you must set up the main account where the result of monetary position is posted.
<ul>
<li><strong>REPOMO account for inflation correction:</strong> This is the main account that is used to post the adjustment inflation. Use this account to post the amount that is received for the Result on Exchange Rate Position (REPOMO) accounts. This account must always of the profit and loss, revenue, or expense type.</li>
<li><strong>Offset main account:</strong> The offset main account that is used for inflation adjustment transactions.</li>
<li><strong>Sequence numbers:</strong> You must specify a sequence number for <strong>Inflation adjustment vouchers</strong> and <strong>Inflation adjustment reversal voucher</strong>. These vouchers are used to generate the adjustment transactions and the reversal adjustment transactions when the inflation adjustment transactions are reversed.</li>
</ul></td>
</tr>
<tr class="odd">
<td>Main accounts</td>
<td>You must configure specific parameters per main account to enable the generation of adjustment inflation transactions.
<ul>
<li><strong>B-10 adjustment:</strong> Select <strong>Yes</strong> if you want to revaluate this account during the inflation adjustment process.</li>
<li><strong>REPOMO type:</strong> If this main account is part of REPOMO calculation, you must indicate the type: <strong>Asset</strong> or <strong>Liability</strong>. <strong>Not applicable</strong> is selected when the main account is not part of REPOMO calculation.</li>
<li><strong>Adjustment method:</strong> Select the adjustment method to use when the adjustment inflation process is run. Only the active ledger accounts are used when the adjustment inflation process is run.
<ul>
<li>None</li>
<li>Transaction date</li>
<li>Opening balance</li>
<li>Monthly balance</li>
<li>Balance</li>
</ul></li>
</ul></td>
</tr>
</tbody>
</table>

## Start the adjustment inflation process
To start the process, click **General ledger** &gt; **Period tasks** &gt; **Inflation adjustment B-10**. You can** **create the entry for a specific period, and include the from and to dates. The default status for this entry is **Open**. You also can include additional notes about the inflation adjustment process. There are various ways to run the process:

-   **Simulate** – Before you run the inflation adjustment process, you can run a simulation of the overall effects of running the inflation adjustment. If differences are found in the **Simulation** report, you can change only the **Posting layer** field and the **Notes** field on the **Inflation adjustment B-10** page. The simulation process does not post the inflation adjustment ledgers transactions. The process generates a report that shows the inflation adjustment ledger transactions that are generated by the system.
-   **Post**  – You can definitively post the adjustment inflation to generate the related adjustment inflation vouchers. You can also specify the posting layer where the transactions are generated. The adjustment inflation entry has a status of **Posted**.
-   **Reverse** – You can reverse inflation adjustment transactions that have been posted and run the process again if you must. After the reversal, the status of the adjustment inflation process is changed to **Reversed**.

## Available report types
Various types of adjustment inflation reports are available for control purposes when the adjustment inflation entry has a status of **Posted**.

### REPOMO report

This report is based on the following parameter values:

-   The **B-10 adjustment** slider is on for the main account.
-   The account type for the main account is **Asset**, **Liability**, or **Balance**.
-   The REPOMO type for the main account is **Asset** or **Liability**.
-   The adjustment type of the main account is **Opening** **balance**.

### Profit and loss report

This report shows the calculation of the profit and loss inflation adjustment for the selected period range. It shows the details of all main accounts that have the following parameter values:

-   The **B-10 adjustment** slider is on for the main account.
-   The account type for the main account is **Profit and loss**, **Revenue**, or **Expense**.
-   The adjustment type of the main account is **Monthly** **Balance**.

### Inventory report

This report shows the calculation of the inventory account code inflation adjustment for the selected period. It must shows all main accounts that have the following parameter values:

-   The **B-10 adjustment** slider is on for the main account.
-   The adjustment type of the main account is **Balance**.

### Capital and result report

This report shows the calculation of the capital and result account code inflation adjustment for the selected period. It must show all main accounts that have the following parameter values:

-   The **B-10 adjustment** slider is on for the main account.
-   The account type for the main account is **Balance** **sheet**, **Asset**, **Liability**, or **Equity**.
-   The adjustment type of the main account is **Transaction** **date**.


