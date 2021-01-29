---
# required metadata

title: Tax calculation service overview
description: This topic explains the overall scope and feature for tax calculation service.
author: wangchen
manager: beya
ms.date: 01/28/2021
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

 

Tax calculation service is a hyper-scalable multi-tenant service that enables the global tax engine to automate and simplify the tax determination and calculation process. The tax engine is fully configurable including but not limited to taxable data model, tax code, tax applicability matrix, tax calculation formula, and it’s running on Microsoft Azure core services platform with modern technology and exponential scalability. 

Tax calculation service integrates with Dynamics 365 Finance and Supply Chain Management at the public preview stage. We plan to integrate it with Dynamics 365 Project operation, Commerce, and other 1st/3rd party applications in the roadmap.

Tax calculation service can help you achieve the following goals:

·     Configuration of tax calculation service through Regulatory Configuration Service (RCS), which is an enhanced version of Electronic Reporting designer available as a standalone service 

·     Configurable tax matrix to automatically determine tax codes and rates 

·     Configurable tax matrix to automatically determine tax registration number 

·     Configurable tax calculation designer to define formulas and conditions 

·     Shared tax determination and calculation solution across legal entities 

·     Microservice-based tax engine with exponential scalability

To use the tax calculation service, you must install the tax calculation service add-in from your project in Microsoft Dynamics Lifecycle Services (LCS) and follow setup procedure to complete the setup in RCS and enable tax calculation service in Dynamics 365 applications. For more information, see **[Get started with tax service](https://go.microsoft.com/fwlink/?linkid=2138482)**.

## Availability

Tax calculation service is available to selected customers through a public preview program and available in sandbox only. Later it will become generally available for all customers and in PROD environment. New features will be delivered in tax calculation service by each release, so always check the most up-to-date documentation for highlighting coverage and scope of supported features.

 The tax calculation service is deployed in the following Azure geographies and will be deployed to more Azure geographies based on customer needs

·     United States 

·     Europe

·     France

·     United Kingdoms

 

Note: The tax calculation service does not support on-premises deployments of Dynamics 365 and early versions like Dynamics AX 2012.

 

## Feature highlights

 

·     Configurable tax matrix to auto determine and calculate tax.

·     Multiple VAT registration number supports.

·     Transfer order support for tax determination and calculation.

·     Transfer order support for multiple VAT registration number determinations.

 

## Supported transactions

 

Tax calculation service can be enabled by legal entity and transaction. Following transactions are supported in the initial public preview release version 10.0.18 and more will be supported in future release.

Sales process

·     Sales Quotation

·     Sales order

·     Confirmation

·     Picking list

·     Packing slip

·     Sales invoice

·     Credit note

·     Return order

·     Header misc. charge

·     Line misc. charge

Purchase process

·     Purchase order

·     Confirmation

·     Receipts list

·     Product receipt

·     Purchase invoice

·     Header misc. charge

·     Line misc. charge

·     Credit note

·     Return order

·     Purchase requisition

·     Purchase requisition line misc. charge

·     Request for quotation

·     Request for quotation header misc. charge

·     Request for quotation line misc. charge

Inventory process

·     Transfer order – ship

·     Transfer order – receive

 

## Related resources

 

·     [Get started with tax service](https://go.microsoft.com/fwlink/?linkid=2138482)

·     [Multiple VAT registration number](https://go.microsoft.com/fwlink/?linkid=2153387)

·     [Tax feature support for transfer order](https://go.microsoft.com/fwlink/?linkid=2153388)

·     [How to build extension in tax service](https://go.microsoft.com/fwlink/?linkid=2138483)
