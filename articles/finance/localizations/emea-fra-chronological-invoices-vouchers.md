---
# required metadata

title: Chronological invoice and voucher numbers
description: This topic explains how to set up and use chronological numbers for invoices and vouchers in Accounts receivable.  
author: ShylaThompson
manager: AnnBe
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: CustParameters, NumberSequenceGroup
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 264514
ms.search.region: France
# ms.search.industry: 
ms.author: ilyako
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611

---

# Chronological invoice and voucher numbers

[!include [banner](../includes/banner.md)]

This topic explains how to set up and use chronological numbers for invoices and vouchers in Accounts receivable.  

In some countries, there is a legal requirement that all invoices and related vouchers that are issued be numbered in chronological order. The chronology must be supported by fiscal periods. All the numbers that belong to earlier periods must be less than the numbers that belong to later periods. Within one fiscal period, chronological order isn't mandatory, but there must be no gaps in the numbering. To meet this requirement, chronological numbering in Accounts receivable affects the following documents:

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
<td>Feature activation</td>
<td>In the **Feature management** workspace, turn on the **Chronological numbering** feature. For more information, see [Feature management overview](../../fin-and-ops/get-started/feature-management/feature-management-overview.md).</td>
</tr>
<tr class="even">
<td>Country/region</td>
<td>If the primary address of the legal entity is in <strong>France</strong> then additionally set the <strong>Chronological numbering</strong> option to <strong>Yes</strong> on the <strong>Accounts receivable parameters</strong> page, on the <strong>Updates</strong> tab.</td>
</tr>
<tr class="odd">
<td>Related setup tasks</td>
<td>On the <strong>Number sequences</strong> page, define as many number sequences as you require to cover the affected fiscal periods. You should specify a company for each number sequence. The segments of the number sequences must be defined so that they provide chronological order for periods. For example, the segment names can contain a special prefix that identifies a specific period.</td>
</tr>
</tbody>
</table>

## Set up chronological numbering
### Accounts receivable parameters

On the **Accounts receivable parameters** page, on the **Number sequences** tab, select one of the supported references, such as **Free text invoice**. Then click the **Chronological numbering setup** button that will be available for the supported references. On the **Chronological numbering setup** page, define the date-effective number sequences that have valid periods.

![Chronological numbers setup](media/emea-chronological-numbering.jpg)

### Number sequence groups

If different customers use different patterns for numbering, you must set up chronological numbering at the level of the number sequence group. On the **Accounts receivable parameters** page, on the **Number sequences** tab, select one of the supported references, and then click **Group**. On the **Number sequence group** page, select an existing group, or create a new group. In the **Reference** section, select one of the supported references, and then click **Chronological numbering setup**. On the **Chronological numbering setup** page, define date-effective number sequences that have valid periods.

## Invoice posting
When you post an invoice or a credit note, the appropriate number sequence is used to generate a number. This number sequence is selected based on the valid period that contains the invoice date. Customer-specific chronological numbering has higher priority than chronological numbering.

### Dates control

The system performs an additional invoice dates control for customer invoices: 

- Posting new invoices with dates earlier than the date of the latest posted invoice is forbidden if no reason code is defined. To enable posting, a reason code must be entered either in an invoice/order header or in one of the lines.
- A warning is raised if the new invoice date is later than the system date.
