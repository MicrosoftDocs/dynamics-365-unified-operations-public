---
# required metadata

title: Default offset accounts for vendor invoice journals and invoice approval journals
description: 
author: twheeloc
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
# ms.reviewer: 101
ms.search.scope: AX 7.0.0, Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 62093
ms.assetid: 553933ca-928d-4031-bb8c-f9cff458320b
ms.search.region: global
# ms.search.industry: 
ms.author: abruer
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Default offset accounts for vendor invoice journals and invoice approval journals



Default offset accounts are used on the following vendor invoice journal pages:

-   Invoice journal
-   Invoice approval journal

Use the following table to help decide where you should assign default accounts for invoice journals.

<table>
<colgroup>
<col width="25%" />
<col width="25%" />
<col width="25%" />
<col width="25%" />
</colgroup>
<thead>
<tr class="header">
<th>Set up default accounts here</th>
<th>Where default accounts are provided</th>
<th>How this option affects processing</th>
<th>When you should use this option</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Vendor group</strong> – Set up default offset accounts for vendor groups on the <strong>Default account setup</strong> page, which you can open from the <strong>Vendor groups</strong> page.</td>
<td><ul>
<li>Vendor account</li>
<li>Journal entries for vendor accounts in the vendor group, if default accounts aren’t specified for vendor accounts</li>
</ul></td>
<td>The default offset accounts for vendor groups are shown as default offset accounts for vendors on the <strong>Default account setup</strong> page. You can open this page from the <strong>All vendors</strong> list page.</td>
<td>Use this option if you typically pay for the same types of things from the same vendor groups over time.</td>
</tr>
<tr class="even">
<td><strong>Vendor account</strong> – Set up default accounts for vendor accounts on the <strong>Default account setup</strong> page, which you can open from the <strong>Vendors</strong> page.</td>
<td>Journal entries for the vendor account</td>
<td>The default offset accounts for vendor accounts are shown as default offset accounts for journal entries for the vendor account.</td>
<td>Use this option if you typically pay for the same types of things from the same vendors over time.</td>
</tr>
<tr class="odd">
<td><strong>Journal names</strong> – Set up default offset accounts for journals on the <strong>Journal names</strong> page. Select the <strong>Fixed offset account</strong> option. Note that you can't specify default offset accounts on journal names if the journal type of the journal names is <strong>Invoice register</strong> or <strong>Approval</strong>.</td>
<td><ul>
<li>Journal header that uses the journal name</li>
<li>Journal entries in journals that use the journal name</li>
</ul></td>
<td>If the <strong>Fixed offset account</strong> option on the <strong>Journal names</strong> page is selected, the offset account for the journal name overrides the default offset account for the vendor or vendor group.</td>
<td>Use this option to set up journals for specific costs and expenses that are charged to specific accounts, regardless of the vendor or the vendor group that the vendor belongs to.</td>
</tr>
<tr class="even">
<td><strong>Journal names</strong> – Set up default offset accounts for journals on the <strong>Journal names</strong> page. Clear the <strong>Fixed offset account</strong> option. Note that you can't specify default offset accounts on journal names if the journal type of the journal names is <strong>Invoice register</strong> or <strong>Approval</strong>.</td>
<td><ul>
<li>Journal header</li>
<li>Journal entries in journals that use the journal name</li>
</ul></td>
<td>These default entries are used on journal header pages, and the offset account on the journal header page is used as a default entry on the journal voucher pages. Default accounts from the <strong>Journal names </strong>page are used only if default accounts aren’t set up for the vendor account.</td>
<td>Use this option to set up default accounts that are used when a default vendor offset account isn't assigned.</td>
</tr>
<tr class="odd">
<td><strong>Journal header</strong> – Set up a default offset account for a journal as a default entry on the journal voucher pages. Note that you can't specify default offset accounts on the journal header if the journal type of the journal names is <strong>Invoice register</strong> or <strong>Approval</strong>.</td>
<td>Journal entries in the journal</td>
<td>The default offset account for a journal is used as the default entry on the journal voucher pages.</td>
<td>Use this option to help speed up data entry if most entries in a journal have the same offset account.</td>
</tr>
</tbody>
</table>



