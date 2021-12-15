---
# required metadata

title: Accounts receivable postings
description: This topic describes how postings ae configured in accounts receivable and provides example posting configurations. 
author: raprofit
ms.date: 12/03/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: CustPosting, CustPaymMode, CustCashDiscount, CommissionPosting, MarkupTable\_Cust, CustPaymFee
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom

---
# Accounts receivable posting
The primary posting profile for the **Accounts receivable** module is the **Customer posting profile**. This posting profile is used to determine which summary account, which is a main account, should be used when posting customer balances to the general ledger. The summary account is also referred to as the Accounts receivable trade account.

For more information refer to [Customer posting profiles](../accounts-receivable/customer-posting-profiles.md).

In addition to the customer posting profile, there are a variety of additional posting configurations available in the Accounts receivable module. The following sections provide more information about the additional posting configurations.

## Methods of payment posting accounts

Methods of payment are used to define how a payment will be posted to the general ledger and to control the behavior of the payment output. One method of payment is typically created for each type of payment that your organization accepts. For example, cash, check, credit card, money order, wire, and so on.

The **Posting** group on the **General** FastTab controls how the payment will be posted to the general ledger. You must first select the **Account type,** which controls the behavior of the **Payment account** field. The recommended approach is to select Bank in the **Account type** field, and then select the **Bank account** in the **Payment account** field. The benefit to this option is that the system will post the payment into the Bank sub ledger which supports reconciliation and other cash related processes. The table below shows an example of how the posting profile would be configured if you are using the **Cash and bank management** module.

| Posting type | Account type | Main account name example | Account type                       | Debit/ Credit? | Clearing account | Description                                                                        |
|--------------|--------------|---------------------------|------------------------------------|----------------|------------------|------------------------------------------------------------------------------------|
| Bank         | Bank         | Bank of Contoso           | Bank account is linked to an Asset | Credit         | No               | Enter the main account in the **Payment account** field on each method of payment. |

If you are not planning to use the **Cash and bank management** module, you will want to select **Ledger** in the **Account type** field and then select the **Main account** in the **Payment account** field. The table below shows an example of how the posting profile would be configured if you are not using the **Cash and bank management** module.

| Posting type | Account type | Main account name example | Account type    | Debit/ Credit? | Clearing account | Description                                                                        |
|--------------|--------------|---------------------------|-----------------|----------------|------------------|------------------------------------------------------------------------------------|
| Ledger       | Ledger       | 100100: Bank of Contoso   | Asset           | Credit         | No               | Enter the main account in the **Payment account** field on each method of payment. |

## Bridging accounts

Bridging posting is a two-step process that is used with the posting of payments. It is an optional feature that can be used with zero-balance bank accounts, for example. It can be used to ensure a more smooth and timely bank reconciliation process. Bridging posting starts with posting to a temporary, or the bridging account, that gets reversed and posted to the bank account when the payment clears the bank.

| Posting type   | Main account example | Main account name example | Account type | Debit/ Credit? | Clearing account | Description                                                                         |
|----------------|----------------------|---------------------------|--------------|----------------|------------------|-------------------------------------------------------------------------------------|
| Ledger journal | 130725               | Uncleared Cash            | Liability    | Debit          | Yes              | Enter the main account in the **Bridging account** field on each method of payment. |

For more information, refer to [Set up and process bridged payments.](../accounts-receivable/setup-and-process-bridged-payments.md)

## Customer cash discounts posting accounts

If your organization chooses to offer cash discounts to customers for quick payment, you will need to configure cash discount codes and determine how the discounts should be posted to the general ledger. There are a variety of options available for specifying the main account to be used for posting a customer cash discount.

For more information refer to [Cash discounts](../cash-bank-management/cash-discounts.md).

## Payment fee posting accounts

Payment fees allow you to automatically add a fee to a customer payment when a set of conditions apply. Payment fees can be charged back to the customer or can be posted as an expense to your bank account.

For example, you charge customer 3% of the payment total for using a credit card. In another example, assume your bank charges you $1.00 for each wire that you process, and the wire fee is expensed.

When you configure a customer payment fee, if the **Charge** field is set to **Customer,** the **Main account** field is disabled, and the system uses the Customer posting profile to post the fee. If you select **Ledger** in the **Charge** field, then in the Main account field you will need to select the main account where the payment fee will post. This will typically be an Expense account.

| Posting type   | Main account example | Main account name example | Account type | Debit/ Credit? | Clearing account | Description                                                                                                           |
|----------------|----------------------|---------------------------|--------------|----------------|------------------|-----------------------------------------------------------------------------------------------------------------------|
| Ledger journal | 618190               | Bank Fee Expense          | Expense      | Debit          | No               | Select this in the **Main account** field on the **Payment fee** when **Ledger** is selected in the **Charge** field. |

For more information refer to [Establish customer payment fees](../accounts-receivable/tasks/establish-customer-payment-fees.md).

## Charges code posting accounts

If you must track sales amounts in addition to line items, you can use charges codes. For example, you might charge freight and handling fees to your customer or expense certain freight and handling fees internally. You can specify whether these amounts are posted to expense accounts, or whether they are added to the cost of the items.

You can create charges codes for Accounts receivable and Accounts payable. When configuring a charges code, you need to define the posting which controls both the debit and credit accounts. When you create charges codes, you can select the posting type to be used for each charge code. The following table shows typical examples of charge codes for Accounts receivable.

| Posting type   | Main account example | Main account name example | Account type | Debit/ Credit? | Clearing account | Description                                                                          |
|----------------|----------------------|---------------------------|--------------|----------------|------------------|--------------------------------------------------------------------------------------|
| Payment fee    | 411400               | Revenue – Fees            | Revenue      | Credit         | No               | Non sufficient fund example: Debit Customer/Vendor and Credit Ledger account         |
| Order, freight | 403500               | Revenue – Freight         | Revenue      | Credit         | No               | Freight charged to customer example: Debit Customer/Vendor and Credit Ledger account |
| Rebate*         | 403200               | Discount                  | Revenue      | Debit          | No               | Customer rebate example: Debit Ledger account and Credit Customer/Vendor             |

*For the Rebate example shown in the table above, the posting is used only when a charges code is added to a purchase order header or line. Advanced rebate functionality is available in Supply Chain Management to have more control and automation of rebates. For more information, refer to [Customer rebates](../../supply-chain/sales-marketing/tasks/process-customer-rebates.md)

The table above shows three common examples of posting types that can be used for charges codes. The list should be used as a guideline and samples and is not a comprehensive list of all possible combinations or posting types that can be used.

For more information, refer to [Create charges code.](../accounts-receivable/create-charges-codes.md)

## Commission posting accounts

You can optionally configure the system to calculate commissions for a sales representative or group of sales representatives on a given sales order. When you enable this functionality, you will need to configure the posting account to be used for calculating the commission. This is done in the **Commission posting** page in the **Sales and marketing** module.

For more information, refer to [Set up sales commission rules](../../supply-chain/sales-marketing/tasks/set-up-sales-commission-rules.md).
