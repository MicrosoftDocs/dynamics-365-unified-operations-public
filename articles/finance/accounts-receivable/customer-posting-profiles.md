---
title: Customer posting profiles
description: Learn about customer posting profiles, which control the posting of customer transactions to the general ledger.
author: JodiChristiansen
ms.author: jchrist
ms.topic: article
ms.date: 08/05/2026
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.search.form: CustPosting, CustVendExternalItem
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: cb82245e-8c02-429c-b36e-8db0e3e6f7e5
---

# Customer posting profiles

[!INCLUDE [banner](../includes/banner.md)]

This article describes customer posting profiles, which control the posting of customer transactions to the general ledger.

## Customer posting profiles

Customer posting profiles let you assign general ledger accounts and document settings to all customers, a group of customers, or a single customer. These settings apply when you create sales orders invoices, free text invoices, project invoices, payment journals, collection letters, and interest notes.

Define the default posting profile on the **Ledger and Sales Tax** tab of the **Accounts receivable parameters** page. The system automatically includes it on the header of new documents. You can change it if a different posting profile is required.

Organizations that accept prepayments from customers often configure a second posting profile for prepayments and link it in the parameters as the default posting profile for prepayments. For more information, see [Customer prepayments](customer-prepayments.md).

You can also associate posting definitions with transaction posting types on the **Transaction posting definitions** page. Use posting definitions instead of posting profiles to control the posting of customer transactions to the general ledger. For more information, see [Posting definitions](../general-ledger/posting-definitions.md).

## Creating a posting profile

Specify the ledger accounts that the system uses when posting transactions that use the selected posting profile. Select an account code and, whenever possible, an account or group number for the selected posting profile. During the posting process, the system locates the most appropriate posting profile for each transaction by searching for the most specific account code, account number, or group and number combination in the following priority order:

| Account code field value | Account/Group number field value                | Search priority |
|--------------------------|-------------------------------------------------|-----------------|
| Table                    | Specific customer account                       | 1               |
| Group                    | Customer group that is assigned to the customer | 2               |
| All                      | Blank                                           | 3               |

If you want all customer transactions to use the same posting profile, set up only one posting profile, where you enter **All** in the **Account code** field. Specify the following values to set up your posting profile.

| Field | Description |
|-------|-------------|
| **Posting profile** | Enter a code for the posting profile. For example, you could create two posting profiles to obtain one account for customer balances in the national currency and another for customer balances in a foreign currency. You could call one account National and the other Foreign. |
| **Description** | Enter a description of the posting profile. This description helps you identify the posting profile when you view it in this page. |
| **Account code** | Specify whether the posting profile applies to a single customer, a group of customers, or all customers:<ul><li>**Table** – The posting profile applies to a single customer. Select the customer account in the **Account/Group number** field.</li><li>**Group** – The posting profile applies to a customer group. Select the customer group in the **Account/Group number** field.</li><li>**All** – The posting profile applies to all customers. Leave the **Account/Group number** field blank.</li></ul> |
| **Account/Group number** | If you select **Table** in the **Account code** field, select the account number of the customer who is associated with the posting profile. If you select **Group**, select the customer group. If you select **All**, leave this field blank. |
| **Summary account** | Select the main account that the system uses as the Accounts receivable trade account for the customers who are associated with the posting profile. This account is the account for the **Customer balance** posting type. |
| **Liquidity account for payments** | Select the **Liquidity ledger account** that the system uses for cash flow forecasts. This field appears only if cash flow forecasts are enabled. |
| **Sales tax prepayments** | Select the account for sales tax for payments that are received in advance.<br><br>**Note:** Use the **Accounts receivable parameters** page to specify the posting profile that the system uses when a payment is marked as a prepayment. |
| **Liabilities for discount account** | Select the ledger account for liabilities of discount. |
| **Collection letter sequence** | Select the identifier of the collection letter sequence to use for customers to whom you assign the posting profile. |
| **Interest code** | Select the interest code to use for the calculation of interest for customers to whom you assign the posting profile. |

## Posting examples

The following table shows examples of the default posting types with sample main accounts and descriptions. The **Debit/Credit** column indicates if the transaction typically debits or credits or in some cases can post either. The **Clearing account** column indicates if the posting type is a clearing account. This account automatically reverses the amount posted when a later transaction is posted.

| Posting type | Main account example | Main account name example | Account type | Debit/Credit | Clearing account | Description |
| -------------- | ---------------------- | ------------- | -------------- | -------------- | --------------- | ------------- |
| Customer balance|130100| Accounts Receivable Trade | Asset | Both | No | Specify the account in the **Summary account** field. |
| None | 110110 | Bank account | Asset | Both | No | Specify the main account in the **Liquidity account for payments** field. This account isn't used for posting. It's used only for cash flow forecasting. |
| Sales tax prepayments | 202900 | Sales tax clearing | Liability | Both | Yes | Select the account for sales tax for payments that are received in advance. |
| Liabilities for discount account | 250600 | Deferred Revenue and Discounts | Liability | Both | Yes | Select the ledger account for liabilities of discounts. |

### Table restrictions

For transactions that have the selected posting profile, specify whether to settle transactions automatically, calculate interest, and send collection letters. You can also select the account to use when closing transactions that have the selected posting profile.

Specify the following values to set up your posting profile:

| Field                 | Description                                           |
|-----------------------|-------------------------------------------------------|
| Settlement        | Select this toggle to enable automatic settlement of transactions that have this posting profile. If you clear this toggle, you must manually settle transactions by using the **Settle open transactions** page or the **Enter customer payments** page. |
| Interest          | Select this toggle if interest should be calculated on outstanding balances for customer accounts that use this profile. If you clear this toggle, interest isn't calculated for these customers.                                           |
| Collection letter | Select this toggle if collection letters should be generated for customer accounts that use this profile. If you clear this toggle, collection letters aren't generated for these customers.                                                 |
| Close             | Select a posting profile to change to when transactions that have this posting profile are closed. A transaction is regarded as closed when it is settled in full.             |

For more information, see [Customer payment overview](../cash-bank-management/tasks/customer-payment-overview.md).

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
