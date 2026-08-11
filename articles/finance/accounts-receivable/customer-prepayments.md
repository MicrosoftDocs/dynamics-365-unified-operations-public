---
title: Customer prepayments
description: Learn about how to set up and process customer prepayments (also known as customer deposits), including an outline on creating customer posting profiles for prepayments.
author: JodiChristiansen
ms.author: jchrist
ms.topic: article
ms.date: 08/05/2026
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 
ms.search.form: CustPosting, LedgerJournalTransCustPaym, CustParameters
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: cb82245e-8c02-429c-b36e-8db0e3e6f7e5
---

# Customer prepayments

[!include [banner](../includes/banner.md)]

Use customer prepayments when you receive a payment from a customer but don't have an invoice to settle the payment. These types of payments are also referred to as customer deposits.

The process of setting up and working with customer prepayments consists of the following basic steps.

1. Create a customer posting profile for prepayments.
1. Set the **Posting profile with prepayment journal voucher** parameter.
1. Create a customer payment journal, and select the **Prepayment journal voucher** checkbox on each line.
1. Post the customer payment journal.
1. After an invoice is generated, settle the prepayment with it by using the **Settle open transactions** page.

## Create a customer posting profile for prepayments

Typically, when you accept prepayments or deposits from your customers before goods or services are delivered, or before an invoice exists in your system, record the cash as a liability instead of an asset in your chart of accounts. However, the requirements for recording these amounts in your general ledger might differ, depending on your country or region. Therefore, consult your accountants about any local regulations that apply.

In general, the process for creating a posting profile that you can use for prepayments is the same as the process for creating other posting profiles. The primary difference is the main account that you select in the **Summary account** field. For more information, see [Customer posting profiles](customer-posting-profiles.md).

## Define parameters for customer prepayments

Two main Accounts receivable parameters require consideration when you configure the system for customer prepayments. Follow these steps to configure the parameters.

1. Go to **Accounts receivable \> Setup \> Accounts receivable parameters**.
1. (Optional) On the **Ledger and sales tax** tab, on the **Payment** FastTab, set the **Sales tax on prepayment journal voucher** option to **Yes**.
1. In the **Posting profile with prepayment journal voucher** field, select the customer posting profile to use when customer prepayments are posted.
1. Close the page.

## Create customer prepayment vouchers

When you create the customer payment journal, set the **Prepayment journal voucher** option to **Yes** on the **Customer payment journal** page for every prepayment. Follow these steps to create a customer prepayment.

1. Go to **Accounts receivable \> Payments \> Customer payment journal**.
1. Select **New** to create a journal.
1. In the **Name** field, select the journal name to use.

    > [!IMPORTANT]
    > If you set the **Sales tax on prepayment journal voucher** option to **Yes** in the previous procedure, select a journal name where the **Amount includes sales tax** parameter is selected.

1. (Optional) In the **Description** field, enter a detailed description.
1. Select **Lines**.
1. If a blank line doesn't exist, select **New** to create a line.
1. In the **Date** field, enter the date when the prepayment should be posted.
1. In the **Account** field, select the customer for the prepayment.
1. (Optional) In the **Description** field, enter a detailed description of the transaction.
1. In the **Credit** field, enter the amount of the prepayment.
1. In the **Offset account** field, select the account to offset the payment to. For example, select the bank or main account to post the payment to.
1. In the **Method of payment** field, select the customer's method of payment.
1. On the **Payment** tab, set the **Prepayment journal voucher** option to **Yes**.
1. Repeat steps 7 through 13 for each additional prepayment that you must post.
1. Select **Post** to finalize the journal.

## Settle prepayments with invoices

Use the **Customer payments** workspace to easily find and settle payments that aren't fully settled.

1. On the **Home** dashboard, select the **Customer payments** tile.
1. In the **Customer transactions** section, on the **Payments not settled** tab, search for and select the payment to settle.
1. Select **Settle transactions**.
1. Select the **Mark** checkbox for the invoice and the payment that you want to settle.
1. Select **Post**.

For more information about how to settle open transactions, see [Settlement overview](/dynamics365/finance/cash-bank-management/settlement-overview).
