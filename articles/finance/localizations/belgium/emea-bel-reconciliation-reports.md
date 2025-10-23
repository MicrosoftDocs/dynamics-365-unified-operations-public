---
title: VAT reconciliation reports for Belgium
description: Learn about the standard reports that Microsoft Dynamics 365 Finance provides to help you with the INTERVAT tax declaration and reconciliation analysis.
author: liza-golub
ms.author: egolub
ms.topic: article
ms.custom: 
  - bap-template
ms.date: 10/01/2025
ms.reviewer: johnmichalak
ms.search.region: Belgium
ms.search.validFrom: 2016-05-31
ms.search.form: TaxReportExtraFieldsBE
ms.dyn365.ops.version: AX 7.0.1
---

# VAT reconciliation reports for Belgium

[!include [banner](../../includes/banner.md)]

Dynamics 365 Finance has evolved into purpose-built applications to help you manage specific business functions. For more information about these changes, see [Dynamics 365 Licensing Guide](https://go.microsoft.com/fwlink/?LinkId=866544).

This article describes the standard reports that are provided to help you with value-added tax (VAT) declaration and reconciliation analysis.

Based on the sales tax entries for selected periods, the Belgian periodic VAT declaration combines sales tax amounts into boxes by sorting, splitting, and totaling information in specific ways. Therefore, control reports are required, so that the amounts in the VAT declaration can be verified in detail. This article describes the reports that include details of the data in the VAT declaration and can be used to support the process of VAT declaration reconciliation. For more information, see [VAT declaration](../emea-bel-vat-declaration-belgium.md).

## Sales tax list - Belgium
Use the **Sales tax list - Belgium** report to view information about posted sales tax. The report gives details about the sales tax code, name, ledger account, account name, quantity, amount inclusive of sales tax, origin, and tax amount. The parameters for this report give you lots of flexibility. You can get a very precise report by selecting the voucher, date, or sales tax code parameters. Use a filter to set up report parameters.

To print the **Sales tax list - Belgium** report, go to **Tax** \> **Inquiries and reports** \> **Sales tax reports** \> **Sales tax list - Belgium**.

![Sales tax list generated report.](../media/2_Sales_tax_list.png)

## Sales tax transactions - Details  Belgium
Use the **Sales tax transactions - Details - Belgium** report to view and print information about posted sales tax transactions for a specified period and a specific range of sales tax codes. The transactions are listed by sales tax code. For each transaction, you can see the customer or vendor, the voucher number, the account that the sales tax base amount (origin) is posted to, the sales tax base amount, the amount inclusive of sales tax, the sales tax amount, the sales tax charge, and the sales tax direction. The amounts are summed for each tax code. The amounts for the Sales tax receivable and Sales tax payable sales tax directions are summed in a grand total. The report also lists sales tax codes that have other sales tax directions, such as Use tax.

To print the **Sales tax transactions - Details - Belgium** report, go to **Tax** \> **Inquiries and reports** \> **Sales tax reports** \> **Sales tax transactions - Details - Belgium**.

![Sales tax transactions details Belguim generated report.](../media/3_Sales_tax_transactions_details.png)

## Sales tax transactions - Belgium

The **Sales tax transactions - Belgium** report shows the Belgian sales tax transactions that have been posted. The report gives details about the date, voucher, sales tax code, name, source, invoice, amount, net VAT amount in the company currency, net VAT amount in the voucher currency and voucher currency.

You can sort the report by voucher, date, voucher currency, sales tax code, and source. The **Voucher**, **Sales tax code**, and **Voucher currency** fields provide drill-through. The parameters for this report give you lots of flexibility. You can get a very precise report by selecting the voucher, date, or sales tax code parameters. Use a filter to set up report parameters.

To print the **Sales tax transactions - Belgium** report, go to **Tax** \> **Inquiries and reports** \> **Sales tax reports** \> **Sales tax transactions - Belgium**.

![Sales tax transactions generated report.](../media/5_Sales_tax_transactions.png)

## Sales tax by customer - Belgium

Control reports are required, so that the amounts in the VAT declaration can be verified in detail on a customer. For each customer account and sales tax code, the following information is printed:

-   Customer account number
-   Sales tax code
-   Amount inclusive of sales tax
-   Origin
-   Sales tax amount
-   Total per customer account
-   Grand total for all customer accounts

This report can be generated as follows:

-   For one customer account or all customer accounts
-   For one sales tax code or all sales tax codes
-   For one specific date or a range of dates

The parameters for this report give you lots of flexibility. You can get a very precise report by selecting the customer account, date, or sales tax code parameters. Use a filter to set up report parameters more precisely.  To print the **Sales tax** **by customer - Belgium** report, click **Tax** &gt; **Inquiries and reports** &gt; **Sales tax reports** &gt; **Sales tax** **by customer - Belgium**.

![Belgian sales tax by customer generated report.](../media/6_Sales_tax_by_customer.png)

## Sales tax by vendor - Belgium

Control reports are required, so that the amounts in the VAT declaration can be verified in detail on a vendor. For each vendor account and sales tax code, the following information is printed:

-   Vendor account number
-   Sales tax code
-   Amount inclusive of sales tax
-   Origin
-   Sales tax amount
-   Total per vendor account
-   Grand total for all vendor accounts

This report can be generated as follows:

-   For one vendor account or all vendor accounts
-   For one sales tax code or all sales tax codes
-   For one specific date or a range of dates

The parameters for this report give you lots of flexibility. You can get a very precise report by selecting the vendor account, date, or sales tax code parameters. Use a filter to set up report parameters more precisely. 
To print the **Sales tax** **by vendor - Belgium** report, click **Tax** &gt; **Inquiries and reports** &gt; **Sales tax reports** &gt; **Sales tax** **by vendor - Belgium**.

![Belgian sales tax by vendor generated report.](../media/7_Sales_tax_by_vendor.png)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
