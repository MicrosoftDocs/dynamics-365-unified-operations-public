---
title: Foreign currency revaluation using FIFO/LIFO for bank accounts
description: Learn how to run foreign currency revaluation for Czech Republic, Estonia, Latvia, Lithuania, Poland, and Hungary.
author: mukumarm
ms.author: mukumarm
ms.topic: how-to
ms.date: 07/15/2026
ms.reviewer: johnmichalak
ms.search.region: Czech Republic, Estonia, Latvia, Lithuania, Poland, Hungary
ms.search.validFrom: 2016-02-28
ms.custom: 
  - bap-template
---

# Foreign currency revaluation for bank accounts

[!INCLUDE [banner](../../includes/banner.md)]

## Revalue foreign currency amounts for bank account transactions

> [!IMPORTANT]
> This section applies only to legal entities that have a primary address in the Czech Republic, Estonia, Lithuania, or Latvia.

The Bank - Exchange adjustment (FIFO/LIFO) feature calculates exchange gains and losses on bank transactions by matching withdrawals against deposits using either the First In, First Out (FIFO) or Last In, First Out (LIFO) valuation method. The feature is intended for localization scenarios where statutory regulations require exchange adjustments to be calculated based on the originating bank transaction layers rather than on the total bank balance. You can then create a report to view the bank transactions that have adjustments for foreign currency revaluations.

The feature supports the following business requirements:

- Calculates exchange gains or losses for bank transactions by using FIFO or LIFO matching logic.
- Matches outgoing bank transactions against available incoming transaction layers.
- Calculates the exchange adjustment amount based on the difference between the exchange rate of the original incoming transaction and the exchange rate of the outgoing transaction.
- Posts exchange adjustment vouchers that you can review from bank transactions and the Bank - Exchange adjustment report.
- Provides an auditable view of how exchange adjustment amounts are calculated for bank transactions.

### Cash and Bank management parameters

To configure exchange rate type FIFO or LIFO for bank foreign currency revaluation, follow these steps:

1. Go to **Cash and bank management** > **Setup** > **Cash and Bank management parameters**.
1. On the **General** tab, select the required **Exchange difference type**.
   - Select **FIFO** to match withdrawals against the oldest available deposits.
   - Select **LIFO** to match withdrawals against the latest available deposits.
1. In the **Number sequence** tab, select the **Bank - Exchange adjustment (FIFO/LIFO)** number sequence.

### Bank foreign currency revaluation

To execute foreign currency revaluation for banks, follow these steps:

1. Go to **Cash and bank management** > **Periodic tasks** > **Bank - Exchange adjustment (FIFO/LIFO)**.
1. In the **On date** field, enter an end date for the revaluation. The calculation includes only transactions that have a date that is before the specified date.
1. Go to **Records to include** > **Filter** > **Add** to add a bank account. If you don't specify a bank account, the system revalues amounts for all bank accounts.
1. On the **Foreign currency revaluation** page, select the **Recalculation** checkbox to revalue foreign currency amounts for all open periods.
1. Select **OK** to close the query page.

## Create a report to view bank transactions that have adjustments for foreign currency revaluations

> [!IMPORTANT]
> This section applies only to legal entities that have a primary address in Poland and Hungary.

1. Go to **Cash and bank management** > **Inquiries and reports** > **Bank - Exchange adjustment report**.
1. Select **Records to include** > **Filter** to find one or more bank accounts to view information for.
1. (Optional) In the **Bank account** field, select a bank account. If you leave this field blank, the report includes bank transaction details for all bank accounts.
1. Select **OK** to generate the report.

## Example scenario

A company uses a bank account where:

- Bank transaction currency is **PLN**.
- Accounting currency is **EUR**.
- Exchange difference type is **FIFO**.

The following bank transactions are posted.

