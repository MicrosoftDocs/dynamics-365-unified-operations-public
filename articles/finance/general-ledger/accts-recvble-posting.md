---
title: Accounts receivable posting
description: Learn how postings are configured in Accounts receivable with examples of posting configurations and an outline on posting accounts for methods of payment.
author: rcarlson
ms.author: rcarlson
ms.topic: article
ms.date: 04/29/2024
ms.custom:
ms.reviewer: twheeloc 
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2022-01-03
ms.search.form: CustPosting, CustPaymMode, CustCashDiscount, CommissionPosting, MarkupTable\_Cust, CustPaymFee
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: c64eed1d-df17-448e-8bb6-d94d63b14607
---

# Accounts receivable posting

[!include [banner](../includes/banner.md)]

The primary posting profile for the **Accounts receivable** module is the customer posting profile. This posting profile determines the summary account that is used when customer balances are posted to the general ledger. A summary account is a main account. It's also referred to as the Accounts receivable trade account.

The **Customer to ledger reconciliation** report can be used after posting to help reconcile the balances of customer and ledger accounts. The report uses the information that is found in the summary account for the customer posting profile. It doesn't use the summary account from the accounting that is created for the document. If you make changes to the customer posting profile or the customer group that is assigned to the customer after you have posted transactions, the report may display differences between the customer and ledger account balance. To view only the lines that have differences, and any lines for which the customer accounts and ledger account are both zero, select the **Differences only** parameter when printing the report.

For more information, see [Customer posting profiles](../accounts-receivable/customer-posting-profiles.md).

Several posting configurations beside the customer posting profile are available in Accounts receivable. The following sections provide more information about these other posting configurations.

## Posting accounts for methods of payment

Methods of payment define how a payment will be posted to the general ledger. They also control the behavior of the payment output. Typically, one method of payment is created for each type of payment that your organization accepts (for example, cash, check, credit card, money order, and wire transfer).

The fields in the **Posting** section on the **General** FastTab control how a payment will be posted to the general ledger. You must first select a value in the **Account type** field. The account type that you select controls the behavior of the **Payment account** field. We recommend that you select **Bank** in the **Account type** field and then select the bank account in the **Payment account** field. The benefit of this approach is that the system will post the payment to the Bank subledger, which supports reconciliation and other cash-related processes. The following table shows an example of the posting profile configuration if you're using the **Cash and bank management** module.

| Posting type | Account type | Main account name example | Account type | Debit/Credit? | Clearing account | Description |
|--------------|--------------|---------------------------|--------------|---------------|------------------|-------------|
| Bank | Bank | Bank of Contoso | Bank account that is linked to an asset | Credit | No | For each method of payment, enter the main account in the **Payment account** field. |

If you don't plan to use Cash and bank management, you should select **Ledger** in the **Account type** field and then select the main account in the **Payment account** field. The following table shows an example of the posting profile configuration if you aren't using Cash and bank management.

| Posting type | Account type | Main account name example | Account type | Debit/Credit? | Clearing account | Description |
|--------------|--------------|---------------------------|--------------|---------------|------------------|-------------|
| Ledger | Ledger | 100100: Bank of Contoso | Asset | Credit | No | For each method of payment, enter the main account in the **Payment account** field. |

## Bridging accounts

Bridging posting is a two-step process that is used when payments are posted. It's an optional feature that can be used with zero-balance bank accounts, for example. It can help ensure a smoother and more timely bank reconciliation process. In the first step, a payment is posted to a temporary account (the bridging account). In the second step, the posted entry is reversed and posted to the bank account when the payment clears the bank. The following table shows an example of the posting profile configuration for bridging posting.

| Posting type | Main account example | Main account name example | Account type | Debit/Credit? | Clearing account | Description |
|--------------|----------------------|---------------------------|--------------|---------------|------------------|-------------|
| Ledger journal | 130725 | Uncleared Cash | Liability | Debit | Yes | For each method of payment, enter the main account in the **Bridging account** field. |

