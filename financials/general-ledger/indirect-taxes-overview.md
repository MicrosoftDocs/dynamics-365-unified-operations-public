---
# required metadata

title: Sales tax overview
description: This article provides an overview of the sales tax system. It explains the elements of the sales tax setup and how they work together.
author: ShylaThompson
manager: AnnBe
ms.date: 2015-12-01 16 - 58 - 30
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

ms.search.form: TaxAuthority, TaxPeriod, TaxTable
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: ShylaThompson
ms.search.scope: AX 7.0.0, Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 13111
ms.assetid: fe5fdc7f-9834-49fb-a611-1dd9c289619d
ms.search.region: Global
# ms.search.industry: 
ms.author: vstehman
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Sales tax overview

This article provides an overview of the sales tax system. It explains the elements of the sales tax setup and how they work together.

Overview
--------

The sales tax framework supports many types of indirect taxes, such as sales tax, value-added tax (VAT), goods and services tax (GST), unit-based fees, and withholding tax. These taxes are calculated and documented during purchase and sales transactions. Periodically, they must be reported and paid to tax authorities. The following diagram shows the entities of the tax setup and how they are related. [![TaxOverview](./media/taxoverview1-300x209.jpg)](./media/taxoverview1.jpg) For every sales tax that a company must account for, a sales tax code must be defined. A sales tax code stores the tax rates and calculation rules for the sales tax. Every sales tax code must be linked to a sales tax settlement period. Sales tax settlement periods define the intervals at which sales tax must be reported and paid to the sales tax authority. Every sales tax settlement period must be assigned to a sales tax authority. A sales tax authority represents the entity that sales tax is reported and paid to. It also defines the layout for the sales tax report. Sales tax authorities can be related to vendor accounts. Every sales tax code must also be linked to a ledger posting group. A ledger posting group specifies the main accounts that amounts for the sales tax codes will be posted to. Optional sales tax reporting codes can also be defined. These can be assigned on sales tax codes for the various amount types that are calculated for the sales tax code. The **Sales tax payment by code** report shows totals per pales tax reporting code for a given sales tax settlement period and interval. Every transaction that sales tax needs to be calculated and posted for must have a sales tax group and an item sales tax group. Sales tax groups are related to the party (for example, customer or vendor) of the transaction, whereas item sales tax groups are related to the resource (for example, item or procurement category) of the transaction. Tax groups contain a list of tax codes. The tax codes that are present in both the sales tax group and item sales tax group for a transaction are the tax code that apply to that transaction. The following table describes the entities and the sequence for the tax setup.

| Setup activity                                                  | Required/Optional and description                                                                                                                                                                                                                                                                                         |
|-----------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Create main accounts.                                           | Required. Before you can set up the sales tax functionality, the main accounts that the company uses to pay and record taxes must be created.                                                                                                                                                                             |
| Set up ledger posting groups for sales tax.                     | Required. Ledger posting groups define the main accounts for recording and paying sales taxes.                                                                                                                                                                                                                            |
| Set up sales tax authorities.                                   | Required. Sales tax authorities are the entities that tax must be reported and paid to.                                                                                                                                                                                                                                   |
| Set up sales tax settlement periods.                            | Required. Sales tax settlement periods contain information about when and how often sales tax must be reported and paid. They are related to a sales tax authority.                                                                                                                                                       |
| Set up sales tax reporting codes.                               | Optional. Sales tax reporting codes can be assigned to sales tax codes to report amounts for multiple sales tax codes under one sales tax reporting code.                                                                                                                                                                 |
| Set up sales tax codes.                                         | Required. Sales tax codes contain the tax rates and calculation rules for each sales tax. Sales tax codes are related to a sales tax settlement period and a ledger posting group.                                                                                                                                        |
| Set up sales tax groups.                                        | Required. Sales tax groups contain a list of sales codes that apply for the party (customer or vendor) of a transaction. For a given transaction, the intersection of sales tax codes in the sales tax group and the item sales tax group determines the sales tax codes that apply to that transaction.                  |
| Set up item sales tax groups.                                   | Required. Item sales tax groups contain a list of sales codes that apply for the resource (product, service, and so on) of a transaction. For a given transaction, the intersection of sales tax codes in the sales tax group and the item sales tax group determines the sales tax codes that apply to that transaction. |
| Set up sales tax parameters on the application parameter pages. | Required. Different areas, such as General ledger, Accounts receivable, and Accounts payable, must set up parameters for correct calculation of indirect taxes. Although most of these parameters have default values, they must be modified to fit each company's requirements.                                          |

## Sales tax on transactions
On every transaction (sales/purchase document lines, journals, and so on), you must enter a sales tax group and an item sales tax group to calculate sales tax. Default groups are specified in master data (for example, customer, vendor, item, and procurement category), but you can manually change the groups on a transaction if you must. Both groups contain a list of sales tax codes, and the intersection of the two lists of sales tax codes determines the list of applicable sales tax codes for the transaction. On every transaction, you can look up the calculated sales tax by opening the **Sales tax transaction** page. You can look up the sales tax for a document line or for the whole document. For certain documents (for example, vendor invoice and general journals), you can adjust the calculated sales tax if the original document shows deviant amounts.

## Sales tax settlement and reporting
Sales tax must be reported and paid to tax authorities at regulated intervals (monthly, quarterly, and so on). Microsoft Dynamics 365 for Operations provides functionality that lets you settle tax accounts for the interval and offset the balances to the tax settlement account, as specified in the ledger posting groups. You can access this functionality on the **Settle and post sales tax** page. You must specify the sales tax settlement period that sales tax should be settled for. After the sales tax has been paid, the balance on the sales tax settlement account should be balanced against the bank account. If the sales tax authority that is specified on the sales tax settlement period is related to a vendor account, the sales tax balance is posted as an open vendor invoice and can be included in the regular payment proposal.

## Conditional sales tax
Conditional sales tax is a sales tax that is paid proportionally to the actual amount that is paid on an invoice. Conversely, standard sales tax is calculated at invoicing time. Conditional sales tax must be paid to the sales tax authority when the payment is posted, not when the invoice is posted. When the invoice is posted, the transaction must be reported on the sales tax book report. However, the transaction must be excluded from the sales tax payment report. If you select the Conditional sales tax check box in the General ledger parameters form, no sales tax can be deducted until you have paid the invoice. This is a legal requirement in some countries/regions.
| **Note**                                                                                                                                                                        |
|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| When you select the Conditional sales tax check box, you must set up sales tax codes and sales tax groups, and also create ledger posting groups, to support the functionality. |

###  Example

You settle sales taxes each month. On June 15, you create a customer invoice of 10,000, plus sales tax.
-   The sales tax is 25 percent, or 2,500.
-   The invoice payment is due July 30.

You typically would have to settle and pay 2,500 to the tax authority when the invoice is posted in June, even though you have not received the payment from the customer. However, if you are using a conditional sales tax, you settle with the tax authority when you receive the payment from the customer on July 30.



See also
--------

[Set up sales tax authorities](http://ax.help.dynamics.com/en/wiki/set-up-sales-tax-authorities/)

[Set up sales tax codes](http://ax.help.dynamics.com/en/wiki/set-up-sales-tax-codes)

[Set up sales tax groups and item sales tax group](http://ax.help.dynamics.com/en/wiki/set-up-sales-tax-groups-and-item-sales-tax-groups/)

[Create a sales tax payment](http://ax.help.dynamics.com/en/wiki/create-a-sales-tax-payment/)