| Date | Transaction | Amount in transaction currency (PLN) | Accounting amount (EUR) | Exchange rate |
|---|---:|---:|---:|---:|
| 01-Jul-2026 | Deposit | 1,000.00 | 4,500.00 | 4.5 |
| 05-Jul-2026 | Deposit | 500.00 | 2,300.00 | 4.6 |
| 10-Jul-2026 | Withdrawal | -800.00 | -3,680.00 | 4.6 |

### FIFO calculation for the first withdrawal

The withdrawal of **800 PLN** on **10-Jul-2026** is matched against the oldest available deposit, which is the deposit from **01-Jul-2026**.

| FIFO source layer | Available amount (PLN) | Consumed amount (PLN) | Remaining amount (PLN) | Original exchange rate |
|---|---:|---:|---:|---:|
| 01-Jul-2026 deposit | 1,000.00 | 800.00 | 200.00 | 4.5 |

The withdrawal is posted at an exchange rate of **4.6**.

The exchange adjustment is calculated as follows:

```text
Exchange adjustment = Consumed amount x (withdrawal exchange rate - original deposit exchange rate)
Exchange adjustment = 800 x (4.6 - 4.5)
Exchange adjustment = 800 x 0.1
Exchange adjustment = 80 EUR
```

Therefore, the process posts an exchange adjustment amount of **80 EUR**.

### FIFO layers after the first withdrawal

After the first withdrawal is matched, the remaining FIFO layers are as follows.

| FIFO source layer | Remaining amount (PLN) | Original exchange rate |
|---|---:|---:|
| 01-Jul-2026 deposit | 200.00 | 4.5 |
| 05-Jul-2026 deposit | 500.00 | 4.6 |

The remaining bank balance is **700 PLN**.

### Second withdrawal example

A second withdrawal is posted.

| Date | Transaction | Amount in transaction currency (PLN) | Accounting amount (EUR) | Exchange rate |
|---|---:|---:|---:|---:|
| 15-Jul-2026 | Withdrawal | -300.00 | -1,410.00 | 4.7 |

Under FIFO, the withdrawal of **300 PLN** is matched as follows:

1. Consume the remaining **200 PLN** from the 01-Jul-2026 deposit layer at rate **4.5**.
1. Consume **100 PLN** from the 05-Jul-2026 deposit layer at rate **4.6**.

| FIFO source layer | Consumed amount (PLN) | Original exchange rate | Withdrawal exchange rate | Exchange adjustment |
|---|---:|---:|---:|---:|
| 01-Jul-2026 deposit | 200.00 | 4.5 | 4.7 | 40.00 EUR |
| 05-Jul-2026 deposit | 100.00 | 4.6 | 4.7 | 10.00 EUR |
| **Total** | **300.00** |  |  | **50.00 EUR** |

The calculation is:

```text
Layer 1 adjustment = 200 x (4.7 - 4.5) = 40 EUR
Layer 2 adjustment = 100 x (4.7 - 4.6) = 10 EUR
Total adjustment = 40 + 10 = 50 EUR
```

Therefore, the process posts an exchange adjustment amount of **50 EUR**.

### Result summary

| Transaction | Calculation | Exchange adjustment amount |
|---|---|---:|
| First withdrawal: 800 PLN at 4.6 | 800 x (4.6 - 4.5) | 80.00 EUR |
| Second withdrawal: 300 PLN at 4.7 | 200 x (4.7 - 4.5) + 100 x (4.7 - 4.6) | 50.00 EUR |
| **Total realized exchange adjustment** |  | **130.00 EUR** |

### Remaining FIFO layer

After both withdrawals, the remaining open layer is from the 05-Jul-2026 deposit.

```text
Original deposits = 1,000 PLN + 500 PLN = 1,500 PLN
Withdrawals = 800 PLN + 300 PLN = 1,100 PLN
Remaining bank balance = 400 PLN
```

| FIFO source layer | Remaining amount (PLN) | Original exchange rate |
|---|---:|---:|
| 05-Jul-2026 deposit | 400.00 | 4.6 |

> [!NOTE]
> In the general ledger, you can view two separate transactions: one for the accounting currency and one for the reporting currency.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
