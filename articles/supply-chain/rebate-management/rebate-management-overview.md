---
# required metadata

title: Rebate management module overview
description: This topic provides an overview of the Rebate management module for Microsoft Dynamics 365 Supply Chain Management.
author: sherry-zheng
ms.date: 02/19/2021
ms.topic: overview
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: [Operations AOT form name to tie this topic to]
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 

ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: chuzheng
ms.search.validFrom: 2021-02-19
ms.dyn365.ops.version: 10.0.18
---

# Rebate management module overview

[!include [banner](../includes/banner.md)]

You can use the **Rebate management** module to create contracts, deals, or agreements between your business and its customers or vendors, so that you can calculate rebates, deductions, and royalties. Rebate management tracks and maintains rebate and deduction transactions in a central location where users can effectively create, review, and process them.

Rebate management supports the creation, maintenance, and processing of *rebates*. A rebate is the return of part of the purchase price by a seller or a buyer. Rebates are typically based on the purchase of a specific quantity or value of goods during a specific period. Unlike discounts, rebates are done after the purchase amount is fully invoiced.

Rebate management also supports *deductions*. A deduction is compensation, a consideration, or a fee that is paid either for a license or the privilege to use intellectual property such as a brand, copyright, or patent, or for the privilege to use a natural resource for a purpose such as for fishing, hunting, or mining. Deductions are usually calculated as a percentage of the revenue or profit from realized use. The more the intellectual property or natural resource is used, the greater the deduction that is realized.

Additionally, Rebate management supports customer *royalties*. Royalties are payments that one party makes to the licensee or franchisee for the right to use an asset.

Rebate management lets you define posting profiles for provisions, rebates, and write-offs. Furthermore, the postings can be defined for a specific customer or vendor. In this way, deals that don't apply to all customer or vendor scenarios can be tracked via postings.

Rebate transactions are automatically generated, based on the calculation method that is selected and scheduled in batch jobs. Additionally, you can set up workflows to manage, review, and approve agreements.

## Basis calculation

Customer rebates, customer royalties, and vendor rebates can all use a different basis, depending on your business requirements:

- Customer rebates can be based on sales orders, delivery notes, or invoices.
- Customer royalties can be based on sales orders, delivery notes, or paid invoices.
- Vendor rebates can be based on either purchase orders or sales orders. They can be calculated based on products that are purchased from the rebate vendor and sold to customers via sales invoices.

## Flexible calculations

Rebate calculation periods are available for both customer deals and vendor deals. A calculation period defines the length of the deal, the calculation frequency, and the calculation period. The rebates can be accrued based on the sales order quantities or amounts for qualified products during the rebate period.

For each agreement calculation, any of the following periods can be set:

- Invoice
- Day
- Week
- Month
- Quarter
- Year
- Customized period
- Any multiple of any of the previously listed periods

The calculation can be applied to individual customers and products, groups of customers and products, or all customers and products. Rebates that have multiple detail lines can have different qualifying date ranges. The provision and claim periods can differ. For example, provisions can be processed every day, whereas claims are processed once per month.

Rebates can be configured based on many different parameters. For example, they can be configured as a percentage, a rate, or a fixed amount. There are four main calculation methods:

- Stepped
- Cumulative
- Rolling
- Total value

Rebate calculation results can also be reduced by other rebates, depending on whether the rebate is set up to calculate based on the net amount.

On the vendor side, rebates that are based on sales orders can calculate the price based on a first in, first out (FIFO) rule, the latest purchase price, the average purchase price, or the sales price.

## Rebate target transactions

The outputs that the rebate deal or agreement generates can be financials or items.

Financial outputs are determined by the payment type that is assigned to the agreement from the posting profile. These outputs can include customer deduction journals, free text invoices, and vendor invoices. For auditing purposes, financial rebate target transactions include a reference to the originating rebate agreement.

Item outputs create a free item sales order for customer rebates and a purchase order for vendor rebates. Item rebate target transactions contain options to determine which rebate reference should be entered on the free item sales order or purchase order.

## Accurate rebate calculations

The combination of the associated deals, the frequency of the calculations, the calculation basis, and the calculation method that is selected determines the accuracy and precision of rebate calculations. Rebate provisions can be used to accrue posted and claimed values.

Provisions can be managed daily, weekly, monthly, or according to a custom period. However, the functionality can allocate or pay the rebate, or receive payment of it, at any defined frequency that is the same length as or longer than the provision frequency. Write-off uses the same frequency as the rebate. Users can easily adjust a plan or payment amounts at any time during the payout.

Users no longer have to handle deals or provisions in two steps. Provisions and write-offs are posted directly to the ledger. Additionally, credit notes can be created automatically. Therefore, there is full integration with accounts payable and accounts receivable. During processing, the calculations can consider settlement discounts, paid invoices, trade discounts, and existing credit notes to ensure that amounts and values are accurately calculated.

When rebates are calculated, the process creates transactions that can be reviewed before posting occurs. A separate process posts rebate management transactions. A journal, credit note, or debit transaction can then be created during posting to proposed transactions. Reporting statements and transaction listings can be obtained to ensure compliance, effectiveness, and transparency.

## Guaranteed royalty payments

In Rebate management, automatic payment generation enables royalties to be handled quickly and easily, even when guaranteed minimums apply.

## Maximizing spend versus rebates

Vendors and products can be grouped by territory, and different offers can be provided, depending on the country or region of the transaction. When users select products, they can define the items that are included and the number of items that will be used in the rebate settlement.
