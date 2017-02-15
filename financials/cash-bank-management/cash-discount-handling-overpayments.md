---
# required metadata

title: Handling cash discounts for overpayments
description: This article provides scenarios that show how a payment is handled when the customer takes a cash discount but also overpays. 
author: twheeloc
manager: AnnBe
ms.date: 2015-12-02 23 - 14 - 39
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

ms.search.form: CustOpenTrans, CustParameters, LedgerJournalTransCustPaym, LedgerJournalTransVendPaym, VendOpenTrans, VendParameters
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 14171
ms.assetid: 97defcb5-9cc9-4e86-b7e1-504332ce5c1e
ms.search.region: Global
# ms.search.industry: 
ms.author: kweekley
ms.dyn365.intro: Feb-16
ms.dyn365.version: AX 7.0.0

---

# Handling cash discounts for overpayments

This article provides scenarios that show how a payment is handled when the customer takes a cash discount but also overpays. 

An invoice is considered overpaid when the payment amount is more than the invoice amount minus the cash discount. To specify how an obtainable cash discount difference is handled when an invoice is overpaid, use the **Cash discount administration** and **Maximum overpayment or underpayment** fields on the **Accounts receivable parameters** page. In the following example, the customer has overpaid the invoice by 0.50.

| Invoice total | Cash discount available | Amount to be paid, which includes the cash discount | Amount the customer actually pays |
|---------------|-------------------------|-----------------------------------------------------|-----------------------------------|
| 105.00        | 10.50                   | 94.50                                               | 95.00                             |

## Cash discount administration = Specific
When **Specific** is selected in the **Cash discount administration** field on the **Accounts for automatic transactions** page, the full cash discount is taken. The overpayment amount either is posted to a cash discount difference ledger account or remains a balance on the customer’s account. The behavior depends on whether the overpayment amount is between 0.00 and the amount that is entered in the **Maximum overpayment or underpayment** field, or whether the overpayment amount is more than the **Maximum overpayment or underpayment** amount.

### Scenario 1

In this scenario, the overpayment amount is between 0.00 and the maximum overpayment or underpayment. An invoice for 105.00 is entered, and a cash discount is available if the invoice is paid within seven days.

| Invoice total | Cash discount available | Amount to be paid, which includes the cash discount |
|---------------|-------------------------|-----------------------------------------------------|
| 105.00        | 10.50                   | 94.50                                               |

The customer submits a payment for 95.00 within the cash discount period. The payment is settled against the invoice for 105.00. After the invoice and payment are settled, the following transactions are created for the customer in Accounts receivable.

| Transaction   | Amount | Balance |
|---------------|--------|---------|
| Invoice       | 105.00 | 0.00    |
| Payment       | -95.00 | 0.00    |
| Cash discount | -10.50 | 0.00    |

The following accounting entries are generated for the payment and the settlement. **Payment**

| Account             | Debit amount | Credit amount |
|---------------------|--------------|---------------|
| Cash                | 95.00        |               |
| Accounts receivable |              | 95.00         |

**Settlement**

| Account                                                                                                          | Debit amount | Credit amount |
|------------------------------------------------------------------------------------------------------------------|--------------|---------------|
| Cash discount (the **Main account for customer discounts** field on the **Cash discounts** page)                 | 10.50        |               |
| Accounts receivable                                                                                              |              | 10.50         |
| Customer cash discount (the **Customer cash discount** field on the **Account for automatic transactions** page) |              | 0.50          |
| Accounts receivable                                                                                              | 0.50         |               |

### Scenario 2

In this scenario, the overpayment amount exceeds the maximum overpayment or underpayment amount. An invoice for 105.00 is entered, and a cash discount is available if the invoice is paid within seven days.

| Invoice total | Cash discount available | Amount to be paid, which includes the cash discount |
|---------------|-------------------------|-----------------------------------------------------|
| 105.00        | 10.50                   | 94.50                                               |

The customer submits a payment for 95.00 within the cash discount period. The payment is settled against the invoice for 105.00. After the invoice and payment are settled, the following transactions are created for the customer in Accounts receivable.

| Transaction   | Amount | Balance |
|---------------|--------|---------|
| Invoice       | 105.00 | 0.00    |
| Payment       | -95.00 | -0.50   |
| Cash discount | -10.50 | 0.00    |

The overpayment amount of 0.50 will remain as an open balance on the payment and can be settled against another invoice. The following accounting entries are generated for the payment and the settlement. **Payment**

| Account             | Debit amount | Credit amount |
|---------------------|--------------|---------------|
| Cash                | 95.00        |               |
| Accounts receivable |              | 95.00         |

**Settlement**

| Account                                                                                          | Debit amount | Credit amount |
|--------------------------------------------------------------------------------------------------|--------------|---------------|
| Cash discount (the **Main account for customer discounts** field on the **Cash discounts** page) | 10.50        |               |
| Accounts receivable                                                                              |              | 10.50         |

## Cash discount administration = Unspecific
When **Unspecific** is selected in the **Cash discount administration** field on the **Accounts for automatic transactions** page, the cash discount amount is reduced by the overpayment amount. This behavior always applies, regardless of whether the overpayment amount is over or under the amount that is entered in the **Maximum overpayment or underpayment** field.

### Scenario 3

In this scenario, an invoice for 105.00 is entered, and a cash discount is available if the invoice is paid within seven days.

| Invoice total | Cash discount available | Amount to be paid, which includes the cash discount |
|---------------|-------------------------|-----------------------------------------------------|
| 105.00        | 10.50                   | 94.50                                               |

The customer submits a payment for 95.00 within the cash discount date. The payment is settled against the invoice for 105.00. After the invoice and payment are settled, the following transactions are created for the customer in Accounts receivable.

| Transaction   | Amount | Balance |
|---------------|--------|---------|
| Invoice       | 105.00 | 0.00    |
| Payment       | -95.00 | -0.00   |
| Cash discount | -10.00 | 0.00    |

The cash discount amount is reduced from 10.50 to 10.00. The payment and invoice are considered settled. **Payment**

| Account             | Debit amount | Credit amount |
|---------------------|--------------|---------------|
| Cash                | 95.00        |               |
| Accounts receivable |              | 95.00         |

**Settlement**

| Account                                                                                          | Debit amount | Credit amount |
|--------------------------------------------------------------------------------------------------|--------------|---------------|
| Cash discount (the **Main account for customer discounts** field on the **Cash discounts** page) | 10.50        |               |
| Accounts receivable                                                                              |              | 10.50         |



