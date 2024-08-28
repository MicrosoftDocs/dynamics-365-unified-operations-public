---
title: Local specific posting of sales VAT
description: Learn about specific settings for posting value-added tax (VAT) payable transactions in accordance with Russian legislation.
author: epodkolzina
ms.author: epodkolzina
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 06/26/2024
ms.reviewer: johnmichalak
audience: Application User
ms.search.region: Russia
ms.search.validFrom: 2019-07-23
ms.dyn365.ops.version: 10.0.1
---

# Local specific posting of sales VAT 

[!include [banner](../../includes/banner.md)]

## General principles of tax accounting

1. Sales tax codes should be determined. For each sales tax code, the following information is determined: the type of tax (VAT, excise, and so on), the base for the tax calculation, the rate or value, the period of validity, and the rules for posting to accounts. The posting rules are set by specifying the posting group for the sales tax code. The ledger accounts are set up on the **Ledger posting groups**. The ledger accounts will be used when accounting transactions are performed for a tax code.
2. Tax codes are combined into sales tax groups and item sales tax groups.
3. When a purchase or sales transaction is performed, sales tax groups and item sales tax groups will be indicated. The system determines which taxes (tax codes) are included in both the sales tax group and the item sales tax group. It also calculates the taxes, and generates accounting transactions for them when the operation is posted.

For more information, see [Indirect taxes overview](../../general-ledger/indirect-taxes-overview.md).

## Posting of VAT payable in Russia
The following table shows an example of accounting entries for sales of goods and services in Russia.

| **Transaction**                          | **Amount**                    | **Origin of transactions**                                                                                                                                                                                                                                                                                                  |
|------------------------------------------|-------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| D62 [Debts] C90.1 [Revenue]              | Sales amount, including taxes | The debit account is determined from the setup of customer posting. The credit account is determined from the setup of either the revenue account from the inventory posting or the revenue account from the sales free text invoice line (**Main account** field).                                                         |
| D90.2 [Cost of goods sold] C41 [Goods]   | Cost of goods and services    | Accounts are determined from the setup of the inventory posting.                                                                                                                                                                                                                                                            |
| D90.3 [VAT from sales] C68 [Taxes] / VAT | VAT amount                    | The debit and credit accounts are determined from the setup of the ledger posting groups for taxes. The debit account is determined from the **Payment offset account** field. The credit account is determined from the **Sales Tax Payable** field of the **Ledger posting groups** page (**Tax** \> **Setup** \> **Sales tax**). |

## System setup

### Set up **fixed offset posting**

To perform sales transactions in accordance with Russian standards, you must complete the following configuration as shown in the preceding.

1. Go to **Tax** \> **Parameters** \> **Setup** \> **General ledger parameters**.
2. On the **Sales tax** tab, make sure that the **Calculation method** field is set to
    **Line**.
3. Make sure that the **Fixed offset posting** option is turned on.

> [!NOTE] 
> If the **Fixed offset posting** option is turned off, the system performs the following transactions for sales of goods and services:
>
> - D90.2 C41 – Cost price
> - D62 C90.1 – Sales amount without taxes
> - D62 C68 – Tax amount

## Set up a posting group

A posting group must be specified for each sales tax code. Use the standard method to set up parameters in the posting group.

1. Go to **Tax** \> **Setup** \> **Sales tax** \> **Ledger posting groups** to open the **Ledger
    posting groups** page.
2. In the **Ledger Posting group** field, enter unique code for the posting
    group.
3. In the **Description** field, enter a description of the posting group.
4. In the **Sales Tax Payable** field, specify the account for tax payable.
5. In the **Payment offset account** field, specify corresponding account for
    tax payable.

> [!NOTE] 
> This Russia-specific field is used when the **Fixed offset posting** option is turned on (see the table earlier in this article for a posting example).

6. Specify the appropriate accounts in the usual way for the following fields:

- **Sales Tax Receivable**
- **Deferred tax**
- **Incoming tax payment**
- **Use tax expense**
- **Use tax payable**
- **Vendor cash discount**
- **Customer cash discount**

> [!NOTE]
> Accounts in the **Posting type** field must have a **Tax** value. If the accounts don't have this value, you can add it on the **Posting validation** tab on the **Main accounts** page.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
