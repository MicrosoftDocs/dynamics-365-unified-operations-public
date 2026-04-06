---
title: Calculate average and daily exchange rates
description: Learn how to calculate the average currency exchange rate for outgoing bank and cash transactions, including an overview on daily exchange rates.
author: AdamTrukawka
ms.author: atrukawk
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 03/19/2026
ms.reviewer: johnmichalak
ms.search.region: Hungary
ms.search.validFrom: 2016-11-30
ms.search.form: AssetParameters
---

# Calculate average and daily exchange rates

[!include [banner](../../includes/banner.md)]

According to the requirements for accounting foreign currencies under "Act C of 2000 on Accounting," the cost of foreign currency holdings comprises one of the following:

- The functional currency value calculated using the foreign currency rate at the time when you obtain the holdings.
- The functional currency value calculated using the average rate or the rate determined by the first in, first out (FIFO) method.

In legal entities that have Hungarian country/region context, you can calculate the average exchange rate for outgoing petty cash and bank transactions. When journal lines have outgoing petty cash or bank transactions, the calculation algorithm for the average exchange rate uses the summarized amounts of the accounting currency and the foreign currency before the specified transaction date.

This article explains how to use the function for calculating the average currency exchange rate for outgoing bank and cash transactions. It also explains how to use the function for calculating the daily exchange rate for incoming and outgoing bank and petty cash transactions.

## Daily exchange rate

You can use the function for calculating the daily exchange rate if you created ledger journal lines that have bank or petty cash transactions before you entered the daily currency exchange rates. The journal lines include the currency exchange rate that was valid on the previous date. Therefore, you need to recalculate them after you enter the new currency rate on the current date.

This example walks you through the function for calculating the daily exchange rate in the DEMF legal entity.

Before you begin, go to **Tax** > **Indirect tax** > **Sales tax** > **Sales tax settlement periods**. On the **Period intervals** tab, create intervals through March 31, 2020.

1. Go to **General ledger** > **Currencies** > **Currency exchange rates**, and select the line, **from USD to EUR**.
1. Select **Add**, and set the fields to the following values:

- **Start date:** 2/29/2020
- **Exchange rate:** 92

1. Select **Save**.
1. Go to **General ledger** \> **Journal entries** \> **General journals**, and select **New**.
1. In the **Name** field, select **GenJrn**.
1. Select **Lines**, and create the following lines.

| **Date**      | **Account type** | **Account** | **Debit** | **Credit** | **Offset account type** | **Offset account** | **Currency** | **Exchange rate** |
|---------------|------------------|-------------|-----------|------------|-------------------------|--------------------|--------------|-------------------|
| March 1, 2020 | Customer         | DE-010      |           | 100        | Bank                    | DEMF USD           | USD          | 92                |
| March 1, 2020 | Customer         | DE-011      |           | 200        | Bank                    | DEMF USD           | USD          | 92                |
| March 1, 2020 | Vendor           | DE-001      | 150       |            | Bank                    | DEMF USD           | USD          | 92                |
| March 1, 2020 | Vendor           | DE-01001    | 250       |            | Bank                    | DEMF USD           | USD          | 92                |

1. Select **Save**, and verify that the currency exchange rate value on the lines is **92**.
1. Go to **General ledger \> Currencies \> Currency exchange rates**, and select the line, **from USD to EUR**.
1. Select **Add**, and set the fields to the following values:

- **Start date:** 3/1/2020
- **Exchange rate:** 91

1. Select **Save**.
1. Go to **General ledger** \> **Journal entries** \> **General journals**.
1. Select the journal that you created earlier, and select **Lines**.
1. Select **Functions** \> **Exchange rate calculation**.
1. In the **Exchange rate calculation** dialog box, set the fields to the following values:

- **From date:** 3/1/2020
- **Calculation method:** Daily exchange rate

1. Select **OK**, and review the following data.

| **Date**      | **Account type** | **Account** | **Debit** | **Credit** | **Offset account type** | **Offset account** | **Currency** | **Exchange rate** |
|---------------|------------------|-------------|-----------|------------|-------------------------|--------------------|--------------|-------------------|
| March 1, 2020 | Customer         | DE-010      |           | 100        | Bank                    | DEMF USD           | USD          | 91                |
| March 1, 2020 | Customer         | DE-011      |           | 200        | Bank                    | DEMF USD           | USD          | 91                |
| March 1, 2020 | Vendor           | DE-001      | 150       |            | Bank                    | DEMF USD           | USD          | 91                |
| March 1, 2020 | Vendor           | DE-01001    | 250       |            | Bank                    | DEMF USD           | USD          | 91                |

Notice that the **Exchange rate** column is set to **91** for all rows.

## Average exchange rate

