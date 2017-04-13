---
# required metadata

title: Credit note on cash discount
description: This topic provides information that will help legal entities in the Czech Republic create, post, and print credit notes for cash discounts that are given to customers.
author: ShylaThompson
manager: AnnBe
ms.date: 04/10/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

ms.search.form: CustParameters, PrintMgmtSetupUIMain, Reasons
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: ShylaThompson
ms.search.scope: Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 273063
ms.assetid: b7cc2add-88dc-4e15-a537-49f3ebe2e37f
ms.search.region: Czech Republic
# ms.search.industry: 
ms.author: v-elgolu
ms.dyn365.ops.intro: Version 1611
ms.search.validFrom: 2016-11-30

---

# Credit note on cash discount
"[!include[banner](../includes/banner.md)]"


This topic provides information that will help legal entities in the Czech Republic create, post, and print credit notes for cash discounts that are given to customers.

Companies in the Czech Republic must issue credit notes for cash discounts that are given to customers. These credit notes must include the following information:

-   Invoice number
-   Value-added tax (VAT) base and amount from the original document
-   Reason for a correction

## Prerequisites
<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Prerequisite</th>
<th>Information</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Set up number sequences.</td>
<td>Create a continuous number sequence for a legal entity. For more information, see <a href="http://ax.help.dynamics.com/en/wiki/set-up-number-sequences-on-an-individual-basis/">Set up number sequences on an individual basis.</a> On the <strong>Accounts receivable parameters</strong> page, select the number sequence that you created for <strong>Sales credit note</strong>. Additionally, set up a number sequence for <strong>Sales credit note voucher</strong>. You can use the same number�sequence�that you used for <strong>Sales credit note</strong>.</td>
</tr>
<tr class="even">
<td>Set up sales tax codes.</td>
<td>For more information, see <a href="http://ax.help.dynamics.com/en/wiki/set-up-sales-tax-codes/">Set up sales tax codes</a>.</td>
</tr>
<tr class="odd">
<td>Set up report formats for documents.</td>
<td><ol>
<li>Go to <strong>Accounts receivable</strong> &gt; <strong>Setup</strong> &gt; <strong>Forms</strong> &gt; <strong>Form setup</strong>.</li>
<li>On the <strong>General</strong> tab, under <strong>Set up options for customer forms</strong>, click <strong>Print management</strong>.</li>
<li>In the tree, expand <strong>Module - accounts receivable</strong> &gt; <strong>Documents</strong> &gt; <strong>Customer invoice</strong>. In the <strong>Report format</strong> field, enter or select a value.</li>
<li>In the tree, under the <strong>Customer invoice</strong> node, select <strong>Original</strong>. In the <strong>Report format</strong> field, enter or select a value.</li>
<li>In the tree, expand <strong>Module - accounts receivable</strong> &gt; <strong>Documents</strong> &gt; <strong>Free text invoice</strong>. In the <strong>Report format</strong> field, enter or select a value.</li>
<li>In the tree, under the <strong>Free text invoice</strong> node, select <strong>Original</strong>. In the <strong>Report format</strong> field, enter or select a value.</li>
</ol></td>
</tr>
<tr class="even">
<td>Set up customer reason codes.</td>
<td>On the <strong>Customer reason codes</strong> page (<strong>Accounts receivable</strong> &gt; <strong>Setup</strong> &gt; <strong>Customer reason codes</strong>), create or edit the reason codes that are used for tax corrective documents.</td>
</tr>
<tr class="odd">
<td>Set up Accounts receivable parameters.</td>
<td>On the <strong>Accounts receivable parameters</strong> page (<strong>Accounts receivable</strong> &gt; <strong>Setup</strong> &gt; <strong>Accounts receivable parameters</strong>), on <strong>Settlement</strong> tab, on the <strong>Options</strong> FastTab, set up the following parameters:
<ul>
<li>Select the <strong>Require reason codes for credit notes</strong> check box.</li>
<li>Select the <strong>Post credit note for cash discount</strong> check box.</li>
<li>In the <strong>Reason code for cash discounts</strong> field, select a default reason code to use for tax corrective documents.</li>
</ul></td>
</tr>
</tbody>
</table>

## Credit notes for cash discounts
Credit notes for cash discounts are posted automatically when open customer transactions (customer invoice and customer payment) are settled. When credit notes for cash discounts are posted, they include the reason codes that you set up in Account receivable parameters, and a reference to the original invoice. Credit notes for cash discounts are numbered by using the number sequence that you set up for credit notes. The document printout is named **Tax corrective document**. It includes the original invoice number, the VAT base and amount, and the reason why a correction was printed.


