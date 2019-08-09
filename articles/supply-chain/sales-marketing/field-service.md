---
# required metadata

title: Integration with Microsoft Dynamics 365 for Field Service overview
description: This topic provides an overview of the Integration with Microsoft Dynamics 365 for Field Service. 
author: ChristianRytt
manager: AnnBe
ms.date: 07/25/2019
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

# Integration with Microsoft Dynamics 365 for Field Service overview

[!include[banner](../includes/banner.md)]

Microsoft Dynamics 365 for Finance and Operations enables synchronization of business processes between Finance and Operations and Microsoft Dynamics 365 for Field Service. The integration scenarios are configured by using extensible Data integrator templates and the Common Data Service (CDS) to enable the synchronization of business processes.
Standard templates can be used to create custom integration projects, where additional standard and custom fields and entities can be mapped to adjust the integration and meet specific business needs. 

The field service integration builds on top of the existing prospect-to-cash functionality.

![Synchronization of business processes between Finance and Operations and Field Service](./media/field-service-integration.png)

The first phase  of the integration between Field Service and Finance and Operations is focused on enabling work orders and agreements in Field Service to be invoiced in Finance and Operations. The supported flow starts in Field Service, where information from work orders is synchronized to Finance and Operations as sales orders. In Finance and Operations, the sales orders are invoiced to generate invoice documents. In addition, the information from Field Service agreement invoices is synchronized to Finance and Operations. The Microsoft Dynamics 365 Data integrator synchronizes data by using customizable projects. Standard templates can be used to create custom integration projects where additional standard and custom fields, and also entities, can be mapped to adjust the integration and meet specific requirements.

The first phase of the integration between Field Service and Finance and Operations enables synchronization of the following items:

- [Products in Finance and Operations to products in Field Service that include Product Type information](field-service-product.md)
- [Work orders in Field Service to sales orders in Finance and Operations](field-service-work-order.md)
- [Invoices in Field Service to free text invoices in Finance and Operations](field-service-invoice.md)

To see an example of how you can synchronize a work order between Field Service and Finance and Operations, watch the short YouTube video [How to synchronize a work order with Microsoft Dynamics 365 Integration](https://www.youtube.com/watch?v=46ylO7raZAo).

## Integration with Microsoft Dynamics 365 for Field Service, including inventory and project information

The additional functionality in this second phase focused on giving field technicians insight about the inventory information from Finance and Operations, allowing them to update inventory levels and do material transfers. In addition, companies installing or servicing sold goods will benefit from better control and visibility to the full sales and service process with integration from projects.

### Functionality includes integration of:
- Warehouse information
- On-hand inventory information
- Inventory transfers
- Inventory adjustments
- Dynamics 365 for Finance and Operations projects connected with Dynamics 365 for Field Service work orders
- Dynamics 365 for Field Service work orders with link to Dynamics 365 for Finance and Operations projects, apply this project number to the Dynamics 365 for Finance and Operations sales order to allow invoicing from the project. 

![Synchronization of business processes between Finance and Operations and Field Service](./media/FSv2overview.png)

### The second phase of the integration between Field Service and Finance and Operations enables synchronization with the following templates:
- Warehouses (Fin and Ops to Field Service) - Warehouses from Finance and Operations to Field Service [Advanced Query] 
- Product Inventory (Fin and Ops to Field Service) - Inventory level information from Finance and Operations to Field Service [Advanced Query] 
- Inventory Adjustment (Field Service to Fin and Ops) - Inventory adjustments from Field Service to Finance and Operations [Advanced Query] 
- Inventory Transfers (Field Service to Fin and Ops) - Inventory transfers from Field Service to Finance and Operations [Advanced Query] 
- Projects (Fin and Ops to Field Service) - Project list from Finance and Operations to Field Service 
- Work Orders with Project (Field Service to Fin and Ops) - Work orders in Field Service to Sales orders  in Finance and Operations, with support for Project [Advanced Query] 
- Field Service Products with Inventory unit (Fin and Ops to Sales) - Finance and Operations 'Sellable released products' to Sales 'Products' for Field Service, including Inventory unit 

## System requirements

### System requirements for Finance and Operations
Field Service integration supports the following versions:

- Dynamics 365 for Finance and Operations version 8.1.2 (December 2018) was released in December 2018 and has an application build number 8.1.195 with Platform Update 22 (7.0.5095). 

### System requirements for Field Service
To use the Field Service integration solution, you must install the following components:

- Field Service for Dynamics 365 (version 8.2.0.286) or a later version on Dynamics 365 9.1.x - Released November 2018
- Prospect to Cash (P2C) solution for Dynamics 365, version 1.15.0.1 or a later version. The solution is available for download from [AppSource](https://appsource.microsoft.com/product/dynamics-365/mscrm.c7a48b40-eed3-4d67-93ba-f2364281feb3).
- 'Field Service Integration, Project and Inventory' solution for Dynamics 365, version 2.0.0.0 or a later version. The solution is available for download from [AppSource](https://appsource.microsoft.com/product/dynamics-365/mscrm.p2cfieldserviceintegrationv2).
