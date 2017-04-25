---
# required metadata

title: Set up signers for print forms
description: For legal entities in Czech Republic, Estonia, Hungary, Lithuania, Latvia, Poland, and Russia, you can set up signers and titles for customers and vendors that print documents such as invoices and cash orders.
author: ShylaThompson
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
# ms.reviewer: 81
ms.search.scope: Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 263464
ms.assetid: 7213914a-ecb6-4711-99fe-4e11867aaf4d
ms.search.region: Czech Republic, Estonia, Hungary, Latvia, Lithuania, Poland, Russia
# ms.search.industry: 
ms.author: v-elgolu
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611

---

# Set up signers for print forms

[!include[banner](../includes/banner.md)]


For legal entities in Czech Republic, Estonia, Hungary, Lithuania, Latvia, Poland, and Russia, you can set up signers and titles for customers and vendors that print documents such as invoices and cash orders.

Set up default values
---------------------

To set up signers for the documents that a company prints, use the **Officials** page. You can set up signers and their titles both for the company and for customers or vendors, depending on the document type. The following table describes the tabs on the **Officials** page.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Tab</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>General</td>
<td>Add positions and related information for signers (Director and Chief accountant) who can sign print documents of all types.</td>
</tr>
<tr class="even">
<td>Ledger</td>
<td>Add the position and related information for signers who can sign the following internal financial documents that are related to cash flow:
<ul>
<li>Cash slips</li>
<li>Advance report</li>
<li>Page of cash book</li>
<li>Count statement</li>
<li>Deferrals*</li>
</ul></td>
</tr>
<tr class="odd">
<td>Sales orders</td>
<td>Add positions and related information for signers who can sign the following outgoing primary documents that are related to customers:
<ul>
<li>Invoice for payment*</li>
<li>Invoice</li>
<li>Facture*</li>
<li>Invoice - credit-note</li>
<li>Facture - credit-note*</li>
<li>Tax transaction facture (client)*</li>
</ul></td>
</tr>
<tr class="even">
<td>Purchase orders</td>
<td>Add positions and related information for signers who can sign the following incoming primary documents that are related to vendors:
<ul>
<li>Invoice</li>
<li>Facture*</li>
<li>Invoice - credit-note</li>
<li>Facture - credit-note*</li>
<li>Invoice for payment*</li>
<li>Tax transaction facture (vendor)*</li>
</ul></td>
</tr>
<tr class="odd">
<td>Inventory item management</td>
<td>Add positions and related information for signers who can sign the following warehouse documents when tangible assets are issued to a customer or received from a vendor:
<ul>
<li>Issue slip for sales order (M-15)*</li>
<li>Rmb. slip/Receipt order</li>
<li>Issue slip for transfer order (M-15)*</li>
</ul></td>
</tr>
</tbody>
</table>

\* This document type is available only for legal entities that have their primary address in Russia. The following table describes the fields on the **Officials** page.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Position</td>
<td>Select the signer’s post title.</td>
</tr>
<tr class="even">
<td>Name</td>
<td>Select the signer’s name. The names in the list come from either the Contacts table or the Employees table, depending on the type of signer (that is, depending on whether the <strong>Our</strong> check box is selected). If the signer's name isn't in the list, manually enter the signer’s full name.</td>
</tr>
<tr class="odd">
<td>Job title</td>
<td>Select the signer’s job title. If the signer’s title isn't in the list, manually enter the signer’s title.</td>
</tr>
<tr class="even">
<td>Account code</td>
<td>Select whether the signer can sign all documents of the selected document type, or only documents for a specific customer or vendor.</td>
</tr>
<tr class="odd">
<td>Account relation</td>
<td>Select the customer or vendor account that is related to the selected account code. This field is available only if you select <strong>Record</strong> in the <strong>Account code</strong> field.</td>
</tr>
<tr class="even">
<td>Our</td>
<td>A selected check box indicates that the position is internal.</td>
</tr>
<tr class="odd">
<td>Association with warehouse</td>
<td>Select whether the signer is assigned to all warehouses or only a specific warehouse. The following options are available:
<ul>
<li><strong>All</strong> – The signer is assigned to all warehouses.</li>
<li><strong>Record</strong> – The signer is assigned to a specific warehouse.</li>
</ul></td>
</tr>
<tr class="even">
<td>Warehouse</td>
<td>Select the warehouse code that corresponds to the warehouse that the signer is assigned to. This field is available only if you select <strong>Record</strong> in the <strong>Association with warehouse</strong> field.</td>
</tr>
</tbody>
</table>

## Set up a number sequence code for officials
You can assign a number sequence code for officials in the **Number sequences** section of the **Legal entities** page. Select a number sequence code for the **Officials session ID** reference.

## Modify signers in primary documents
The Officials functionality shows the default predefined signers from the Officials table. On the **Posting invoice** page, on the **Officials** tab, you can modify a signer’s name and title on the primary document for the following document types:

-   Customer invoice
-   Vendor invoice
-   Ship transfer order
-   Cash order

**Note:** After a document is posted, officials can't be edited.



