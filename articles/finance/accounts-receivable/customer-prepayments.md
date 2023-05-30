---
# required metadata

title: Customer prepayments
description: This article explains how to set up and process customer prepayments (also known as customer deposits).
author: twheeloc
ms.date: 11/21/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: CustPosting, LedgerJournalTransCustPaym, CustParameters
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc

# ms.tgt_pltfrm: 
ms.assetid: cb82245e-8c02-429c-b36e-8db0e3e6f7e5
ms.search.region: Global
# ms.search.industry: 
ms.author: raprofit
ms.search.validFrom: 
ms.dyn365.ops.version: AX 7.0.0

---

# Customer prepayments

[!include [banner](../includes/banner.md)]

Customer prepayments are used when you receive a payment from a customer, but there is no invoice that the payment can be settled against. These types of payments are also referred to as customer deposits.

The process of setting up and working with customer prepayments consists of the following basic steps.

1. Create a customer posting profile for prepayments.
2. Set the **Posting profile with prepayment journal voucher** parameter.
3. Create a customer payment journal, and select the **Prepayment journal voucher** checkbox on each line.
4. Post the customer payment journal.
5. After an invoice is generated, settle the prepayment with it by using the **Settle open transactions** page.

## Create a customer posting profile for prepayments

Typically, when you accept prepayments or deposits from your customers before goods or services are delivered, or before an invoice exists in your system, you will want to record the cash as a liability instead of an asset in your chart of accounts. However, the requirements for recording these amounts in your general ledger might differ, depending on your country or region. Therefore, be sure to consult your accountants about any local regulations that apply.

In general, the process for creating a posting profile that can be used for prepayments is the same as the process for creating other posting profiles. The primary difference is the main account that you select in the **Summary account** field. For more information, see [Customer posting profiles](customer-posting-profiles.md).

## Define parameters for customer prepayments

There are two main Accounts receivable parameters that you must consider when you configure the system for customer prepayments. Follow these steps to configure the parameters.

1. Go to **Accounts receivable \> Setup \> Accounts receivable parameters**.
2. Optional: On the **Ledger and sales tax** tab, on the **Payment** FastTab, set the **Sales tax on prepayment journal voucher** option to **Yes**.
3. In the **Posting profile with prepayment journal voucher** field, select the customer posting profile to use when customer prepayments are posted.
4. Close the page.

## Create customer prepayment vouchers

When you create the customer payment journal, for every prepayment, you must set the **Prepayment journal voucher** option to **Yes** on the **Customer payment journal** page. Follow these steps to create a customer prepayment.

1. Go to **Accounts receivable \> Payments \> Customer payment journal**.
2. Select **New** to create a journal.
3. In the **Name** field, select the journal name to use.

    > [!IMPORTANT]
    > If you set the **Sales tax on prepayment journal voucher** option to **Yes** in the previous procedure, you must select a journal name where the **Amount includes sales tax** parameter is selected. 

4. Optional: In the **Description** field, enter a detailed description.
5. Select **Lines**.
6. If a blank line doesn't exist, select **New** to create a line.
7. In the **Date** field, enter the date when the prepayment should be posted.
8. In the **Account** field, select the customer for the prepayment.
9. Optional: In the **Description** field, enter a detailed description of the transaction.
10. In the **Credit** field, enter the amount of the prepayment.
11. In the **Offset account** field, select the account to offset the payment to. For example, select the bank or main account to post the payment to.
12. In the **Method of payment** field, select the customer's method of payment.
13. On the **Payment** tab, set the **Prepayment journal voucher** option to **Yes**.
14. Repeat steps 7 through 13 for each additional prepayment that must be posted.
15. Select **Post** to finalize the journal.

## Settle prepayments with invoices

You can use the **Customer payments** workspace to easily find and settle payments that haven't been fully settled.

1. On the **Home** dashboard, select the **Customer payments** tile.
2. In the **Customer transactions** section, on the **Payments not settled** tab, search for and select the payment to settle.
3. Select **Settle transactions**.
4. Select the **Mark** checkbox for the invoice and the payment that will be settled.
5. Select **Post**.

For more information about how to settle open transactions, see [Settlement overview](/dynamics365/finance/cash-bank-management/settlement-overview).
