---
# required metadata

title: Currency revaluation in a consolidation company
description: This article describes how to revalue currency in a consolidation company. 
author: aprilolson
ms.date: 10/02/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: LedgerExchAdjHist
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
ms.assetid: 2762baaf-0c10-4ff7-8713-c506d6c29b98
ms.search.region: Global
# ms.search.industry: 
ms.author: aolson
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Currency revaluation in a consolidation company

[!include [banner](../includes/banner.md)]

When you consolidate data from one accounting currency to another, you must still run currency revaluation if there is a change in exchange rates, so that your account balances  are correctly revalued. When you originally consolidate the data, use the **Currency translation** tab to select the initial exchange rates to for translation during the consolidation process. After a new exchange rate is entered (for example, in the next month), you must revalue the account balances. The unrealized gains or losses are then updated accordingly, based on the new exchange rate and date. The following example illustrates the accounting entries that are created during the process.

## Company setup
-   **Source/operating company (USMF)** – US dollars (USD) are used as the accounting and reporting currency.
-   **Consolidated company (CON)** – Euros (EUR) are used as the accounting and reporting currency.
    -   **Realized gain**– Ledger account 801500
    -   **Realized loss** – Ledger account 801600
    -   **Unrealized gain** – Ledger account 801600
    -   **Unrealized loss** – Ledger account 801400

## Original transactions
### Cash receipt transactions in USMF

| Date       | Ledger account               | Currency | Amount |
|------------|------------------------------|----------|--------|
| 10/11/2020 | 110110 – Cash                | USD      | 500    |
| 10/11/2020 | 130100 – Accounts Receivable | USD      | -500   |

## Exchange rates

| From currency | To currency | Start date | Exchange rate |
|---------------|-------------|------------|---------------|
| EUR           | USD         | 10/1/2020  | 200           |
| EUR           | USD         | 11/1/2020  | 150           |
| EUR           | USD         | 12/1/2017  | 100           |

## Perform the consolidation for October 2020
### Balances in the consolidation company

| Ledger account | Currency | Amount | Calculation    |
|----------------|----------|--------|----------------|
| 110110         | EUR      | 250    | 500 USD × 50%  |
| 130100         | EUR      | -250   | -500 USD × 50% |

## Perform currency revaluation for the accounts from October 1, 2020, through November 30, 2020
### Balances in the consolidation company

| Ledger account | Currency | Amount  | Calculation                        |
|----------------|----------|---------|------------------------------------|
| 110110         | EUR      | 333.33  | Original amount of 500 × 66.6667%  |
| 130100         | EUR      | -333.33 | Original amount of -500 × 66.6667% |
| 801400         | EUR      | 83.33   | 333.33 – 250                       |
| 801600         | EUR      | -83.33  | -333.33 – (-250)                   |

You will see additional transactions for the reporting currency amounts.

## Perform currency revaluation for the accounts from October 1, 2020, through December 31, 2020
### Balances in the consolidation company

| Ledger account | Currency | Amount  | Calculation                                          |
|----------------|----------|---------|------------------------------------------------------|
| 110110         | EUR      | 500.00  | Original amount of 500 × 1                           |
| 130100         | EUR      | -500.00 | Original amount of -500 × 1                          |
| 801400         | EUR      | 250     | 500 – 333.33 = 166.67 166.67 + 83.33 = 250           |
| 801600         | EUR      | -250    | -500 – (-333.33) = -166.67 -166.67 + (-83.33) = -250 |







[!INCLUDE[footer-include](../../includes/footer-banner.md)]
