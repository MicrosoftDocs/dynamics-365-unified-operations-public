---
# required metadata

title: Chronological invoice and voucher numbers for France
description: This topic explains how to set up and use chronological numbers for invoices and vouchers in Accounts receivable for legal entities in France.  
author: ShylaThompson
manager: AnnBe
ms date: 2017-04-04
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

ms.search.form: CustParameters, NumberSequenceGroup
# ROBOTS: 
audience: Application User
# ms.devlang: 
# ms.reviewer: 81
ms.search.scope: Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 264514
ms.assetid: d1fce1dc-2186-443c-9b4d-b6f64236bc3a
ms.search.region: France
# ms.search.industry: 
ms.author: ilyako
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611

---

# Chronological invoice and voucher numbers for France

This topic explains how to set up and use chronological numbers for invoices and vouchers in Accounts receivable for legal entities in France.  

In France, there is a legal requirement that all invoices and related vouchers that are issued be numbered in chronological order. The chronology must be supported by fiscal periods. All the numbers that belong to earlier periods must be less than the numbers that belong to later periods. Within one fiscal period, chronological order isn't mandatory, but there must be no gaps in the numbering. To meet this requirement, chronological numbering in Accounts receivable affects the following documents:

-   Free text invoice
-   Free text invoice voucher
-   Free text credit note
-   Free text credit note voucher
-   Sales invoice
-   Sales invoice voucher
-   Sales credit note
-   Sales credit note voucher

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
<td>Country/region</td>
<td>The primary address of the legal entity must be in France.</td>
</tr>
<tr class="even">
<td>Related setup tasks</td>
<td><ul>
<li>On the <strong>Accounts receivable parameters</strong> page, on the <strong>Updates</strong> tab, set the <strong>Chronological numbering</strong> option to <strong>Yes</strong>.</li>
<li>On the <strong>Number sequences</strong> page, define as many number sequences as you require to cover the affected fiscal periods. You should specify a company for each number sequence. The segments of the number sequences must be defined so that they provide chronological order for periods. For example, the segment names can contain a special prefix that identifies a specific period.</li>
</ul></td>
</tr>
</tbody>
</table>

## Set up chronological numbering
### Accounts receivable parameters

On the **Accounts receivable parameters** page, on the **Number sequences** tab, select one of the supported references, such as **Free text invoice**. Then click the **Chronological numbering setup** button that will be available for the supported references. On the **Chronological numbering setup** page, define the date-effective number sequences that have valid periods.

### Number sequence groups

If different customers use different patterns for numbering, you must set up chronological numbering at the level of the number sequence group. On the **Accounts receivable parameters** page, on the **Number sequences** tab, select one of the supported references, and then click **Group**. On the **Number sequence group** page, select an existing group, or create a new group. In the **Reference** section, select one of the supported references, and then click **Chronological numbering setup**. On the **Chronological numbering setup** page, define date-effective number sequences that have valid periods.

## Invoice posting
When you post an invoice or a credit note, the appropriate number sequence is used to generate a number. This number sequence is selected based on the valid period that contains the invoice date. Customer-specific chronological numbering has higher priority than chronological numbering.

