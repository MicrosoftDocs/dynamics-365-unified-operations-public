---
title: Vendor posting profiles
description: Vendor posting profiles control the posting of vendor transactions to the general ledger. Learn how to create a posting profile.
author: twheeloc
ms.author: shpandey
ms.topic: article
ms.date: 07/29/2026
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.search.form: VendPosting
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 18def866-7655-4f0b-b299-eec83098d23a
---

# Vendor posting profiles

[!include [banner](../includes/banner.md)]

Vendor posting profiles control the posting of vendor transactions to the general ledger.

## Vendor posting profiles

Vendor posting profiles enable you to assign general ledger accounts and document settings to all vendors, a group of vendors, or a single vendor. These settings apply when you create purchase orders, vendor invoices, and cash payments. For some transactions, you can select a posting profile that differs from and takes precedence over the posting profiles that you set up on this page. You define the default posting profile on the **Ledger and Sales Tax** FastTab on the **Accounts payable parameters** page. The default posting profile automatically appears on the header of new documents, where you can change it to a different posting profile if needed.

You can also associate posting definitions with transaction posting types on the **Transaction posting definitions** page. Posting definitions control the posting of vendor transactions to the general ledger instead of posting profiles.

## Creating a posting profile

### Setup

Specify the ledger accounts that are used in the posting of transactions that use the selected posting profile. Select an account code and, whenever possible, an account or group number for the selected posting profile. In the posting process, the system locates the most appropriate posting profile for each transaction by searching for the most specific account code, account number, or group and number combination in the following priority.

| **Account code** field value | **Account/Group number** field value        | Search priority |
|------------------------------|---------------------------------------------|-----------------|
| **Table**                    | Specific vendor account                     | 1               |
| **Group**                    | Vendor group that is assigned to the vendor | 2               |
| **All**                      | Blank                                       | 3               |

If you want all vendor transactions to use the same posting profile, set up only one posting profile with **All** in the **Account code** field. Specify the following values to set up your posting profile.

| Field | Description |
|-------|-------------|
| **Posting profile** | Enter a code for the posting profile. For example, you could create two posting profiles to obtain one account for vendor balances in the national currency and another for vendor balances in a foreign currency. You could call one account National and the other Foreign. |
| **Description** | Enter a description of the posting profile. |
| **Account code** | Specify whether the posting profile applies to a specific vendor, a group of vendors, or all vendors:<ul><li>**Table** – The posting profile applies to a single vendor. Select the vendor account in the **Account/Group number** field.</li><li>**Group** – The posting profile applies to a vendor group. Select the vendor group in the **Account/Group number** field.</li><li>**All** – The posting profile applies to all vendors. Leave the **Account/Group number** field blank.</li></ul> |
| **Account/Group number** | If you select **Table** in the **Account code** field, select the account number of the vendor that is associated with the posting profile. If you select **Group**, select a vendor group. If you select **All**, leave this field blank. |
| **Summary account** | Select the ledger account that the system uses as the summary account for the vendors that the posting profile relates to. The **Do not allow manual entry** parameter for this main account is marked. If you subsequently remove this account from the posting profile, validate the **Do not allow manual entry** setting on the **Main accounts** page.<br><br>**Note:** If you select the **Use posting definitions** option on the **General ledger parameters** page, the transaction posting definition for vendor invoices is used instead of the summary account. |
| **Settle account** | Select the liquidity ledger account that is used for cash flow forecasts. This field is only available when cash flow forecasting is enabled. |
| **Sales tax prepayments** | Select the account for sales tax payments that are received in advance.<br><br>**Note:** The posting profile that the system uses when the payment is marked as a prepayment is selected in the **Posting** profile with **Prepayment journal voucher** field in the **Ledger and sales tax** area on the **Accounts payable parameters** page. |
| **Arrival** | Select the ledger account that the system posts information about unapproved vendor invoices to. The user enters the information in the **Invoice register journal**. For example, a user enters very basic information about vendor invoices when they are received in the invoice register. When the invoice register is posted, the system posts the transactions to the account that is entered here and in the **Offset account** field. When the invoices are approved, the system transfers the debt from the arrival account to the vendor summary account. |
| **Offset account** | Select the ledger account that you use to offset unapproved vendor invoices when you update them by using the invoice register. The offset account works as the offset account for transactions that you post to arrival accounts. Therefore, the account contains vendor purchases that aren't yet approved. |

### Table restrictions

For transactions that have the selected posting profile, specify whether to settle transactions automatically, calculate interest, and send collection letters. You can also select the account to use when closing transactions that have the selected posting profile.

Specify the following values to set up your posting profile

| Field          | Description             |
|----------------|--------------------------------------------------------------------------|
| **Settlement** | Select this option to enable automatic settlement of transactions that have this posting profile. If you clear this option, you must manually settle transactions by using the **Settle open transactions** page. |
| **Cancel**     | Select this option if you want to be able to cancel transactions that have this posting profile.                              |
| **Close**      | Select a posting profile to change to when closing transactions that have this posting profile. A transaction is closed when it's fully settled.                                       |

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
