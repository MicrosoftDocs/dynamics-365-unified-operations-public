---
title: EU Entry certificates
description: Learn about European Union (EU) entry certificates, including prerequisites and technical information for system administrators.
author: mrolecki
ms.author: johnmichalak
ms.topic: article
ms.date: 12/16/2025
ms.reviewer: johnmichalak
audience: Application User
ms.search.region: Austria, Belgium, Czech Republic, Denmark, Estonia, Finland, France, Germany, Hungary, Ireland, Italy, Latvia, Lithuania, Netherlands, Poland, Spain, Sweden, United Kingdom
ms.search.validFrom: 2016-02-28
ms.search.form: CustEntryCertificateJour_W, CustParameters, CustTable, SalesTable
ms.dyn365.ops.version: AX 7.0.0
---

# EU entry certificates

[!include [banner](../../includes/banner.md)]

This article provides information about European Union (EU) entry certificates.

For a European Union (EU) entry certificate, you can complete the following tasks:

- Create and issue an EU entry certificate together with a packing slip or customer invoice for the delivery of items or services to EU countries or regions.
- Receive the EU entry certificate that an EU customer signs.
- Upload the signed EU entry certificate that you receive either from the customer or from a third party who is responsible for delivering items to the customer.
- Associate the uploaded EU entry certificate with a customer invoice.
- Update the status of the uploaded EU entry certificate.

## Prerequisites

The following table shows the prerequisites that must be in place before you start.

| Category | Prerequisite |
|----------|--------------|
| Country/region | The primary address of the legal entity must be in an EU member state. |
| Related set up tasks | <ul><li>On the <strong>Accounts receivable parameters</strong> page, select the <strong>Enable entry certificate management</strong> and <strong>Enable entry certificate issuing</strong> options.</li><li>On the <strong>Customers</strong> page, on the <strong>Invoice and delivery</strong> FastTab, select the <strong>Entry certificate required</strong> option to indicate that an EU entry certificate is mandatory for the customer. Select the <strong>Issue entry certificate</strong> option to issue an EU entry certificate of the legal entity to the customer.</li><li>On the <strong>Accounts receivable parameters</strong> page, select a number sequence code for the <strong>Entry certificate</strong> reference.</li></ul> |
| Related transactions | <ul><li>Create a customer account.</li><li>Create a sales order.</li></ul> |

## Creating, registering, and uploading an EU entry certificate

You can create an EU entry certificate automatically or manually. The system automatically creates and prints an EU entry certificate when you post a packing slip or invoice for a customer by using the **Packing slip posting** page or the **Posting invoice** page. To manually create or reprint an EU entry certificate for a customer invoice, use the **Invoice journal** page. Additionally, you can use the **Entry certificate journal** page to enter details about an EU entry certificate that a third party issues.

### Creating an EU entry certificate automatically or manually

You can create an EU entry certificate automatically by using a packing slip on the **All sales orders** page or by using an invoice on the **Sales order** page. To manually create an EU entry certificate, use an invoice on the **Invoice journal** page. However, you must change the certification status of the invoice before you manually create an EU entry certificate.

### Registering an EU entry certificate

If registration is required, use the **Entry certificate journal** page to register an EU entry certificate that a third party issues.

### Uploading a received EU entry certificate

Use the **Attachments** page to upload a received EU entry certificate that an EU customer signs. After you upload the certificate, you can associate it with an invoice as proof that the items were delivered. This proof is required if you must issue an invoice that doesn't include value-added tax (VAT), and it's also used during auditing.

### Optional: Updating the certification status and printing status of an invoice

You can update the entry certification status and printing status of a customer invoice by using the **Invoice journal** page.

## Technical information for system administrators

If you don't have access to the pages that are used to complete this task, contact your system administrator, and provide the information that the following table shows.

| Category | Prerequisite |
|----------|--------------|
| Security roles and duties | To set up and create EU entry certificates for items or services, you must be a member of a security role that includes the following duties:<ul><li><strong>Accounts receivable clerk</strong> (CustInvoiceAccountsReceivableClerk)</li><li><strong>Customer service representative</strong> (TradeCustomerServiceRepresentative)</li><li><strong>Sales clerk</strong> (TradeSalesClerk)</li><li><strong>Shipping clerk</strong> (InventShippingClerk)</li></ul> |

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
