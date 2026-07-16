---
title: Automatic settlement and prioritization
description: Learn about how transactions are settled if you select Automatic settlement on the Accounts receivable or Accounts payable parameters pages.
author: mukumarm
ms.author: mukumarm
ms.topic: article
ms.date: 07/08/2026
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.search.form: CustOpenTrans, CustParameters, LedgerJournalTransCustPaym, VendParameters
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: e7837cf6-ec69-44b4-8d47-eba38d5c7b1f
---

# Automatic settlement and prioritization

[!include [banner](../includes/banner.md)]

This article describes how transactions are settled if you select **Automatic settlement** on the **Accounts receivable parameters** or **Accounts payable parameters** pages. It also explains how automatic settlement can be used together with settlement priority.

You have two options when you settle payments with invoices and other transactions. You can manually select the transactions to settle, or the system can automatically select transactions by using automatic settlement. You can also customize how automatic settlement is processed by using the **Use priority for automatic settlements** option. These options are part of the settlement parameters that you define on the **Accounts receivable parameters** or **Accounts payable parameters** pages.

Automatic settlement can be processed by using one of the following methods:

- User-defined settlement priority
- Default automatic settlement

The following sections describe how transactions are settled for each method.

## Example transactions

The examples of settlements later in this article are based on the following transactions. All transactions are for customer 2050.

| Transaction   | Date        | Amount | Cash discount terms | Cash discount date | Comments                                  |
|---------------|-------------|--------|---------------------|--------------------|--------------------|
| Invoice 1     | August 15   | 100.00 | 2%14, Net 30  | August 29          |                                             |
| Invoice 2     | September 1 | 250.00 | 2%14, Net 30        | September 15       |                                        |
| Invoice 3     | October 15  | 500.00 | 2% 14/Net 30        | October 29         |                                       |
| Interest note | October 15  | 7.00   |     |          | This interest note is for invoice 1 and invoice 2. The amount is calculated as 2-percent interest on amounts that are 30 or more days past due. For example, 0.02 × (100.00 + 250.00) = 7.00. |

## Default automatic settlement

If you don't specify a settlement priority, the system automatically selects transactions for settlement based on the due date. The transactions you settle must have the same currency as the transaction that they're settled with. If you post a payment for 700.00 on October 25, the system selects the following transactions for settlement.

| Voucher       | Date       | Invoice | Amount in transaction currency | Amount to settle | Balance | Currency |
|---------------|------------|---------|--------------------------------|------------------|---------|----------|
| Invoice 1     | 8/15/2015  | 10001   | 100.00                         | 100.00           | 0.00    | USD      |
| Invoice 2     | 9/1/2015   | 10002   | 250.00                         | 250.00           | 0.00    | USD      |
| Invoice 3     | 10/15/2015 |         | 500.00                         | 350.00           | 150.00  | USD      |
| Interest note | 10/15/2015 |         | 7.00                           | 0.00             | 7.00    | USD      |

## Configure settlement priority for automatic settlements

Dynamics 365 Finance can automatically determine which customer or vendor transactions to settle when a payment doesn't explicitly identify the transactions to settle. Settlement priority lets organizations define business-specific rules that determine the order in which open transactions are selected during automatic settlement.

Use settlement priority to help support scenarios such as:

- Prioritizing transaction types, such as payment fees, collection letters, interest notes, and invoices.
- Settling transactions based on due date, cash discount date, transaction date, transaction amount, or voucher.
- Applying payments consistently when the payment amount doesn't cover all open transactions.
- Supporting cash discount handling and overpayment scenarios during automatic settlement.

---

### Prerequisites

Before you can use settlement priority, turn on automatic settlement.

1. Go to **Accounts receivable > Setup > Accounts receivable parameters**.
1. Open the **Settlement** tab.
1. Set **Automatic settlement** to **Yes**.
1. Set **Use priority for automatic settlements** to **Yes**.
1. Select **Manage priority** to define the settlement priority rules.

---

### Configure settlement priority attributes

On the **Settlement priority** page, you define the order in which transaction attributes are evaluated when the system automatically selects transactions for settlement. Select the attributes that you want to include in the priority sequence, and then use **Up** and **Down** to arrange the attributes in the order you want.

Use the following attributes in the priority sequence.

