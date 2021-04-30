---
# required metadata

title: Payments, posting, and reversal
description: This topic describes payments, posting of payments, and reversal of payments that are associated with Tax Deducted at Source (TDS).
author: kailiang
manager: AnnBe
ms.date: 02/12/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
# ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 15721
ms.assetid: b4b406fa-b772-44ec-8dd8-8eb818a921ef
ms.search.region: Global
# ms.search.industry: 
ms.author: kailiang
ms.search.validFrom: 2021-02-12
ms.dyn365.ops.version: AX 10.0.17

---

# Payments, posting, and reversal

[!include [banner](../includes/banner.md)]

This topic describes payments, posting of payments, and reversal of payments that are associated with Tax Deducted at Source (TDS).

## Payment allocation that uses a proportional TDS payment schedule

If the TDS payment schedule that is attached to an invoice specifies **Proportionally** as the withholding tax allocation, the installment amount is calculated based on the net amount (that is, the invoice amount after the TDS amount is deducted). For example, if the invoice amount is 100,000, and the TDS amount is 20,000, the installments are calculated based on 80,000 (100,000 – 20,000).

## COD payment terms

If the terms of payment on an attached purchase invoice are cash on delivery (COD), TDS is calculated on the invoice. The net amount (after the TDS amount is deducted) is posted to the Cash account.

## Discounts

If a line discount, multiline discount, or total discount is attached to an invoice, the calculation of TDS on the invoice amount considers the discount. For example, if the invoice amount is 10,000, and the line discount is 100, TDS is calculated on 9,900.

## Purchase invoices where a TDS group and a TCS group are attached to different invoice lines

If a TDS group and a Tax Collected at Source (TCS) group are attached to different invoice lines, the invoice can't be posted. However, if the purchase order is partially invoiced, TDS is calculated for the partial invoice amount.

## Advance payments and prepayments

TDS can be calculated on advance payments and prepayments that are made to vendors. You can attach a prepayment or advance payment by going to **Accounts payable \> Purchase order** and selecting **Functions \> Open transaction editing**. In this case, TDS will be calculated only on any amount that exceeds the advance payment or prepayment amount.

For example, an advance payment transaction for 10,000 is created for vendor 1, and TDS is calculated for the transaction. Later, a purchase invoice for 15,000 is created for vendor 1, and the advance payment transaction is linked to the invoice. For this transaction, TDS is calculated only on 5,000.

> [!NOTE]
> If the **Amount incl. sales tax** checkbox is selected for a prepayment, the payment amount that TDS is calculated on includes sales taxes.

## Automatic posting

If a purchase invoice is created by using a method of payment where the **Automatic posting** checkbox is selected, an automatic payment voucher is created for the net amount (after the TDS amount is deducted). For example, if the invoice amount is 100,000, and the total TDS amount is 11,330, the automatic payment voucher is posted for 88,670.

## Credit notes and returned item invoices

If a credit note or a returned item invoice is created by using a credit note, only the TDS amount that is calculated on the original invoice is reversed. The TDS amount isn't reversed if TDS has already been paid to the tax authority, or if the TDS settlement process has already been run for the period.

If the credit note or the returned item invoice is posted for a partial quantity, the proportionate TDS amount is reversed.

## Posting multiple journals that have withholding tax (TDS)

The calculation and accounting of withholding tax (TDS) in India depends on the threshold limit that is defined for a withholding tax component. When you post multiple journals, TDS is calculated for a journal only if the cumulative transaction amount exceeds the threshold limit that is specified for the withholding tax component. In this case, the journal amount that TDS is calculated on includes previous transactions that TDS was applied to but wasn't calculated on.

The following examples show how threshold limits are considered when multiple journals that include withholding tax (TDS) are posted. A journal can be posted only if the posting validation rules that are applicable for Indian withholding tax are satisfied.

### Example 1

The following table shows the details of a scenario where multiple journals are posted for the TDS component – Rent for vendor account 3000.

| Threshold specified for withholding tax component - Rent | Multiple journals selected for posting | | | Posting type in all the journals | Rate of withholding tax | Calculation basis for the tax component |
|---|---|---|---|---|---|---|
| 120,000 | Journal number | Journal amount | TDS group | Debit – Expenses - Rent Credit – Vendor account (3000) | TDS-10% | Line amount |
| 001 | 40,000 | Rent | Surcharge-10% | Excl line amount + \[TDS\] | | |
| 002 | 40,000 | Rent | PE-Cess-2% | Excl line amount + \[TDS + Surcharge\] | | |
| 003 | 40,000 | Rent | SHE-cess-1% | Excl line amount + \[TDS + Surcharge\] | | |
| 004 | 40,000 | Rent | | | | |

When the journals are posted simultaneously, the threshold for posting multiple journals is based on the chronological order that the journals are posted in. In this example, journal 001 is posted first. Journals 002, 003, and 004 are then posted in chronological order.

Here is the voucher entry for journal 001.

