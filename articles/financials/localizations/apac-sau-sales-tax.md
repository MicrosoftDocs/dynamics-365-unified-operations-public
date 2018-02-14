---
# required metadata

title: Sales tax for Saudi Arabia
description: This topic provides information about sales taxes for Saudi Arabia.           
author: ShylaThompson
manager: AnnBe
ms.date: 10/05/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: shylaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Saudi Arabia
# ms.search.industry: 
ms.author: shylaw
ms.search.validFrom: 
ms.dyn365.ops.version: 

---

# Sales tax for Saudi Arabia

[!include[banner](../includes/banner.md)]

This topic walks you through setting up sales taxes for Saudi Arabia. For information about regulatory requirements for Saudi Arabia, see [VAT for Saudi Arabia](https://www.vat.gov.sa/). 

## Sales tax codes, sales tax groups, and item sales tax groups

- [Sales tax groups and item sales tax groups](../general-ledger/tasks/set-up-sales-tax-groups-item-sales-tax-groups.md)
- [Sales tax codes](../general-ledger/tasks/set-up-sales-tax-codes.md)

Tax type with values added for VAT type: Standard VAT, Reduced VAT, VAT 0%
New value in Country/ Region field: GCC
Translation of sales tax description (button Tax directive)

 
You may set up, for example, one group named Domestic and include two sales tax codes in it (one sales tax code with rate 5% and another with rate 0%) and set up two item sales tax groups. Each group includes only one sales tax code.

Sales tax group may be set up in Customer/ Vendor by default and Item sales tax group may be set up in Items by default when a user creates sales/purchase order the system transfers Sales tax group from customer to the header and lines and transfers Item sales tax group from item to the lines. But a user may change groups both in the header and in lines.

If a sales tax code is included in two groups (sales tax group and item sales tax group) in the line, then when posting the invoice, the system will create sales tax transaction with this sales tax code and calculate sales tax. If there is no intersection of sales tax codes in groups of line, then sales tax transaction will not be created

The following diagram demonstrates one way that sales tax groups can be set up and how sales tax transactions and sales tax calculation are defined given that setup.  

![Sales tax groups diagram](media/apac-sau-sales-tax-groups-diagram.png)

In every sales tax code you should fill in (main sales tax settings): 
1.	Type of tax (Standard VAT or VAT 0%)
2.	Settlement period
3.	Ledger posting codes
4.	Calculation (firstly the settings by default may be used)
5.	Report setup/ Report setup – Credit note
When you select Settlement period the system automatically fills in Report layout field in the Report setup/ Report setup – Credit note areas.

Tax > Setup > Sales tax > Sales tax groups 
And
Tax > Indirect taxes > Sales tax > Item sales tax groups
It is up to company accounting how it will be include sales tax codes in Sales tax groups and Item sales tax groups.
Different Sales tax group settings may be for different operations. 
For examples, for export operations, you may select **Exempt** check box and Select **Exempt code**. In this case, the system will create sales tax transaction with VAT equal to zero. But with the rate equal to 5% (Value field in sales tax transaction). It may be useful for analysis of export operations by VAT rates.   

The similar settings may be done for other exemption operations. 

For import operations from third countries (VAT is paid at customs) you may use the following setting: 

When you post an invoice with such setting, the system creates sales tax transaction with Use tax direction, but sales tax is not included in vendor liability. Sales transactions with Use tax direction are not taken into account when settling and posting sales taxes (see Settle and post sales tax), and depending on ledger posting setting (see Ledger posting groups) the system creates ledger transactions for this sales tax (see the screenshot below).
This setting allows you to analyze purchases from third countries by VAT rates.
Example of sales tax transactions with different values of sales tax direction.


## Reverse charges


### Enable reverse charge
You can enable the reverse charge functionality by setting the **Reverse charge** option to **Yes** on the **General ledger parameters** page.

### Create sales tax codes for reverse charge operations
Create sales tax codes for reverse charge operations (for purchase operations). (**Tax** > **Indirect taxes** > **Sales tax** > **Sales tax codes**) 

It is necessary to set up two sales tax codes for reverse charge operations (for purchase operations): one with positive rate and another with negative rate.  You may fill in negative rate (SALES TAX CODE/ Value button) if Negative sales tax percentage check box has been selected in the Sales tax codes form (see the screenshot below). 
Tax > Indirect taxes > Sales tax > Sales tax codes

![Sales tax codes for reverse charge](media/apac-sau-sales-tax-codes-reverse-charge.png)

### Create a sales tax group for reverse charge
Create a sales tax group that has the **Reverse charge** check box selected for a sales tax code with a negative rate. The two sales tax codes that you created in [Create sales tax codes for reverse charge operations](#create-sales-tax-codes-for-reverse-charge-operations) should be added to a sales tax group and to an item sales tax group.  See how sales tax functionality works in Sales tax codes, Sales tax group and Item sales tax groups
Tax > Indirect taxes > Sales tax > Sales tax groups 

![Reverse charge selection on sales tax group](media/apac-sau-sales-tax-group-reverse-charge.png)


### Sales tax transactions with reverse charges
If the **Reverse charge** check box is selected in the sales tax group, sales tax transactions are created when you posting an invoice. One transaction includes sales tax receivable and another transaction includes a sales tax payable direction. 

Tax > Inquiries and reports > Sales tax inquiries > Posted sales tax

![Posted sales tax](media/apac-sau-posted-sales-tax.png)

## Printing invoices

When you print an invoice, if your language is different than the language specified for the current legal entity, two invoices will be generated, one in Arabic and the other in the language that you selected on the **User options** page.

## Sales tax payment by report code report

The diagram below shows how data may be collected in the **Sales tax payment by report code** report. 
It is important to note that data is collected on the base of sales tax transactions. Therefore, if an invoice does not include tax transactions then this invoice will not be included in the report.  One report code may be selected in several sales tax codes and several report codes may be selected in one sales tax code in different fields. 

![Sales tax payment by report code](media/apac-sau-sales-tax-diagram.png)

### Report setup
Consider the following before you generate the **Sales tax payment by report code** report:

- 

### Sales tax authorities

When you set up sales tax authorities pay attention to the **Report layout**
field. When you create a new sales tax code and select **Settlement period,**
the system fills in the corresponding field with the value from sales tax
authority, which related to Sales tax settlement period selected in **Settlement
period** field.

*Tax \> Indirect taxes \> Sales tax \> Sales tax authorities*

![](media/0f5ae5241dbbcf66b3290a2f501eed85.png)

### Sales tax reporting codes

You may create report codes in details which are necessary for analysis (for
example, details of legislation return and/or data disclosure). You may consider
this table only as an example.

*Tax \> Setup \> Sales tax \> Sales tax reporting codes*

![](media/1f9ea5e313eddd40083b396e5d6a1a08.png)

### Sales tax codes

To include sales tax transactions in **Sales tax payments by report code**
report, it is necessary to select report codes in the corresponding fields. in
the **Report setup** and **Report setup – Credit note** areas in **Sales tax
code** form.

*Note*: you may input Reporting codes in the sales tax code either before
posting tax transactions or after posting tax transactions.

*Tax \> Indirect taxes \> Sales tax \> Sales tax codes*

![](media/2191347efca160fb97f79dbbb4eadd68.png)

### Run **Sales tax payment by code** report

To run this report, please, open

*Tax \> Inquiries and reports \> Sales tax reports \> Sales tax payment by code*

The system collects data from sales tax transactions on **Report layout**
specified in dialog form.

![](media/95b43ad71006eb64365cff8103b09f8c.png)

Example of the report:

![](media/2932e4bb2bbf69130cf32d043a6f6601.png)

## Validate previously posted sales tax payments

*Tax \> Declarations \> Sales tax \> Report sales tax for settlement period*

## Post sales tax payment

[Create a sales tax payment](../general-ledger/tasks/create-sales-tax-payment.md)


## VAT returns



[FAQ: VAT returns (English)](https://www.vat.gov.sa/en/e-services/vat-returns)
[FAQ: VAT returns (Arabic)](https://www.vat.gov.sa/ar/e-services/vat-returns)

