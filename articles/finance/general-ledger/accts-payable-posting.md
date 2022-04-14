---
# required metadata

title: Accounts payable postings
description: This topic explains how postings are configured in Accounts payable and provides examples of posting configurations.
author: rachel-profitt
ms.date: 01/19/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: VendPosting, VendPaymMode, VendCashDiscount, MarkupTable\_Vend, VendPaymFee
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: c64eed1d-df17-448e-8bb6-d94d63b14607
ms.search.region: Global
# ms.search.industry: 
ms.author: kweekley
ms.search.validFrom: 2022-01-03
ms.dyn365.ops.version: AX 7.0.0

---

# Accounts payable posting

[!include [banner](../includes/banner.md)]

The primary posting profile for the **Accounts payable** module is the vendor posting profile. This posting profile determines the summary account that is used when vendor balances are posted to the general ledger. A summary account is a main account. It's also referred to as the Accounts payable trade account.

For more information, see [Vendor posting profiles](../accounts-payable/vendor-posting-profiles.md).

Several posting configurations besides the vendor posting profile are available in Accounts payable. The following sections provide more information about these other posting configurations.

## Methods of payment posting accounts

Methods of payment define how a payment will be posted to the general ledger. They also control the behavior of the payment output. Typically, one method of payment is created for each type of payment that your organization makes (for example, cash, check, credit card, money order, and wire).

The fields in the **Posting** section on the **General** FastTab on the **Methods of payment** page (**Accounts payable > Payment setup > Methods of payment**) control how a payment will be posted to the general ledger. You must first select a value in the **Account type** field. The account type that you select controls the behavior of the **Payment account** field. We recommend that you select **Bank** in the **Account type** field and then select the bank account in the **Payment account** field. The benefit of the approach is that the system will post the payment to the Bank subledger, which supports reconciliation and other cash-related processes. The following table shows an example of the posting profile configuration if you're using the **Cash and bank management** module.

| Posting type | Account type | Payment account name example | Account type | Debit/Credit? | Clearing account | Description |
|--------------|--------------|------------------------------|--------------|---------------|------------------|-------------|
| Bank | Bank | Bank of America | Bank account that is linked to an asset | Debit | No | For each method of payment, enter the main account in the **Payment account** field. |

If you aren't planning to use Cash and bank management, you should select **Ledger** in the **Account type** field and then select the main account in the **Payment account** field. The following table shows an example of the posting profile configuration if you are **not** using Cash and bank management.

| Posting type | Account type |Payment account example | Account type | Debit/Credit? | Clearing account | Description |
|--------------|--------------|------------------------|--------------|---------------|------------------|-------------|
| Ledger | Ledger | 100100: Bank of America | Asset | Debit | No | For each method of payment, enter the main account in the **Payment account** field. |

## Bridging accounts

Bridging posting is a two-step process that is used when payments are posted. It's an optional feature that can be used with zero-balance bank accounts, for example. It can help ensure a smoother and more timely bank reconciliation process. In the first step, a payment is posted to a temporary account (the bridging account). In the second step, the posted entry is reversed and posted to the bank account when the payment clears the bank. The following table shows an example of the posting profile configuration for bridging posting.

| Posting type | Main account example | Main account name example | Account type | Debit/Credit? | Clearing account | Description |
|--------------|----------------------|---------------------------|--------------|---------------|------------------|-------------|
| Ledger journal | 130725 | Uncleared Cash | Liability | Debit | Yes | For each method of payment, enter the main account in the **Bridging account** field. |

For more information, see [Set up and process bridged payments](../accounts-receivable/set-up-and-process-bridged-payments.md).

## Customer cash discounts posting accounts

If your organization receives cash discounts from vendors in return for quick payment, you must configure cash discount codes and specify how the discounts should be posted to the general ledger. Several options are available for specifying the main account that is used to post a customer cash discount.

For more information, see [Cash discounts](../cash-bank-management/cash-discounts.md).

## Payment fee posting accounts

Payment fees let you automatically add a fee to a vendor payment when a set of conditions applies. Payment fees can be paid to the vendor, or they can be posted to your bank account as an expense. Here are some examples:

- A vendor charges you 3 percent of the payment total if you pay by using a credit card.
- Your bank charges you $1.00 for each wire transfer that you process, and the wire fee is expensed.

When you configure a vendor payment fee, if you set the **Charge** field to **Vendor**, the **Main account** field becomes unavailable, and the system uses the vendor posting profile to post the fee. If you set the **Charge** field to **Ledger**, you must set the **Main account** field to the main account where the payment fee will be posted. Typically, this main account will be an expense account. The following table shows an example of the posting profile configuration for payment fee posting.

| Posting type | Main account example | Main account name example | Account type | Debit/Credit? | Clearing account | Description |
|--------------|----------------------|---------------------------|--------------|----------------|------------------|-------------|
| Ledger journal | 618190 | Bank Fee Expense | Expense | Debit | No | If **Ledger** is selected in the **Charge** field, select this account in the **Main account** field on the **Payment fee** page. |

For more information, see [Define vendor payment fees](../accounts-payable/tasks/define-vendor-payment-fees.md).

## Charges code posting accounts

If you must track purchase amounts in addition to line items, you can use charges codes. For example, your supplier might charge freight and handling fees to you, or it might expense some freight and handling fees internally. You can specify whether these amounts are posted to expense accounts or added to the cost of the items.

You can create charges codes for Accounts receivable and Accounts payable. When you configure a charges code, you must define the posting. The posting controls both the debit account and the credit account. When you create charges codes, you can select the posting type that is used for each charge code. The following table shows examples of typical charge codes for Accounts payable on the **Charges codes** page.

| Posting type | Main account example | Main account name example | Account type | Debit/Credit? | Clearing account | Description |
|--------------|----------------------|---------------------------|--------------|---------------|------------------|-------------|
| Purchase fee | Leave the field blank. | Not applicable | Item | Debit | No | **Example for a purchase fee for an item:** </p><ul><li>**Debit type** field = **Item**</li><li>  **Credit type** field =  **Customer/Vendor**.</li><li> The item posting uses the main account from the inventory posting profile. |
| Order, freight | 600120 | Freight In | Revenue | Debit | No | **Example for freight that is paid to a vendor:** </p><ul><li>**Debit type** field = **Ledger account**</li><li> **Credit type** field = **Customer/Vendor** |
| Rebate\* | 503160 | Vendor Rebate (Contra COGS)| Expense | Credit | No | **Example for a vendor rebate:**</p><ul><li>**Debit type** field = **Customer/Vendor**</li><li>**Credit type** field = **Ledger account** |

\* For the rebate example, the posting is used only when a charges code is added to a purchase order header or line. Advanced rebate functionality that is available in Microsoft Dynamics 365 Supply Chain Management provides more control and automation of rebates. For more information, see [Vendor rebates](../../supply-chain//procurement/vendor-rebates.md).

The preceding table shows three typical examples of posting types that can be used for charges codes. It should be used as a guideline and a selection of samples. It doesn't provide a comprehensive list of all possible combinations or posting types that can be used.

For more information, see [Create charges code](../accounts-receivable/create-charges-codes.md).
