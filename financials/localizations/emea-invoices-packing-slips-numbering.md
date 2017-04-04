---
# required metadata

title: Invoice and packing slip numbering for Latvia and Lithuania
description: This topic explains how to set up number sequences for invoices and packing slips, and how to set up self-numbering ranges for documents.
author: ShylaThompson
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

ms.search.form: LtInvoiceAutoNumberingGroups, LtInvoiceAutonumberingTable, NumberSequenceTableListPage
# ROBOTS: 
audience: Application User
# ms.devlang: 
# ms.reviewer: 81
ms.search.scope: Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 268484
ms.assetid: d7ff8162-bd5c-4582-a18a-144ce5e4c06f
ms.search.region: Latvia, Lithuania
# ms.search.industry: 
ms.author: v-elgolu
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611

---

# Invoice and packing slip numbering for Latvia and Lithuania

This topic explains how to set up number sequences for invoices and packing slips, and how to set up self-numbering ranges for documents.

For legal entities that have a primary address in Latvia or Lithuania, you can set up conditional numbering for invoices and packing slips that is based on the assigned user or user group.

## Set up number sequences for invoices and packing slips
You can set up unique document number sequences for master data records and transaction records. If the tax authorities for your country or region assign your organization a specific document number sequence or format, you can associate the number sequence with a document type. You can assign each document number sequence to a user or user group. In this way, only the designated user or user group can assign the numbers in the series to a document. You can set up number sequences for invoices and packing slips on the **Invoice numbering setup** page. (Click **Organization administration** &gt; **Number sequences** &gt; **Invoice numbering setup**.) Use the information in the following table to complete the fields on the **Invoice numbering setup** page.

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
<td>Numbering</td>
<td>Enter the prefix for the document number sequence.</td>
</tr>
<tr class="even">
<td>Module</td>
<td>Select the module that will use the number series. The module that you select determines the options that are available in the <strong>Type</strong> field. For customer invoices and customer packing slips, select <strong>Sales</strong> in this field.</td>
</tr>
<tr class="odd">
<td>Number sequence code</td>
<td>Select the number sequence code for the data area where the number series is applied.</td>
</tr>
<tr class="even">
<td>Type</td>
<td>Select whether the number sequence applies to invoices or packing slips.</td>
</tr>
<tr class="odd">
<td>Account code</td>
<td>Select how the number series is applied to invoices. The following options are available:
<ul>
<li><strong>Table</strong> – The number series is available only to the user that is selected in the <strong>Code</strong> field.</li>
<li><strong>Group</strong> – The number series is available to the user group that is selected in the <strong>Code</strong> field.</li>
<li><strong>All</strong> – The number series is available to all users.</li>
</ul></td>
</tr>
<tr class="even">
<td>Code</td>
<td>Select the ID of the user or user group that the number series is assigned to for invoice numbering.</td>
</tr>
<tr class="odd">
<td>Last date</td>
<td>The date that the number series was last updated.</td>
</tr>
<tr class="even">
<td>Continue</td>
<td>Select this option to search for number series that are assigned to the selected user or user group.</td>
</tr>
</tbody>
</table>

## Set up document selfnumbering ranges
You can assign specific number sequences to invoices and packing slips that are generated in the **Accounts receivable**, **Accounts payable**, **Inventory management**, and **Project management and accounting** modules. You can also specify individual number sequences for different users and user groups, customer groups and vendor groups, or warehouses. To set up number sequences for customer invoices and vendor invoices, use the **Counters management** page. (Click **Organization administration** &gt; **Number sequences** &gt; **Counters management**.) You can define the number sequence by user or user group, or for specific customer groups and vendor groups. Use the information in the following table to complete the fields on the **Counters management** page.

| Field          | Description                                                                                                                                     |
|----------------|-------------------------------------------------------------------------------------------------------------------------------------------------|
| Module         | Select the module that the selected number sequence applies to.                                                                                 |
| Account code   | Select whether the number sequence code applies to all records in the selected module or to a specific group in the module.                     |
| Code           | Select the code for the selected module. **Note:** The **Code** field is available only if **Group** is selected in the **Account code** field. |
| Type           | Select the type of document to number: **Invoice** or **Packing slip**.                                                                         |
| Auto numbering | Select this option to automatically assign a number to a document. You can manually select or clear this option for individual documents.       |

For information about how to manually number invoices and packing slips, see [Edit invoice ID on Sales orders](emea-edit-invoice-id-sales-orders.md).

## Affected processes
The headers of the following documents are updated with invoice and packing slip numbering:

-   Sales orders
-   Purchase orders
-   Free text invoices
-   Project invoice proposals

When you post the following documents, you can select a specific number sequence in the **Numbering** field:

-   Sales packing slip
-   Sales posting invoice
-   Purchasing posting product receipt
-   Purchasing vendor invoices
-   Post project invoice proposals
-   Post free text invoice

Additionally, forms below are supplemented by the **Documents to update** field:

-   Purchasing Vendor invoices form,
-   Sales Packing slip posting form,
-   Sales Posting invoice form,
-   Purchasing Posting product receipt form.

The “**Documents to update**” field influences on the “**Document status**” field in “**Packing slip journal**” and "**Invoice Journal**". On **Packing slip** creation, the “**Document status**” field value is equal to “**None**”. If any **Packing slip** was chosen in field “**Documents to update**” then its “**Document status**” would be “**Broken**” and the “**Document status**” of **Packing slip** where it was done will be “**Canceled**”.

