---
title: Intra-community VAT for Spain
description: Learn how to enable and use the intracommunity value-added tax (VAT) functionality in Microsoft Dynamics 365 Finance.
author: AdamTrukawka
ms.author: atrukawk
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 07/11/2025
ms.reviewer: johnmichalak
ms.search.region: Spain
ms.search.validFrom: 2016-11-30
ms.search.form: VendFormletterParameters, VendParameters, TaxTrans
---

# Intra-community VAT for Spain

[!include [banner](../../includes/banner.md)]

This article explains how to enable and use the intracommunity value-added tax (VAT) functionality in Microsoft Dynamics 365 Finance, including how to turn on the functionality, calculate and print intracommunity VAT amounts, and review posted intracommunity VAT amounts.

Information about the intracommunity value-added tax (VAT) can be calculated and posted automatically. When you post a European Union (EU) vendor invoice, two VAT transactions are created. One VAT transaction is created for payable sales tax, and the other VAT transaction is created for receivable sales tax. 

Before you can use the intracommunity VAT functionality, you must enable it.

To enable the intracommunity VAT functionality, follow these steps.

1. In Dynamics 365 Finance, go to the **Accounts payable parameters** page (**Accounts payable** \> **Setup** \> **Accounts payable parameters**).
1. Select the **Ledger and sales tax** tab.
1. On the **Sales tax** FastTab, enable the the **Intra-community VAT** option.

## Calculate intracommunity VAT for purchase transactions

To calculate intracommunity VAT for purchase transactions, you must have two sales tax codes that have the same tax percentage. However, one code must have a positive tax percentage, and the other code must have a negative tax percentage. You must also have a sales tax group that contains both a positive sales tax code and a negative sales tax code. 

To calculate intracommunity VAT for purchase transactions, select the **Intra-community VAT** checkbox for the line that has a negative sales tax code. 

## Print intracommunity VAT on a purchase invoice

To print the intracommunity VAT on a purchase invoice, follow these steps. 

1. In Dynamics 365 Finance, go to the **Form setup** page (**Accounts payable** \> **Setup** \> **Forms** \> **Form setup**).
1. On the **Invoice** tab, enable the **Print EU sales tax on Spanish invoices** option.

## Print invoices that have intracommunity VAT amounts

To print purchase invoices and intracommunity invoices that have intracommunity VAT amounts, follow these steps. 

1. In Dynamics 365 Finance, go to the vendor invoice page.
1. On the **Process** tab, select **Print setup** \> **Print options**.
1. In the **Print options** dialog, enable the **Print invoice** and **Print intracommunity invoice** options.

> [!NOTE]
> You must set up a vendor's country/region as an EU member state on the **Tax** \> **Setup** \> **Foreign trade \> Foreign trade parameters Country/region properties** tab.

## Review posted intracommunity VAT amounts

To review posted intracommunity VAT amounts, follow these steps.

1. In Dynamics 365 Finance, go to **Tax** \> **Inquiries and reports** \> **Sales tax inquiries** \> **Posted sales tax**.
1. Run the **Posted sales tax** query.
1. On the **General** tab, if the **Intra-community VAT** checkbox is selected, the tax transaction is an intracommunity VAT transaction.
1. You must set up Spanish VAT books so that posted payable and receivable VAT transactions are reflected in the appropriate sections. To set up Spanish VAT books, go to **Tax** \> **Setup** \> **Sales tax** \> **Spanish VAT books**. Learn more at [Report 340 for Spain](emea-esp-report-340.md).

## Example

The following example procedure shows you how to set up sales tax codes and post and print transactions for Intra-community VAT.

1. In Dynamics 365 Finance, go to **Accounts payable** \> **Setup** \> **Accounts payable parameters**. 
1. On the **Ledger and sales tax** tab, on the **Sales tax** FastTab, set the **Intra-community VAT** option to **Yes**.

    ![Accounts payable parameters page, Ledger and sales tax tab, Intra-community VAT field.](../media/1_Intra-community_VAT.png)

1. Go to **Tax** \> **Indirect taxes** \> **Sales tax** \> **Sales tax codes** and create a pair of sales tax codes with the same tax percentage for each tax rate. One code must have a positive tax percentage, and the other code must have a negative tax percentage. For codes with negative tax percentage, on the **Calculation** FastTab, set the **Allow negative sales tax percentage** option to **Yes**.

    | **Sales tax code** | **Percentage** | **Description**                       |
    |--------------------|----------------|---------------------------------------|
    | EU21               | 21             | EU purchases at a rate of 21 percent. |
    | EU-21              | -21            | EU purchases at a rate of 21 percent. |
    | EU10               | 10             | EU purchases at a rate of 10 percent. |
    | EU-10              | -10            | EU purchases at a rate of 10 percent. |
    | EU4               | 4             | EU purchases at a rate of 4 percent. |
    | EU-4              | -4            | EU purchases at a rate of 4 percent. |

1. Go to **Tax** \> **Indirect taxes** \> **Sales tax** \> **Sales tax groups** and create a new sales tax group called **EU**.
1. On the **Setup** FastTab, add the following codes.

    | **Sales tax code** | **Intra-community VAT** |
    |--------------------|-------------------------|
    | EU21               | No                      |
    | EU-21              | Yes                     |
    | EU10               | No                      |
    | EU-10              | Yes                     |
    | EU4                | No                      |
    | EU-4               | Yes                     |

1. Go to **Tax** \> **Indirect taxes** \> **Sales tax** \> **Item sales tax groups** and create the following item sales tax groups.

    | **Item sales tax group** | **Sales tax codes** |
    |--------------------------|---------------------|
    | 21                       | EU21, EU-21         |
    | 10                       | EU10, EU-10         |
    | 4                        | EU4, EU-4           |

1. Go to **Accounts payable** \> **Invoices** \> **Invoice journal** and create the following line.

    | **Date**        | **Transaction type** | **Amount net** | **VAT amount** | **Sales tax codes** |
    |-----------------|----------------------|----------------|----------------|---------------------|
    | January 1, 2020 | Customer invoice     | 1000           | 210            | EU21 EU-21          |

1. Verify that there are two lines in the **Sales tax transactions** list.

    ![Sales tax transaction lines.](../media/2_Sales_tax.png)

1. Select **Post** to post the transaction, and then select **OK**.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