| Account               | Debit  | Credit |
|-----------------------|--------|--------|
| Expenses – Rent       | 40,000 |        |
| Vendor account (3000) |        | 40,000 |

Here is the voucher entry for journal 002.

| Account               | Debit  | Credit |
|-----------------------|--------|--------|
| Expenses – Rent       | 40,000 |        |
| Vendor account (3000) |        | 40,000 |

Here is the voucher entry for journal 003.

| Account               | Debit  | Credit |
|-----------------------|--------|--------|
| Expenses – Rent       | 40,000 |        |
| Vendor account (3000) |        | 40,000 |

Here is the voucher entry for journal 004.

| Account               | Debit     | Credit    |
|-----------------------|-----------|-----------|
| Expenses – Rent       | 40,000    |           |
| Vendor account (3000) |           | 40,000    |
| Vendor account (3000) | 18,128.00 |           |
| TDS Payable           |           | 16,000.00 |
| Surcharge Payable     |           | 1,600.00  |
| PE-Cess Payable       |           | 352.00    |
| SHE Cess Payable      |           | 176.00    |

If the **Overlook threshold** checkbox is selected for the tax code on the **Withholding tax groups** page, when the journals are posted, the withholding tax code is calculated on the individual journal amounts for all of them.

### Example 2

The following table shows the details of another scenario where multiple journals are posted for TDS component – Rent for vendor account 3000.

| Threshold specified for withholding tax component - Rent | Multiple journals selected for posting | Posting type in all the journals | Rate of withholding tax | Calculation basis for the tax code | Overlook threshold limit checkbox | Amount | Marked or unmarked |
|---|---|---|---|---|---|---|---|
| 50,000 | Journal number | Journal amount | TDS group | Debit – Expenses - Rent Credit – Vendor account (3000) | TDS-10% | Line amount | Marked |
| 005 | 20,000 | Rent | Surcharge-10% | Excel line amount + \[TDS\] | Marked | | |
| 006 | 20,000 | Rent | PE-Cess-2% | Excel line amount + \[TDS+ Surcharge\] | Unmarked | | |
| 007 | 9,000 | Rent | SHE-cess-1% | Excel line amount + \[TDS+ Surcharge\] | Marked | | |
| 008 | 2,000 | Rent | | | | | |
| 009 | 1,000 | Rent | | | Marked | | |
| 010 | 20,000 | Rent | | | Marked | | |

#### Step 1

In this example, journals 005 and 006 are posted together. If the **Overlook threshold limit** checkbox is selected, the taxes are calculated. The following table shows how the taxes for the transaction are calculated.

| Journal | Transaction amount | TDS   | Surcharge | PE-Cess | SHE-Cess |
|---------|--------------------|-------|-----------|---------|----------|
| 005     | 20,000             | 2,000 | 200       | 44      | 22       |
| 006     | 20,000             | 2,000 | 200       | 44      | 22       |

#### Step 2

The **Overlook threshold limit** checkbox is cleared. Journal 007 is posted. Taxes are calculated only if the cumulative transaction amount exceeds the specified threshold limit.

| Journal | Transaction amount | TDS  | Surcharge | PE-Cess | SHE-Cess |
|---------|--------------------|------|-----------|---------|----------|
| 007     | 9,000              | 0    | 0         | 0       | 0        |

#### Step 3

The **Overlook threshold limit** checkbox is selected. Journals 008, 009, and 010 are posted.

| Journal | Transaction amount | TDS      | Surcharge | PE-Cess | SHE-Cess |
|---------|--------------------|----------|-----------|---------|----------|
| 008     | 2,000.00           | 200.00   | 20.00     | 4.40    | 2.20     |
| 009     | 1,000.00           | 100.00   | 10.00     | 2.20    | 1.10     |
| 010     | 20,000.00          | 2,000.00 | 200.00    | 44.00   | 22.00    |

> [!NOTE]
> In the Indian business scenario, the threshold limit and the exception threshold limit aren't applicable to the TCS tax type. However, the application lets you define the threshold limit and the exception threshold limit for the TCS tax components. If they are defined, the threshold functionality that is applicable to the TDS tax codes will be applied as-is to the TCS tax codes.

## Reverse transactions

You can reverse a transaction that TDS is calculated on by going to **Accounts payable \> Vendors**, **Accounts receivable \> Customers**, or **General ledger \> Chart of accounts**, selecting **Transactions**, and then selecting **Reverse transaction**. In this case, the TDS amount is reversed together with the transaction amount.

In cases where TDS is calculated on the cumulative amount of a group of invoices because of a threshold limit, the TDS amount is reversed only when the specific invoice that the TDS is calculated on is reversed. For transactions that are created after the reversal transaction, TDS will be calculated again, and the calculation will consider the threshold limit.

For example, the threshold limit is 25,000. Three invoices are posted: one for 10,000, another for 10,000, and one for 6,000. TDS is calculated for the third invoice, on the cumulative amount of 26,000. If you reverse the first and second invoices, the TDS amount won't be reversed. It will be reversed only when you reverse the third invoice.
