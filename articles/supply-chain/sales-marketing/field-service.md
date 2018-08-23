---
# required metadata

title: Integration with Microsoft Dynamics 365 for Field Service
description: This topic provides an overview of the Integration with Microsoft Dynamics 365 for Field Service. 
author: ChristianRytt
manager: AnnBe
ms.date: 04/25/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User, IT Pro
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: global
ms.search.industry: 
ms.author: crytt
ms.dyn365.ops.version: July 2017 update 
ms.search.validFrom: 2017-07-8

---


# Integration with Microsoft Dynamics 365 for Field Service

[!include[banner](../includes/banner.md)]

Microsoft Dynamics 365 for Finance and Operations enables synchronization of business processes between Finance and Operations and Microsoft Dynamics 365 for Field Service. The integration scenarios are configured by using extensible Data integrator templates and the Common Data Service (CDS) to enable the synchronization of business processes.

[![Synchronization of business processes between Finance and Operations and Field Service](./media/field-service-integration.png)](./media/field-service-integration.png)

The first phase  of the integration between Field Service and Finance and Operations is focused on enabling work orders and agreements in Field Service to be invoiced in Finance and Operations. The supported flow starts in Field Service, where information from work orders is synchronized to Finance and Operations as sales orders. In Finance and Operations, the sales orders are invoiced to generate invoice documents. In addition, the information from Field Service agreement invoices is synchronized to Finance and Operations. The Microsoft Dynamics 365 Data integrator synchronizes data by using customizable projects. Standard templates can be used to create custom integration projects where additional standard and custom fields, and also entities, can be mapped to adjust the integration and meet specific requirements.

The first phase of the integration between Field Service and Finance and Operations enables synchronization of the following items:

- [Products in Finance and Operations to products in Field Service that include Product Type information](field-service-product.md)
- [Work orders in Field Service to sales orders in Finance and Operations](field-service-work-order.md)
- [Invoices in Field Service to free text invoices in Finance and Operations](field-service-invoice.md)

To see an example of how you can synchronize a work order between Field Service and Finance and Operations, watch the short YouTube video [Synchronize a work order between Dynamics 365 for Field Service and Finance and Operations](https://www.youtube.com/watch?v=hAB4TDVMjxU).

## System requirements for Finance and Operations
Field Service integration supports the following versions:

### Dynamics 365 for Finance and Operations version 8.0 (April 2018) or later

- Dynamics 365 for Finance and Operations version 8.0 (April 2018) was released in April 2018 and has an application build number 8.0.30.8020 with Platform Update 15 (7.0.4841.35234). 

## System requirements for Field Service
To use the Field Service integration solution, you must install the following components:

### Microsoft Dynamics 365 for Field Service 9.0 or later

- Dynamics 365 for Field Service version 1612 (9.0.1.733) (DB 9.0.1.733) online or a later version.
- Prospect to Cash (P2C) solution for Dynamics 365, version 1.15.0.1 or a later version. The solution is available for download from [AppSource](https://appsource.microsoft.com/en-us/product/dynamics-365/mscrm.c7a48b40-eed3-4d67-93ba-f2364281feb3).
- Field Service integration solution for Dynamics 365, version 1.0.0.0 or a later version. The solution is available for download from [AppSource](https://appsource.microsoft.com/en-us/product/dynamics-365/mscrm.p2cfieldserviceintegration).