| Attribute | Description |
|---|---|
| **Transaction type** | Prioritizes transactions by transaction category, such as payment fees, collection letters, interest notes, and invoices. |
| **Due date** | Prioritizes transactions according to the transaction due date. |
| **Cash discount date** | Prioritizes transactions according to the cash discount date. This attribute is useful when payments should be applied first to transactions where the cash discount date is approaching. |
| **Transaction date** | Prioritizes transactions according to the original transaction date. |
| **Transaction amount** | Prioritizes transactions according to the transaction amount. |
| **Voucher** | Prioritizes transactions according to voucher number. Use it as a tie-breaker when other attributes have the same value. |

The system evaluates active priority attributes from top to bottom. If a higher-priority attribute determines which transaction should be selected first, the system uses lower-priority attributes only when needed to sort transactions that have the same value for the higher-priority attribute.

---

### Define the priority order

Select the **Active** option to include an attribute in the settlement priority sequence. Use the **Up** and **Down** buttons to arrange active attributes in the required order.

Example priority sequence:

1. **Transaction type**
1. **Cash discount date**
1. **Due date**
1. **Transaction date**
1. **Voucher**

When automatic settlement runs, the system evaluates the active priority attributes in sequence. If a higher-priority attribute determines which transaction should be settled first, the system uses lower-priority attributes only when needed to resolve transactions with the same priority value.

---

#### Example transactions

If you set **Use priority for automatic settlements** to **Yes** on the **Accounts receivable parameters** or **Accounts payable parameters** pages, the system uses the settlement priority you define on the **Settlement priority** page when it selects transactions for automatic settlement. For this example, the settlement priority is defined as follows:

1. Transaction type
    - Payment fees
    - Collection letters
    - Interest notes
    - Invoices

1. Transaction date, Ascending
1. Voucher

If you post a payment for 700.00 on October 25, the payment settles to the transactions in the following order.

| Voucher       | Date       | Invoice | Amount in transaction currency | Amount to settle | Balance | Currency |
|---------------|------------|---------|--------------------------------|------------------|---------|----------|
| Interest note | 10/15/2015 |         | 7.00                           | 7.00             | 0.00    | USD      |
| Invoice 1     | 8/15/2015  | 10001   | 100.00                         | 100.00           | 0.00    | USD      |
| Invoice 2     | 9/1/2015   | 10002   | 250.00                         | 250.00           | 0.00    | USD      |
| Invoice 3     | 10/15/2015 |         | 500.00                         | 343.00           | 157.00  | USD      |

---

### Settlement priority and cash discounts

To prioritize transactions that are eligible for cash discounts, activate **Cash discount date** and place it before attributes such as **Due date** or **Transaction date**.

This configuration helps ensure that transactions with earlier cash discount dates are selected before transactions that have later discount dates. If the payment qualifies for a cash discount, the discount is considered during settlement, and the payment amount required to close the invoice is reduced by the eligible discount amount.

#### Example

| Invoice | Invoice amount | Cash discount | Amount required to close |
|---|---:|---:|---:|
| Invoice 1 | 100.00 | 2.00 | 98.00 |
| Invoice 2 | 250.00 | 5.00 | 245.00 |

If the customer payment amount is **343.00**, both invoices can be closed:

- Invoice 1 is settled for **98.00**.
- Invoice 2 is settled for **245.00**.
- Total cash discount applied is **7.00**.
- Total payment consumed is **343.00**.

---

### Settlement priority and overpayments

Settlement priority determines the order in which the system selects transactions for settlement. It doesn't change the basic overpayment behavior.

If the payment amount is greater than the amount required to settle the selected transactions:

1. The system applies eligible cash discounts.
1. The system settles transactions according to the configured priority sequence.
1. Any remaining payment amount stays as an open customer payment or customer credit.
1. The remaining credit can settle future transactions based on the applicable settlement configuration.

#### Example

| Description | Amount |
|---|---:|
| Customer payment | 360.00 |
| Invoice 1 amount | 100.00 |
| Invoice 1 cash discount | 2.00 |
| Invoice 2 amount | 250.00 |
| Invoice 2 cash discount | 5.00 |
| Amount required to close both invoices | 343.00 |
| Remaining customer credit | 17.00 |

In this example, the system settles both invoices and leaves **17.00** as an open payment balance.

---

### Important considerations

- Settlement priority works only when the system automatically selects transactions for settlement.
- If you manually mark transactions for settlement, your selection takes priority over the settlement priority.
- Cash discount handling depends on whether the payment qualifies for the discount based on the configured payment terms and discount dates.
- If the payment amount exceeds the amount needed to settle the selected transactions, the system retains the remaining amount as an open payment or customer credit.
- The selected priority sequence should reflect the organization's cash application policy.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
