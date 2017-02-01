---
# required metadata

title: Sales tax payments and rounding rules | Microsoft Docs
description: This article explains how the rounding rule setup on the Sales tax authorities works and rounding the sales tax balance during the Settle and post sales tax job.
author: ShylaThompson
manager: AnnBe
ms.date: 2015-09-14 12:24:02
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

keywords: TaxAuthority
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: ShylaThompson
ms.suite: Released- Dynamics AX 7.0.0
# ms.tgt_pltfrm: 
ms.custom: 6134
ms.assetid: 1c6636c3-83f8-4eb6-8bdf-0b1529b6a6b6
ms.region: Global
# ms.industry: 
ms.author: vstehman

---

# Sales tax payments and rounding rules

This article explains how the rounding rule setup on the Sales tax authorities works and rounding the sales tax balance during the Settle and post sales tax job.

Periodically, sales tax needs to be reported and paid to tax authorities. This can be done by running the settle and post sales tax process in the Sales tax page. Sales tax for a period will be settled against the sales tax accounts and the sales tax balance will be posted to the Sales tax settlement account. The sales tax balance, which is posted on the Sales tax settlement account, can be rounded as required by tax authorities by setting up a rounding rule on the Sales tax page. The rounding difference is posted to the Sales tax rounding account that is selected in the Accounts for automatic transactions field in the General ledger. The below example illustrates how the rounding rule on Sales tax authority works.
### Example:

The total sales tax for a period shows a credit balance of -98,765.43. The legal entity collected more sales taxes than it paid. Therefore, the legal entity owes money to the tax authority. The legal entity wants to use a rounding method that rounds the balance to the nearest 1.00. The user who is responsible for sales tax accounting performs the following steps.
1.  Click Tax &gt; Indirect taxes &gt; Sales tax &gt; Sales tax authorities
2.  On the General FastTab, select Normal in the Rounding form field.
3.  In the Round-off field, enter 1.00.
4.  When it is time to pay the sales taxes to the tax authority, open the Settle and post sales tax page. (Click Tax &gt; Declarations &gt; Sales tax &gt; Settle and post sales tax.)
5.  On the sales tax settlement account, the tax liability amount of 98,765.43 is rounded to 98,765.

The following table shows how an amount of 98,765.43 is rounded by using each rounding method that is available in the Rounding form field in the Sales tax authorities page.

| Rounding form option                | Round-off value = 0.01 | Round-off value = 0.10 | Round-off value = 1.00 | Round-off value = 100.00 |
|-------------------------------------|------------------------|------------------------|------------------------|--------------------------|
| Normal                              | 98,765.43              | 98,765.40              | 98,765.00              | 98,800.00                |
| Downward                            | 98,765.43              | 98,765.40              | 98,765.00              | 98,700.00                |
| Rounding-up                         | 98,765.43              | 98,765.50              | 98,766.00              | 98,800.00                |
| Own advantage, for a credit balance | 98,765.43              | 98,765.40              | 98,765.00              | 98,700.00                |
| Own advantage, for a debit balance  | 98,765.43              | 98,765.50              | 98,766.00              | 98,800.00                |

| **Note**                                                                                  |
|-------------------------------------------------------------------------------------------|
| If you select Own advantage, the rounding is always to the advantage of the legal entity. |



See also
--------

[Sales tax overview](https://docs.microsoft.com/en-us/dynamics365/operations/financials/general-ledger/indirect-taxes-in-microsoft-dynamics-ax-overview)

[View posted sales tax transactions](http://ax.help.dynamics.com/en/wiki/view-posted-sales-tax-transactions/)

