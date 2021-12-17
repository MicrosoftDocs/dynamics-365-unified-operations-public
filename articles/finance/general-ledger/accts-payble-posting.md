---
# required metadata

title: Accounts payable postings
description: This topic describes how postings ae configured in accounts payable and provides example posting configurations. 
author: raprofit
ms.date: 12/06/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: VendPosting, VendPaymMode, VendCashDiscount, MarkupTable\_Vend, VendPaymFee
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
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

The primary posting profile for the **Accounts payable** module is the **Vendor posting profile**. This posting profile is used to determine which summary account, which is a main account, should be used when posting vendor balances to the general ledger. The summary account is also referred to as the Accounts payable trade account.

For more information refer to [Vendor posting profiles](../accounts-payable/vendor-posting-profiles.md).

In addition to the vendor posting profile, there are a variety of additional posting configurations available in the **Accounts payable** module. The following sections provide more information about the additional posting configurations.

## Methods of payment posting accounts

Methods of payment are used to define how a payment will be posted to the general ledger and to control the behavior of the payment output. One method of payment is typically created for each type of payment that your organization makes. For example, cash, check, credit card, money order, wire, and so on.

The **Posting** group on the **General** FastTab controls how the payment will be posted to the general ledger. You must first select the **Account type**, which controls the behavior of the **Payment account** field. The recommended approach is to select Bank in the **Account type** field, and then select the **Bank account** in the **Payment account** field. The benefit to this option is that the system will post the payment into the Bank sub ledger which supports reconciliation and other cash related processes. The following table shows an example of how the posting profile would be configured if you're using **Cash and bank management**.

| Posting type | Account type | Payment account name example | Account type                       | Debit/ Credit? | Clearing account | Description                                                                        |
| :--------------: | :--------------: | :---------------------------: | :------------------------------------: | :----------------: | :------------------: | :---------------: |
| Bank         | Bank         | Bank of America           | Bank account is linked to an Asset | Debit         | No               | Enter the main account in the **Payment account** field on each method of payment. |

If you're not planning to use the **Cash and bank management** module, you will want to select **Ledger** in the **Account type** field and then select the **Main account** in the **Payment account** field. The following table shows an example of how the posting profile would be configured if you're *not* using **Cash and bank management**.

| Posting type | Account type |Payment account example | Account type    | Debit/ Credit? | Clearing account | Description                                                                        |
| :--------------: | :--------------: | :---------------------------: | :-----------------: | :----------------: | :------------------: | :------------------------: |
| Ledger       | Ledger       | 100100: Bank of America   | Asset           | Debit          | No               | Enter the main account in the **Payment account** field on each method of payment. |

## Bridging accounts

Bridging posting is a two-step process that's used with the posting of payments. It is an optional feature that can be used with zero-balance bank accounts, for example. It can be used to ensure a smoother and more timely bank reconciliation process. Bridging posting starts with posting a payment to a temporary account, or the bridging account. The entry that's posted gets reversed and posted to the bank account when the payment clears the bank.

| Posting type   | Main account example | Main account name example | Account type | Debit/ Credit? | Clearing account | Description                                                                         |
| :----------------: | :----------------------: | :---------------------------: | :--------------: | :----------------: | :------------------: | :---------------------------: |
| Ledger journal | 130725               | Uncleared Cash            | Liability    | Debit          | Yes              | Enter the main account in the **Bridging account** field on each method of payment. |

For more information, see to [Set up and process bridged payments page.] (../accounts-receivable/setup-and-process-bridged-payments.md)

## Customer cash discounts posting accounts

If your organization receives cash discounts from vendors for quick payment, you will need to configure cash discount codes and determine how the discounts should be posted to the general ledger. There are a number of options available for specifying the main account to be used for posting a customer cash discount.

For more information refer to [Cash discounts](../cash-bank-management/cash-discounts.md).

## Payment fee posting accounts

Payment fees let you automatically add a fee to a vendor payment when a set of conditions apply. Payment fees can be paid to the vendor or can be posted as an expense to your bank account.

For example, your vendor charges you 3% of the payment total for using a credit card. In another example, assume your bank charges you $1.00 for each wire that you process, and the wire fee is expensed.

When you configure a vendor payment fee, if the **Charge** field is set to **Vendor,** the **Main account** field is disabled, and the system uses the Vendor posting profile to post the fee. If you select **Ledger** in the **Charge** field, then in the Main account field you will need to select the main account where the payment fee will post. This will typically be an Expense account.

| Posting type   | Main account example | Main account name example | Account type | Debit/ Credit? | Clearing account | Description                                                                                                           |
| :----------------: | :----------------------: | :---------------------------: | :--------------: | :----------------: | :------------------: | :------------------------: |
| Ledger journal | 618190               | Bank Fee Expense          | Expense      | Debit          | No               | Select this in the **Main account** field on the **Payment fee** when **Ledger** is selected in the **Charge** field. |

For more information refer to [Define vendor payment fees](../accounts-payable/tasks/define-vendor-payment-fees.md).

## Charges code posting accounts

If you must track purchase amounts in addition to line items, you can use charges codes. For example, your supplier might charge freight and handling fees to you or might expense certain freight and handling fees internally. You can specify whether these amounts are posted to expense accounts, or whether they are added to the cost of the items.

You can create charges codes for Accounts receivable and Accounts payable. When configuring a charges code, you need to define the posting which controls both the debit and credit accounts. When you create charges codes, you can select the posting type to be used for each charge code. The following table shows examples of typical charge codes for Accounts payable.

| Posting type   | Main account example | Main account name example | Account type | Debit/ Credit? | Clearing account | Description                                                                          |
| :----------------: | :----------------------: | :---------------------------: | :--------------: | :----------------: | :------------------: | :----------------------------: |
| Purchase fee   | Leave blank          | Not applicable            | Item         | Debit          | No               | Purchase fee for item example: Debit Item and Credit Customer/Vendor. The item posting uses the main account from the Inventory posting profile.         |
| Order, freight | 600120               | Freight In                | Revenue      | Debit          | No               | Freight paid to vendor example: Debit Ledger account and Credit Customer/Vendor |
| Rebate*        | 503160               | Vendor Rebate (Contra COGS)| Expense     | Credit         | No               | Vendor rebate example: Debit Customer/Vendor and Credit Ledger account   |

*For the Rebate example, the posting is used only when a charges code is added to a purchase order header or line. Advanced rebate functionality is available in Supply Chain Management to provide more control and automation of rebates. For more information, see to [Vendor rebates](../../scm/supply-chain/procurement/vendor-rebates.md)

The preceding table shows three common examples of posting types that can be used for charges codes. The list should be used as a guideline and a selection of samples. It isn't a comprehensive list of all possible combinations or posting types that can be used. 

For more information, see to [Create charges code.](../accounts-receivable/create-charges-codes.md)
