---
# required metadata

title: Calculate average and daily exchange rates
description: This topic explains how to calculate the average currency exchange rate for outgoing bank and cash transactions.
author: v-lurodi
manager: AnnBe
ms.date: 05/07/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: AssetParameters
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 264684
ms.search.region: Hungary
# ms.search.industry: 
ms.author: epopov
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: 10.0.0

---

# Calculate average and daily exchange rates

[!include [banner](../includes/banner.md)]

According to the requirements for accounting foreign currencies under "Act C of 2000 on Accounting," the cost of foreign currency holdings comprises either the functional currency value that is calculated by using the foreign currency rate at the time when the holdings are obtained, or the functional currency value that is calculated by using either the average rate or the rate that is determined by the first in, first out (FIFO) method.

In legal entities that have Hungarian country context, the function for calculating the average exchange rate for outgoing petty cash and bank transactions is available. For journal lines that have outgoing petty cash or bank transactions, the calculation algorithm of the average exchange rate uses the summarized amounts of the accounting currency and the foreign currency before the specified transaction date.

This topic explains how to use the function for calculating the average currency exchange rate for outgoing bank and cash transactions. It also explains how to use the function for calculating the daily exchange rate for incoming and outgoing bank and petty cash transactions.

## Daily exchange rate

You can use the function for calculating the daily exchange rate if you created ledger journal lines that have bank or petty cash transactions before you entered the daily currency exchange rates. The journal lines will have the currency exchange rate that was valid on the previous date. Therefore, they must be recalculated after the new currency rate on the current date is entered.

This example walks you through the function for calculating the daily exchange rate in the DEMF legal entity.

Before you begin, go to **Tax** \> **Indirect tax** \> **Sales tax** \> **Sales tax settlement periods**. On the **Period intervals** tab, create intervals through March 31, 2020.

1. Go to **General ledger** \> **Currencies** \> **Currency exchange rates**, and select the **from USD to EUR** line.
2. Select **Add**, and set the fields to the following values:

- **Start date:** 2/29/2020
- **Exchange rate:** 92

3. Select **Save**.
4. Go to **General ledger** \> **Journal entries** \> **General journals**, and select **New**.
5. In the **Name** field, select **GenJrn**.
6. Select **Lines**, and create the following lines.

| **Date**      | **Account type** | **Account** | **Debit** | **Credit** | **Offset account type** | **Offset account** | **Currency** | **Exchange rate** |
|---------------|------------------|-------------|-----------|------------|-------------------------|--------------------|--------------|-------------------|
| March 1, 2020 | Customer         | DE-010      |           | 100        | Bank                    | DEMF USD           | USD          | 92                |
| March 1, 2020 | Customer         | DE-011      |           | 200        | Bank                    | DEMF USD           | USD          | 92                |
| March 1, 2020 | Vendor           | DE-001      | 150       |            | Bank                    | DEMF USD           | USD          | 92                |
| March 1, 2020 | Vendor           | DE-01001    | 250       |            | Bank                    | DEMF USD           | USD          | 92                |

7. Select **Save**, and verify that the currency exchange rate value on the lines is **92**.
8. Go to **General ledger \> Currencies \> Currency exchange rates**, and elect the **from USD to EUR** line.
9. Select **Add**, and set the fields to the following values:

- **Start date:** 3/1/2020
- **Exchange rate:** 91

10. Select **Save**.
11. Go to **General ledger** \> **Journal entries** \> **General journals**.
12. Select the journal that you created earlier, and select **Lines**.
13. Select **Functions** \> **Exchange rate calculation**.
14.  In the **Exchange rate calculation** dialog box, set the fields to the ollowing values:

- **From date:** 3/1/2020
- **Calculation method:** Daily exchange rate

15. Select **OK**, and review the following data.

| **Date**      | **Account type** | **Account** | **Debit** | **Credit** | **Offset account type** | **Offset account** | **Currency** | **Exchange rate** |
|---------------|------------------|-------------|-----------|------------|-------------------------|--------------------|--------------|-------------------|
| March 1, 2020 | Customer         | DE-010      |           | 100        | Bank                    | DEMF USD           | USD          | 91                |
| March 1, 2020 | Customer         | DE-011      |           | 200        | Bank                    | DEMF USD           | USD          | 91                |
| March 1, 2020 | Vendor           | DE-001      | 150       |            | Bank                    | DEMF USD           | USD          | 91                |
| March 1, 2020 | Vendor           | DE-01001    | 250       |            | Bank                    | DEMF USD           | USD          | 91                |

