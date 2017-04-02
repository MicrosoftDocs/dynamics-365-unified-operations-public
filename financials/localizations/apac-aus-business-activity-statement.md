---
# required metadata

title: Business Activity Statement (BAS)
description: This topic provides information about the business activity statement (BAS) for Australia. The BAS is a form submitted to the Australian Taxation Office by all businesses to report their taxation obligations.          
author: ShylaThompson
manager: AnnBe
ms date: 2017-04-04
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
# ms.reviewer: 81
ms.search.scope: AX 7.0.0, Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 12641
ms.assetid: 76db7011-2055-4c24-ac78-8f4d0675da2b
ms.search.region: Australia
# ms.search.industry: 
ms.author: leguo
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Business activity statement (BAS)

This topic provides information about the business activity statement (BAS) for Australia. The BAS is a form submitted to the Australian Taxation Office by all businesses to report their taxation obligations.          

The business activity statement feature in Microsoft Dynamics AX is designed to help you fill out your Business Activity Statement, commonly known as the BAS. It is very similar to the Calculation Sheet that the Australian Taxation Office provides you when you receive your BAS form in the mail. The taxation liabilities in the BAS include the following:

-   GST amounts you owe the Australian Taxation Office from sales
-   GST amounts the Australian Taxation Office owes you from purchases
-   Pay-As-You-Go (PAYG) Tax Withheld
-   Pay-As-You-Go (PAYG) Instalment
-   Fringe Benefit Tax (FBT)

The following list provides an overview of the process to calculate GST and prepare the BAS in General ledger:

1.  Set up GST prerequisites. Refer to the table at the end of this article.
2.  Set up report boxes - You must set up BAS report boxes to report other non-GST tax liabilities and credits for a particular GST settlement periods.
3.  Post and settle Australian BAS to tax authorities for a particular GST settlement period.
4.  Process payments to tax authorities.
5.  Manually adjust journals to transfer non-GST transactions posted to the BAS reconciliation account to the correct ledger account.
6.  Print and review GST reports.

## Prerequisites
<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Category</th>
<th>Prerequisite</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span class="ui">Country/region</span></td>
<td>The primary address for the legal entity must be in the following countries/regions: Australia</td>
</tr>
<tr class="even">
<td><span class="ui">Parameters</span></td>
<td><ul>
<li>Unmark the Apply sales tax taxable rules check box on the General ledger parameters page.</li>
</ul></td>
</tr>
<tr class="odd">
<td><span class="ui">Related setup tasks</span></td>
<td><ul>
<li>Create an additional BAS reconciliation account</li>
<li>Create ledger posting groups.</li>
<li>Set up the GST sales tax authority</li>
<li>Create settlement periods</li>
<li>Set up sales tax reporting codes</li>
<li>Set up sales tax codes</li>
<li>Set up sales tax groups</li>
<li>Set up item sales tax groups</li>
<li>Set up reason codes for Australia BAS</li>
<li>Set up BAS fringe benefit reason codes</li>
<li>Set up withholding tax codes</li>
<li>Set up withholding tax groups</li>
<li>Specify the withholding tax group for Vendors</li>
</ul></td>
</tr>
</tbody>
</table>
