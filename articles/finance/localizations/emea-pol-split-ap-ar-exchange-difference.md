---
# required metadata

title: Split the AP/AR realized exchange difference amount into the difference of the invoice net value and the VAT amount
description: This topic provides information about a feature for splitting of the AP/AR realized exchange difference amount into the difference of the invoice net value and the VAT amount in Poland
author: anasyash
manager: 
ms.date: 04/01/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 414136
ms.search.region: Poland
# ms.search.industry: 
ms.author: shylaw
ms.dyn365.ops.version: 
ms.search.validFrom: 2020-04-01

---


# Split the AP/AR realized exchange difference amount into the difference of the invoice net value and the VAT amount

This feature allows you to split the AP/AR foreign currency revaluation amount
into two parts – exchange difference related to net value of invoice (customer
debts and vendor liabilities) and exchange difference related to VAT invoice
amount. You can also post the exchange differences, which are related to the VAT
invoice amount, to a separate ledger account of realized gains/losses.

This feature is available only in legal entities with Polish county context.

## Setup

### Activate the feature


In the **Feature management** workspace, select the feature **(Poland) Split the
AP/AR realized exchange difference amount into the difference of the invoice net
value and the VAT amount** and enable it.

### Set up ledger accounts

You should set up ledger accounts for posting the exchange difference amount
part related to tax amount of invoice.

1.  Go to **Modules \> General ledger \> Currencies \> Currency revaluation
    accounts.** Select the currency code. Select code of legal entity in the
    **Ledger** field.

![A screenshot of a social media post Description automatically generated](media/4ccbaa57f8ad73291cfaab593a3847b8.png)

2.  Select the line with **Realized gain** or **Realized loss** in the
    **Posting** field.

3.  Set up **Main account** in standard way – select ledger account for posting
    of realized exchange difference.

4.  In the field **Sales taxes** select **Expense** to post a part of realized
    exchange difference amount which is related to tax amount of invoice, to a
    separate expense ledger account. Select this expense ledger account in **Tax
    posting account** field.

## Post and settle customer/vendor transactions.

Post and settle documents in standard way.

Exchange difference transaction created during settlement will generate a
voucher where exchange difference amount related to tax amount is posted
separately to a ledger account selected in **Tax posting account** field of
**Currency revaluation accounts** page.

## Examples

Below you can find two examples with resulting ledger transactions.

### Example 1

Make the following settings in DEMF legal entity:

1.  Change country to POL.

2.  Validate that Accounting currency is set up as EUR in **Ledger** page.

3.  Set up currency exchange rates for *Default* exchange rate type:

| **Date**   | **USD** | **EUR** | **Description**    |
|------------|---------|---------|--------------------|
| 01.01.2020 | 100     | 80      | 100 USD for 80 EUR |
| 10.01.2020 | 100     | 90      | 100 USD for 90 EUR |

4.  Set up ledger accounts for realized exchange difference: **Main account**
    and **Tax posting account**

Post the following transactions:

| **Document**                   | **Date**   | **Amount in USD**                | **Amount in EUR**                     | **Voucher**                                                                                               | **Voucher amount** |
|--------------------------------|------------|----------------------------------|---------------------------------------|-----------------------------------------------------------------------------------------------------------|--------------------|
| Customer invoice               | 01.01.2020 | 119 USD, incl. VAT amount 19 USD | 95,20 EUR, incl. VAT amount 15,20 EUR | Debit *Accounts receivable* Credit *Expense* Credit *VAT*                                                 | 95,20 80,00 15,20  |
| Customer payment               | 10.01.2020 | 119 USD                          | 107,10 EUR                            | Debit *Bank* Credit *AR*                                                                                  | 107,10 107,10      |
| Invoice and payment settlement | 10.01.2020 | 0 USD                            | 11,90 EUR                             | Debit *AR* Credit *Exchange difference – main account* Credit *Exchange difference – tax posting account* | 11,90 10,00 1,90   |

Where: 10,00 = 11,90 \* 80,00 / 95,20 (exchange difference related to net value
of invoice)

1,90 = 11,90 – 10,00 (exchange difference related to tax amount of invoice)

### Example 2

In addition to settings in Example 1, make the following settings:

1.  Set up **Bank exchange rate** as *Average* exchange rate type. This rate
    will be used for calculating VAT amounts.

2.  Set up currency exchange rate for *Average* exchange rate type:

| Date       | USD | EUR | **Description**     |
|------------|-----|-----|---------------------|
| 01.01.2020 | 100 | 100 | 100 USD for 100 EUR |
| 10.01.2020 | 100 | 110 | 100 USD for 110 EUR |

Post the following transactions:

| **Document**                   | **Date**   | **Amount in USD**                | **Amount in EUR**                     | **Voucher**                                                                                                                      | **Voucher amount**          |
|--------------------------------|------------|----------------------------------|---------------------------------------|----------------------------------------------------------------------------------------------------------------------------------|-----------------------------|
| Customer invoice               | 01.01.2020 | 119 USD, incl. VAT amount 19 USD | 95,20 EUR, incl. VAT amount 19,00 EUR | Debit *Accounts receivable* Credit *Expense* Credit *VAT* Debit *Accounts receivable tax difference* Credit *VAT tax difference* | 95,20 80,00 15,20 3,80 3,80 |
| Customer payment               | 10.01.2020 | 119 USD                          | 107,10 EUR                            | Debit *Bank* Credit *AR*                                                                                                         | 107,10 107,10               |
| Invoice and payment settlement | 10.01.2020 | 0 USD                            | 11,90 EUR                             | Debit *AR* Credit *Exchange difference – main account* Credit *Exchange difference – tax posting account*                        | 11,90 10,00 1,90            |

Where: 10,00 = 11,90 \* 80,00 / 95,20 (exchange difference related to net value
of invoice)

1,90 = 11,90 – 10,00 (exchange difference related to tax amount of invoice)