For more information, see [Set up and process bridged payments](../accounts-receivable/set-up-and-process-bridged-payments.md).

## Posting accounts for customer cash discounts

If your organization offers cash discounts to customers in return for quick payment, you must configure cash discount codes and specify how the discounts should be posted to the general ledger. Several options are available for specifying the main account that is used to post a customer cash discount.

For more information, see [Cash discounts](../cash-bank-management/cash-discounts.md).

## Posting accounts for payment fees

Payment fees let you automatically add a fee to a customer payment when a set of conditions applies. Payment fees can be charged to the customer, or they can be posted to your bank account as an expense. Here are some examples:

- You charge customers 3 percent of the payment total if they pay by using a credit card.
- Your bank charges you $1.00 for each wire transfer that you process, and the wire transfer fee is expensed.

When you configure a customer payment fee, if you set the **Charge** field to **Customer**, the **Main account** field becomes unavailable, and the system uses the customer posting profile to post the fee. If you set the **Charge** field to **Ledger**, you must set the **Main account** field to the main account where the payment fee will be posted. Typically, this main account will be an expense account. The following table shows an example of the posting profile configuration for payment fee posting.

| Posting type | Main account example | Main account name example | Account type | Debit/Credit? | Clearing account | Description |
|--------------|----------------------|---------------------------|--------------|---------------|------------------|-------------|
| Ledger journal | 618190 | Bank Fee Expense | Expense | Debit | No |  If **Ledger** is selected in the **Charge** field, select this account in the **Main account** field for the payment fee. |

For more information, see [Establish customer payment fees](../accounts-receivable/tasks/establish-customer-payment-fees.md).

## Posting accounts for charges codes

If you must track sales amounts in addition to line items, you can use charges codes. For example, you might charge freight and handling fees to your customers, or you might expense some freight and handling fees internally. You can specify whether these amounts are posted to expense accounts or added to the cost of the items.

You can create charges codes for Accounts receivable and Accounts payable. When you configure a charges code, you must define the posting. The posting controls both the debit account and the credit account. For each charges codes that you create, you can select the posting type that is used. The following table shows typical examples of charges codes for Accounts receivable.

| Posting type | Main account example | Main account name example | Account type | Debit/Credit? | Clearing account | Description |
|--------------|----------------------|---------------------------|--------------|---------------|------------------|-------------|
| Payment fee | 411400 | Revenue – Fees | Revenue | Credit | No | **Example for non-sufficient funds:** Debit Customer/Vendor and Credit Ledger account |
| Order, freight | 403500 | Revenue – Freight | Revenue | Credit | No | **Example for freight that is charged to a customer:** Debit Customer/Vendor and Credit Ledger account |
| Rebate\* | 403200 | Discount | Revenue | Debit | No | **Example for a customer rebate:** Debit Ledger account and Credit Customer/Vendor |

\* For the rebate example, the posting is used only when a charges code is added to a purchase order header or line. Advanced rebate functionality that is available in Microsoft Dynamics 365 Supply Chain Management provides more control and automation of rebates. For more information, see [Customer rebates](../../supply-chain/sales-marketing/tasks/process-customer-rebates.md).

The preceding table shows three typical examples of posting types that can be used for charges codes. It should be used as a guideline and a sample. It doesn't provide a comprehensive list of all possible combinations or posting types that can be used.

For more information, see [Create charges code](../accounts-receivable/create-charges-codes.md).

## Posting accounts for commissions

You can optionally configure the system to calculate commissions for a sales representative or a group of sales representatives on a given sales order. If you enable this functionality, you must configure the posting account that is used to calculate the commission. This configuration is done on the **Commission posting** page in the **Sales and marketing** module.

For more information, see [Set up sales commission rules](../../supply-chain/sales-marketing/tasks/set-up-sales-commission-rules.md).
