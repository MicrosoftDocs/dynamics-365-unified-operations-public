---
# required metadata

title: Intra-community VAT for Spain
description: This topic provides information about the functionality for intra-community value-added tax (VAT). It explains how to turn on the functionality, calculate and print intra-community VAT amounts, and review intra-community VAT amounts that have been posted.
author: Anasyash
manager: AnnBe
ms.date: 04/25/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: VendFormletterParameters, VendParameters, TaxTrans
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 271523
ms.search.region: Spain
# ms.search.industry: 
ms.author: anasyash
ms.dyn365.ops.version: Version 1611
ms.search.validFrom: 2016-11-30

---

# Intra-community VAT for Spain
[!include [banner](../includes/banner.md)]

This topic provides information about the functionality for intra-community
value-added tax (VAT). It explains how to turn on the functionality, calculate
and print intra-community VAT amounts, and review intra-community VAT amounts
that have been posted.

Information about intra-community value-added tax (VAT) can be calculated and
posted automatically. When you post a European Union (EU) vendor invoice, two
VAT transactions are created. One VAT transaction is created for payable sales
tax, and the other VAT transaction is created for receivable sales tax. Before
you can use the intra-community VAT functionality, you must enable
the **Intra-community VAT** option on the **Ledger and sales tax** tab (Fasttab
**Sales tax)** of the **Accounts payable parameters** page (**Accounts payable
\> Setup \> Accounts payable parameters**).

## Calculating intracommunity VAT for purchase transactions
To calculate intra-community VAT for purchase transactions, you must have two sales tax codes that have the same tax percentage. However, one code must have a positive tax percentage, and the other code must have a negative tax percentage. You must also have a sales tax group that contains both a positive sales tax code and a negative sales tax code. 
Select the **Intra-community VAT** check box for the line that has a negative sales tax code. 

## Printing intracommunity VAT on a purchase invoice
To print intra-community VAT on a purchase invoice, enable the **Print EU sales tax on Spanish invoices** option on the **Invoice** tab of the **Form setup** page (**Accounts payable** \> **Setup** \> **Forms** \> **Form setup**).

## Printing invoices that have intracommunity VAT amounts
To print purchase invoices and intra-community invoices that have intra-community VAT amounts, on the vendor invoice page, on the **Process** tab, click **Print setup** &gt; **Print options**. In the **Print options** dialog box, enable the **Print invoice** and **Print intra-community invoice** options.

> [!NOTE]
> vendor’s country must be set up as EU member state (**Tax \> Setup \>
Foreign trade \> Foreign trade parameters Country/region properties tab**).

## Reviewing posted intracommunity VAT amounts
To review the intra-community VAT amounts that have been posted, run the Posted
sales tax query (**Tax** \> **Inquiries and reports** \> **Sales tax
inquiries** \> **Posted sales tax**). On the **Posted sales tax** page, on
the **General** tab, if the **Intra-community VAT** check box is selected, the
tax transaction is an intra-community VAT transaction. Spanish VAT books must be
set up so that posted payable and receivable VAT transactions are reflected in
the appropriate sections. To set up Spanish VAT books,
click **Tax** \> **Setup** \> **Sales tax** \> **Spanish VAT books**. For more
information, see [Report 340 for
Spain](https://github.com/MicrosoftDocs/Dynamics-365-Operations/blob/master/articles/finance/localizations/emea-esp-report-340.md).

## Example

The following example shows how you can set up sales tax codes, post and print
transaction for Intra-community VAT.

1.  Go to **Accounts payable \> Setup \> Accounts payable parameters**. On
    FastTab **Sales tax** on the **Ledger and sales tax** tab set
    the **Intra-community VAT** option to **Yes**.

![](media/1_Intra-community_VAT.png)

2.  Go to **Tax \> Indirect taxes \> Sales tax \> Sales tax codes** and create a
    pair of sales tax codes with the same tax percentage for each tax rate. One
    code must have a positive tax percentage, and the other code must have a
    negative tax percentage. For codes with negative tax percentage on
    **Calculation** FastTab **Allow negative sales tax percentage** option must
    be set to **Yes**.

| **Sales tax code** | **Percentage** | **Description**                       |
|--------------------|----------------|---------------------------------------|
| EU21               | 21             | EU purchases at a rate of 21 percent. |
| EU-21              | -21            | EU purchases at a rate of 21 percent. |
| EU10               | 10             | EU purchases at a rate of 10 percent. |
| EU-10              | -10            | EU purchases at a rate of 10 percent. |
| EU4               | 4             | EU purchases at a rate of 4 percent. |
| EU-4              | -4            | EU purchases at a rate of 4 percent. |

3.  Go to **Tax \> Indirect taxes \> Sales tax \> Sales tax groups** and create
    Sales tax group **EU** on **Setup** FastTab add the following codes:

| **Sales tax code** | **Intra-community VAT** |
|--------------------|-------------------------|
| EU21               | No                      |
| EU-21              | Yes                     |
| EU10               | No                      |
| EU-10              | Yes                     |
| EU4                | No                      |
| EU-4               | Yes                     |

3.  Go to **Tax \> Indirect taxes \> Sales tax \> Item sales tax groups** and
    create the following Item sales tax groups:

| **Item sales tax group** | **Sales tax codes** |
|--------------------------|---------------------|
| 21                       | EU21, EU-21         |
| 10                       | EU10, EU-10         |
| 4                        | EU4, EU-4           |

4.  Go to **Accounts payable \> Invoices \> Invoice journal** and create the
    following line.

| **Date**        | **Transaction type** | **Amount net** | **VAT amount** | **Sales tax codes** |
|-----------------|----------------------|----------------|----------------|---------------------|
| January 1, 2020 | Customer invoice     | 1000           | 210            | EU21 EU-21          |

5.  Verify that in **Sales tax** there are two lines.

    ![](media/2_Sales_tax.png)

6.  Select **Post** to post the transaction. Select **OK**.
