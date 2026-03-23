---
title: Adjustment inflation declaration report
description: Microsoft Dynamics 365 Finance users can process inflation adjustments by using INPC rates, various methods (such as opening balance), and various dimensions.
author: AdamTrukawka
ms.author: atrukawk
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 03/20/2026
ms.reviewer: johnmichalak
ms.search.region: Mexico
ms.search.validFrom: 2016-02-28
ms.search.form: InflationAdjJournal_MX, InpcRateTable_MX, LedgerParameters, MainAccount
ms.assetid: 9076bf16-0021-47ad-a3b9-1bab75c583ec
---

# Adjustment inflation declaration report

[!include [banner](../../includes/banner.md)]

You can process inflation adjustments by using INPC rates, various methods (such as opening balance, balance, monthly balance, and transaction date), and various dimensions.

All companies in Mexico are required to apply the NIF B-10 process to inflation recognition in financial statements if the cumulative inflation rate during the last three years equals or exceeds 26 percent. By using the Índice Nacional de Precios al Consumidor (INPC) index rates every month, you can express the transaction values at the closing date of the general balance sheet. When you run the inflation adjustment process, the system adjusts the ledger balances and posts voucher entries according to the INPC rates. You define adjustment methods, and you can view the effect of the inflation adjustment by generating simulation reports before you run the actual process.

## Prerequisites

The following table lists the configuration that must be in place before you start registration of inflationary effects in your general ledger.

| Setup | Description |
|---|---|
| INPC rates | Create or edit the INPC rate table to register the inflation rate per year and month to calculate the inflation adjustment amounts. You can change the amounts only when there's no adjustment inflation for the particular year and month, and when the status of the inflation adjustment process is open and reversed. This table is available on the government site (SAT). |
| Inflation parameters | In the general ledger parameters, set up the main account where you post the result of monetary position. **REPOMO account for inflation correction:** This account posts the adjustment inflation. Use this account to post the amount that is received for the Result on Exchange Rate Position (REPOMO) accounts. This account must always be of the profit and loss, revenue, or expense type. **Offset main account:** Use this account for inflation adjustment transactions. **Sequence numbers:** Specify a sequence number for **Inflation adjustment vouchers** and **Inflation adjustment reversal voucher**. These vouchers generate the adjustment transactions and the reversal adjustment transactions when you reverse the inflation adjustment transactions. |
| Main accounts | Configure specific parameters per main account to enable the generation of adjustment inflation transactions. **B-10 adjustment:** Select **Yes** if you want to revaluate this account during the inflation adjustment process. **REPOMO type:** If this main account is part of REPOMO calculation, indicate the type: **Asset** or **Liability**. Select **Not applicable** when the main account isn't part of REPOMO calculation. **Adjustment method:** Select the adjustment method to use when you run the adjustment inflation process. Only the active ledger accounts are used when you run the adjustment inflation process. None; Transaction date; Opening balance; Monthly balance; Balance |

## Start the adjustment inflation process

To start the process, select **General ledger** > **Period tasks** > **Inflation adjustment B-10**. You can create the entry for a specific period, and include the from and to dates. The default status for this entry is **Open**. You can also include additional notes about the inflation adjustment process. There are various ways to run the process:

- **Simulate** – Before you run the inflation adjustment process, run a simulation of the overall effects of running the inflation adjustment. If differences are found in the **Simulation** report, you can change only the **Posting layer** field and the **Notes** field on the **Inflation adjustment B-10** page. The simulation process doesn't post the inflation adjustment ledgers transactions. The process generates a report that shows the inflation adjustment ledger transactions that the system generates.
- **Post**  – You can definitively post the adjustment inflation to generate the related adjustment inflation vouchers. You can also specify the posting layer where the transactions are generated. The adjustment inflation entry has a status of **Posted**.
- **Reverse** – You can reverse inflation adjustment transactions that you already posted and run the process again if you must. After the reversal, the status of the adjustment inflation process changes to **Reversed**.

## Available report types

Various types of adjustment inflation reports are available for control purposes when the adjustment inflation entry has a status of **Posted**.

### REPOMO report

This report is based on the following parameter values:

- The **B-10 adjustment** slider is on for the main account.
- The account type for the main account is **Asset**, **Liability**, or **Balance**.
- The REPOMO type for the main account is **Asset** or **Liability**.
- The adjustment type of the main account is **Opening** **balance**.

### Profit and loss report

This report shows the calculation of the profit and loss inflation adjustment for the selected period range. It shows the details of all main accounts that have the following parameter values:

- The **B-10 adjustment** slider is on for the main account.
- The account type for the main account is **Profit and loss**, **Revenue**, or **Expense**.
- The adjustment type of the main account is **Monthly** **Balance**.

### Inventory report

This report shows the calculation of the inventory account code inflation adjustment for the selected period. It shows all main accounts that have the following parameter values:

- The **B-10 adjustment** slider is on for the main account.
- The adjustment type of the main account is **Balance**.

### Capital and result report

This report shows the calculation of the capital and result account code inflation adjustment for the selected period. It shows all main accounts that have the following parameter values:

- The **B-10 adjustment** slider is on for the main account.
- The account type for the main account is **Balance** **sheet**, **Asset**, **Liability**, or **Equity**.
- The adjustment type of the main account is **Transaction** **date**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
