---
title: EU Entry certificates
description: This article provides information about European Union (EU) entry certificates.
author: mrolecki
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: Austria, Belgium, Czech Republic, Denmark, Estonia, Finland, France, Germany, Hungary, Ireland, Italy, Latvia, Lithuania, Netherlands, Poland, Spain, Sweden, United Kingdom
ms.author: mrolecki
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
ms.search.form: CustEntryCertificateJour_W, CustParameters, CustTable, SalesTable
---

# EU entry certificates

[!include [banner](../includes/banner.md)]

This article provides information about European Union (EU) entry certificates.

You can complete the following tasks for a European Union (EU) entry certificate:

-   Create and issue an EU entry certificate together with a packing slip or customer invoice for the delivery of items or services to EU countries/regions.
-   Receive the EU entry certificate that is signed by an EU customer.
-   Upload the signed EU entry certificate that is received either from the customer or from a third party who is responsible for delivering items to the customer.
-   Associate the uploaded EU entry certificate with a customer invoice.
-   Update the status of the uploaded EU entry certificate.

## Prerequisites
The following table shows the prerequisites that must be in place before you start.

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
<td>The primary address of the legal entity must be in a EU member state.</td>
</tr>
<tr class="even">
<td>Related set up tasks</td>
<td><ul>
<li>On the <strong>Accounts receivable parameters</strong> page, select the <strong>Enable entry certificate management</strong> and <strong>Enable entry certificate issuing</strong> options.</li>
<li>On the <strong>Customers</strong> page, on the <strong>Invoice and delivery</strong> FastTab, select the <strong>Entry certificate required</strong> option to indicate that an EU entry certificate is mandatory for the customer. Select the <strong>Issue entry certificate</strong> option to issue an EU entry certificate of the legal entity to the customer.</li>
<li>On the <strong>Accounts receivable parameters</strong> page, select a number sequence code for the <strong>Entry certificate</strong> reference.</li>
</ul></td>
</tr>
<tr class="odd">
<td>Related transactions</td>
<td><ul>
<li>Create a customer account.</li>
<li>Create a sales order.</li>
</ul></td>
</tr>
</tbody>
</table>

## Creating, registering, and uploading an EU entry certificate
You can create an EU entry certificate automatically or manually. An EU entry certificate is created and printed automatically when you post a packing slip or invoice for a customer by using the **Packing slip posting** page or the **Posting invoice** page. To manually create or reprint an EU entry certificate for a customer invoice, use the **Invoice journal** page. Additionally, you can use the **Entry certificate journal** page to enter details about an EU entry certificate that is issued by a third party.

### Creating an EU entry certificate automatically or manually

You can create an EU entry certificate automatically by using a packing slip on the **All sales orders** page or by using an invoice on the **Sales order** page. To manually create an EU entry certificate, you can use an invoice on the **Invoice journal** page. However, you must change the certification status of the invoice before you manually create an EU entry certificate.

### Registering an EU entry certificate

If registration is required, you can use the **Entry certificate journal** page to register an EU entry certificate that is issued by a third party.

### Uploading a received EU entry certificate

Use the **Attachments** page to upload a received EU entry certificate that is signed by an EU customer. After the certificate is uploaded, you can associate it with an invoice as proof that the items were delivered. This proof is required if you must issue an invoice that doesn't include value-added tax (VAT), and it's also used during auditing.

### Optional: Updating the certification status and printing status of an invoice

You can update the entry certification status and printing status of a customer invoice by using the **Invoice journal** page.

## Technical information for system administrators
If you don't have access to the pages that are used to complete this task, contact your system administrator, and provide the information that is shown in the following table.

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
<td>Security roles and duties</td>
<td>To set up and create EU entry certificates for items or services, you must be a member of a security role that includes the following duties:
<ul>
<li><strong>Accounts receivable clerk</strong> (CustInvoiceAccountsReceivableClerk)</li>
<li><strong>Customer service representative</strong> (TradeCustomerServiceRepresentative)</li>
<li><strong>Sales clerk</strong> (TradeSalesClerk)</li>
<li><strong>Shipping clerk</strong> (InventShippingClerk)</li>
</ul></td>
</tr>
</tbody>
</table>







[!INCLUDE[footer-include](../../includes/footer-banner.md)]
