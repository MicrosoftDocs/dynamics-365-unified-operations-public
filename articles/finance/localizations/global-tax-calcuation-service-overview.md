---
# required metadata

title: Tax calculation service overview
description: This topic explains the overall scope and feature for the tax calculation service.
author: wangchen
manager: beya
ms.date: 03/02/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form:
audience: Application user
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: wangchen
ms.search.validFrom: 2021-04-01
ms.dyn365.ops.version: 10.0.18

---

# Tax calculation service (Preview) overview

 [!include [banner](../includes/banner.md)]
 
 [!include [banner](../includes/preview-banner.md)]

The tax calculation service is a hyper-scalable multi-tenant service that enables the global tax engine to automate and simplify the tax determination and calculation process. The tax engine is fully configurable including but not limited to taxable data model, tax code, tax applicability matrix, and tax calculation formula. The tax engine is running on Microsoft Azure core services platform with modern technology and exponential scalability. 

The tax calculation service integrates with Dynamics 365 Finance and Dynamics 365 Supply Chain Management. In the future, the tax calculation service will integrate with Dynamics 365 Project Operations, Dynamics 365 Commerce, and other first- and third-party applications.

The tax calculation service is a Microsoft-based tax engine with exponential scalability that can help you to:

   - Configure the tax calculation service through the Microsoft Dynamics Regulatory Configuration Service (RCS), which is an enhanced version of the Electronic Reporting designer and is available as a standalone service.
   - Configure hee tax matrix to automatically determine tax codes and rates 
   - Configure the tax matrix to automatically determine the tax registration number 
   - Configure the tax calculation designer to define formulas and conditions 
   - Share tax determination and calculations solution across legal entities 

To use the tax calculation service, install the tax calculation service add-in from your project in Microsoft Dynamics Lifecycle Services (LCS) and follow the set up procedure to complete the setup in RCS and enable tax calculation service in Finance and Supply Chain Management. For more information, see **[Get started with tax service](https://go.microsoft.com/fwlink/?linkid=2138482)**.

## Availability

The tax calculation service is only available in a sandbox environment to selected customers through a public preview program. In the future, the service will become generally available for all customers and in a PROD environment. New features will be delivered in the tax calculation service, so always check the most up-to-date documentation for highlighting coverage and scope of supported features.

 The tax calculation service is deployed in the following Azure geographies and will be deployed to more Azure geographies based on customer needs:

   - United States 
   - Europe
   - France
   - United Kingdoms

> [!NOTE]
> The tax calculation service doesn't support on-premises deployments of Dynamics 365 and earlier versions like Dynamics AX 2012.


## Feature highlights

- Configurable tax matrix to automatically determine and calculate tax.
- Multiple VAT registration number supports.
- Transfer order support for tax determination and calculation.
- Transfer order support for multiple VAT registration number determinations. 

## Supported transactions

The tax calculation service can be enabled by legal entity and transaction. The following transactions are supported:

- Sales process

     - Sales Quotation
     - Sales order
     - Confirmation
     - Picking list
     - Packing slip
     - Sales invoice
     - Credit note
     - Return order
     - Header misc. charge
     - Line misc. charge

- Purchase process

     - Purchase order
     - Confirmation
     - Receipts list
     - Product receipt
     - Purchase invoice
     - Header misc. charge
     - Line misc. charge
     - Credit note
     - Return order
     - Purchase requisition
     - Purchase requisition line misc. charge
     - Request for quotation
     - Request for quotation header misc. charge
     - Request for quotation line misc. charge

- Inventory process

     - Transfer order – ship
     - Transfer order – receive

## Related resources

[Get started with tax service](https://go.microsoft.com/fwlink/?linkid=2138482)

[Multiple VAT registration number](https://go.microsoft.com/fwlink/?linkid=2153387)

[Tax feature support for transfer order](https://go.microsoft.com/fwlink/?linkid=2153388)

[How to build extension in tax service](https://go.microsoft.com/fwlink/?linkid=2138483)
