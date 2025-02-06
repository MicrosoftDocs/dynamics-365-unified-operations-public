---
title: Invoice capture solution overview
description: Learn about the Invoice capture solution, including a table that outlines actions, system, and role names for various roles.
author: sunfzam
ms.author: shielas
ms.topic: overview
ms.date: 02/06/2025
ms.reviewer: twheeloc
ms.collection: get-started
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2022-09-28
ms.search.form: VendorInvoiceWorkspace, VendInvoiceInfoListPage
ms.dyn365.ops.version: 
ms.assetid: 0ec4dbc0-2eeb-423b-8592-4b5d37e559d3
---

# Invoice capture solution

[!include [banner](../includes/banner.md)]

This article provides information about the Invoice capture solution that automatically creates vendor invoices from digital invoice images.

The Accounts payable (AP) department manages and processes invoices for goods and services that are received. The AP accountant verifies data on vendor invoices for the following reasons:

- To avoid extra effort if adjustments or corrections are required during period close
- To pay vendor invoices in a timely manner and prevent financial loss because of error or fraud

Optical character recognition (OCR) has become widely used by different industries in past years. It's now common for printed texts to be digitized, so that they can be electronically edited, searched, stored more compactly, and displayed online. The digital text can be used in machine processes such as cognitive computing, machine translation, text-to-speech, key data, and text mining.

The evolution of artificial intelligence (AI) technology has enabled modern OCR solutions to read different invoice formats from different vendors without requiring much human intervention. More companies are recognizing that they can save effort and improve accuracy by processing invoices via automation instead of doing manual processing.


## Required roles

The following table shows the roles that are required to set up and use the Invoice capture solution.

| Role | Actions | Systems | Role names |
|------|---------|---------|------------|
| Administrator | <ul><li>Set up environments in Microsoft Power Platform.</li><li>Deploy solutions in Microsoft Power Platform.</li><li>Set up connections between Dynamics 365 and AI Builder.</li><li>Set up Azure Data Lake Storage locations.</li><li>Install Invoice capture.</li></ul> | <ul><li>Dynamics 365</li><li>Microsoft Power Platform</li><li>Azure Data Lake Storage</li></ul> | <ul><li>Dynamics 365 administrator</li><li>Power Platform administrator</li><li>Storage Blob data owner</li></ul> |
| Environment maker | <ul><li>Create custom AI models, and create flows in Power Automate.</li></ul> | <ul><li>Microsoft Power Platform</li></ul> | <ul><li>Environment makers</li></ul> |
| AP admin | <ul><li>Set up and configure Invoice capture.</li></ul> | <ul><li>Microsoft Power Platform</li><li>Dynamics 365 Finance</li></ul> | <ul><li>Accounts Payable admin role</li><li>InvoiceCaptureOperator</li></ul> |
| AP clerk | <ul><li>Review and correct captured invoices in Invoice capture.</li></ul> | <ul><li>Invoice capture in Power Platform</li><li>Dynamics 365 Finance</li></ul> | <ul><li>Accounts payable clerk role</li><li>InvoiceCaptureOperator</li></ul> |

The **InvoiceCaptureOperator** role must be included in the role settings to successfully run the derivation and validation logic in Invoice capture, and to transfer the invoice to Dynamics 365 Finance. For a touchless scenario, the role must be added to the corresponding flow user on the finance and operations apps side. 

> [!NOTE]
> The **Environment maker** role must be assigned to the Accounts payable administrator if they create channels in Invoice capture.

## License

To use the Invoice capture solution, the following licenses must be considered for Dynamics 365 Finance customers:

- **Power Apps license (per user)** – If users don't have a full Dynamics 365 Finance license and want to access Invoice capture, a Power Apps license is needed with the **InvoiceCaptureOperator** role assigned in Dynamics 365 Finance. 
- **Azure Data Lake Storage subscription** – Usually, Dynamics 365 Finance customers don't have to subscribe to more Azure Data Lake storage if the 20-gigabyte (GB) Dataverse file license is sufficient to persist the original invoice documents. Different apps share this Dataverse file storage. Extra subscriptions might be needed if the Dataverse file capacity isn't sufficient. The same applies to Dataverse database storage (default capacity: 10 GB).
- **Invoice processing fee based on number of invoices** – Dynamics 365 Finance customers are entitled to 100 invoice capture transactions per tenant per month. If customers need more transactions, they must purchase extra Electronic Invoicing stock keeping units (SKUs) at 300 US dollars (USD) for 1,000 transactions per tenant per month. The transaction capacity is available on a monthly, use-it-or-lose-it basis, and customers must purchase for peak capacity.

### Licensing FAQ 
How are the number of invoices calculated for the monthly quota? Are received files included?  
 - No, only the captured invoices are going to be considered as valid transactions. In case the file has been filtered by the file filter setting it won't be counted. 

Is there a supported list of environment types for invoice capture? 
 - Invoice capture is supported when the integrated Dataverse environment exists. This should include Partner Tier 2 environments. Learn more in [Enable power platform integration](../../fin-ops-core/dev-itpro/power-platform/enable-power-platform-integration.md). 
