---
# required metadata

title: Sales tax specification by ledger transaction report
description: This article explains how to use this report to show and print information about ledger transactions for which sales tax is calculated.
author: ericwang
manager: Ann Beebe
ms.date: 08/19/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: TaxTable
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
ms.search.scope: Core, Operations

# ms.tgt_pltfrm: 
ms.custom: 4464
ms.assetid: 5f89daf1-acc2-4959-b48d-91542fb6bacb
ms.search.region: Global
# ms.search.industry: 
ms.author: vstehman
ms.search.validFrom: 2019-08-19
ms.dyn365.ops.version: 10.0.6

---

This article explains how to use this report to show and print information about ledger transactions for which sales tax is calculated.

## Tax Account and Non-Tax Account

This report will show tax transaction for both tax account and non-tax account. Definition of the two accounts is:

- Tax account: when tax transaction is posted, main account on "Sales Tax" journal line is tax account. e.g. sales tax payable, sales tax receivable
- Non-tax account: when tax transaction is posted, main account on original transaction is non-tax account. e.g. revenue account, expense account

In this report, report columns "Origin", "Sales tax receivable", "Sales tax payable" amount will show for non-tax account and will show 0 for tax account


## How to filter the data on this report

When you generate this report, the following default parameters are displayed. You can use these parameters to filter the data that will be displayed on the report.

|Field|Description|
|-------|-----------------|
|Main accounts only|Tax transaction date range|
|From/To Main account|Main account range|
|From/To sales tax code|Sales tax code range|
|Grouping|Report is grouped by ledger account or sales tax code|
|Subtotal by sales tax code|Select this check box to show subtotal by sales tax code|
|Totals only|Select this check box to show totals only|
|Main accounts only|Select this check box to print only main accounts on the report|