This example walks you through the function for calculating the average exchange rate for a bank account. Average rate is calculated for outgoing cash and bank transactions.

1. Go to **General ledger** > **Currencies** > **Currency exchange rates**, and select the line, **from USD to EUR**.
1. Select **Add**, and create the following lines.

| **Start date** | **Exchange rate** |
|----------------|-------------------|
| March 1, 2020  | 91                |
| March 2, 2020  | 92                |
| March 3, 2020  | 93                |

1. Go to **General ledger** > **Journal entries** > **General journals**, and select **New**.
1. In the **Name** field, select **GenJrn**.
1. Select **Lines**, and create the following lines that have incoming bank transactions.

| **Date**      | **Account type** | **Account** | **Debit** | **Credit** | **Offset account type** | **Offset account** | **Currency** | **Exchange rate** |
|---------------|------------------|-------------|-----------|------------|-------------------------|--------------------|--------------|-------------------|
| March 1, 2020 | Bank             | DEMF USD    | 100       |            | Customer                | DE-010             | USD          | 91.0000           |
| March 2, 2020 | Bank             | DEMF USD    | 200       |            | Customer                | DE-011             | USD          | 92.0000           |

1. Select **Post**.
1. Go to **General ledger** > **Journal entries** > **General journals**, and select **New**.
1. In the **Name** field, select **GenJrn**.
1. Select **Lines**, and create the following lines that have incoming and outgoing bank transactions.

| **Date**      | **Account type** | **Account** | **Debit** | **Credit** | **Offset account type** | **Offset account** | **Currency** | **Exchange rate** |
|---------------|------------------|-------------|-----------|------------|-------------------------|--------------------|--------------|-------------------|
| March 3, 2020 | Bank             | DEMF USD    | 100       |            | Customer                | DE-012             | USD          | 93.0000           |
| March 3, 2020 | Bank             | DEMF USD    |           | 150        | Vendor                  | DE-001             | USD          | 93.0000           |
| March 3, 2020 | Bank             | DEMF USD    |           | 250        | Vendor                  | DE-01001           | USD          | 93.0000           |

1. Verify that the currency exchange rate value that is automatically entered on the lines is **93**.
1. Select **Functions** \> **Exchange rate calculation**.
1. In the **Exchange rate calculation** dialog box, set the fields to the following values:

- **From date:** 3/1/2020
- **Calculation method:** Average exchange rate

1. Select **OK**, and verify that the currency exchange rate value for the outgoing bank transactions has been changed to **92**.

| **Date**      | **Account type** | **Account** | **Debit** | **Credit** | **Offset account type** | **Offset account** | **Currency** | **Exchange rate** |
|---------------|------------------|-------------|-----------|------------|-------------------------|--------------------|--------------|-------------------|
| March 3, 2020 | Bank             | DEMF USD    | 100       |            | Customer                | DE-012             | USD          | 93.0000           |
| March 3, 2020 | Bank             | DEMF USD    |           | 150        | Vendor                  | DE-001             | USD          | 92.0000           |
| March 3, 2020 | Bank             | DEMF USD    |           | 250        | Vendor                  | DE-01001           | USD          | 92.0000           |

The value **92.0000** for second line was calculated as (100 *0.91 + 200* 0.92 + 100 * 0.93)/(100 + 200 + 100). Three earlier incoming transactions for 100, 200, and 100 were considered in the calculation formula.

The value **92.0000** for third line was calculated as (100 *0.91 + 200* 0.92 + 100 *0.93 - 150* 0.92)/(100 + 200 + 100 - 150). Three earlier incoming transactions and one earlier outgoing transaction were considered in the formula.

The Average exchange rate calculation method is available for the outgoing bank transaction. It considers posted bank transactions and not-posted bank transactions in the current general journal that you created before considered outgoing bank transaction, for the period that starts on the "from date" that you specify in the dialog box and ends on the date of the outgoing bank transaction. This method calculates the average exchange rate for these transactions as a result of dividing total amount of all earlier transactions in the foreign currency by total amount of all earlier transactions in the accounting currency. The resulting exchange rate is then assigned to outgoing transaction. The average exchange rate is calculated by using dimension values for dimensions that are active in the account structure that the cash or bank ledger account belongs to.

   > [!NOTE]
   > To calculate the average exchange rates for cash and bank accounts based on the main account code only and not considering financial dimensions, enable the feature, **(Hungary) Calculate the average exchange rate based on the main account code only** in the **Feature management** workspace.

The Daily exchange rate and Average exchange rate methods are also available for the petty cash transactions that you enter in the slip journal (**Cash and bank management** > **Cash transactions** > **Slip journal**). The same algorithm that is used for the bank transactions is used to calculate the average rate.

[!INCLUDE [footer-include](../../../includes/footer-banner.md)]