Notice that the **Exchange rate** column is set to **91** for all rows.

## Average exchange rate

This example walks you through the function for calculating the average exchange rate for a bank account.

1. Go to **General ledger** \> **Currencies** \> **Currency exchange rates**, and select the **from USD to EUR** line.
2. Select **Add**, and create the following lines.

| **Start date** | **Exchange rate** |
|----------------|-------------------|
| March 1, 2020  | 91                |
| March 2, 2020  | 92                |
| March 3, 2020  | 93                |

3. Go to **General ledger \> Journal entries \> General journals**, and select **New**.
4. In the **Name** field, select **GenJrn**.
5. Select **Lines**, and create the following lines that have incoming bank transactions.

| **Date**      | **Account type** | **Account** | **Debit** | **Credit** | **Offset account type** | **Offset account** | **Currency** | **Exchange rate** |
|---------------|------------------|-------------|-----------|------------|-------------------------|--------------------|--------------|-------------------|
| March 1, 2020 | Bank             | DEMF USD    | 100       |            | Customer                | DE-010             | USD          | 91                |
| March 2, 2020 | Bank             | DEMF USD    | 200       |            | Customer                | DE-011             | USD          | 92                |

6. Select **Post**.
7. Go to **General ledger** \> **Journal entries** \> **General journals**, and select **New**.
8. In the **Name** field, select **GenJrn**.
9. Select **Lines**, and create the following lines that have incoming and outgoing bank transactions.

| **Date**      | **Account type** | **Account** | **Debit** | **Credit** | **Offset account type** | **Offset account** | **Currency** | **Exchange rate** |
|---------------|------------------|-------------|-----------|------------|-------------------------|--------------------|--------------|-------------------|
| March 3, 2020 | Bank             | DEMF USD    | 110       |            | Customer                | DE-012             | USD          | 93                |
| March 3, 2020 | Bank             | DEMF USD    |           | 150        | Vendor                  | DE-001             | USD          | 93                |
| March 3, 2020 | Bank             | DEMF USD    |           | 250        | Vendor                  | DE-01001           | USD          | 93                |

10. Verify that the currency exchange rate value that is automatically entered on the lines is **93**.
11. Select **Functions** \> **Exchange rate calculation**.
12. In the **Exchange rate calculation** dialog box, set the fields to the following values:

- **From date:** 3/1/2020
- **Calculation method:** Average exchange rate

13. Select **OK**, and verify that the currency exchange rate value for the outgoing bank transactions has been changed to **92**.

| **Date**      | **Account type** | **Account** | **Debit** | **Credit** | **Offset account type** | **Offset account** | **Currency** | **Exchange rate** |
|---------------|------------------|-------------|-----------|------------|-------------------------|--------------------|--------------|-------------------|
| March 3, 2020 | Bank             | DEMF USD    | 110       |            | Customer                | DE-012             | USD          | 93                |
| March 3, 2020 | Bank             | DEMF USD    |           | 150        | Vendor                  | DE-001             | USD          | 92                |
| March 3, 2020 | Bank             | DEMF USD    |           | 250        | Vendor                  | DE-01001           | USD          | 92                |

The value **92** was calculated as (91 + 92 + 93) ÷ 3, where 91 is the exchange rate for the incoming posted bank transaction on March 1, 2020, 92 is the exchange rate for the incoming posted bank transaction on March 2, 2020, and 93 is the exchange rate for the incoming not-posted bank transaction on March 3, 2020 in the same journal.

The Average exchange rate calculation method is available for the outgoing bank transaction. It considers incoming bank transactions (both posted and not-posted transactions in the current general journal) for the period that starts on the "from date" that is specified in the dialog box and ends on the date of the outgoing bank transaction. This method calculates the average exchange rate for these transactions by using the arithmetic mean formula. The resulting exchange rate is then assigned to outgoing transactions.

The Daily exchange rate and Average exchange rate methods are also available for the petty cash transactions that you enter in the slip journal (**Cash and bank management** \> **Cash transactions** \> **Slip journal**). The same algorithm that is used for the bank transactions is used to calculate the average rate.
