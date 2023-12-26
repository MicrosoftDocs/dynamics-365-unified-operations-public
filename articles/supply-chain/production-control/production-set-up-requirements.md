---
# required metadata

title: Production setup requirements
description: This article provides information about setup requirements before you can work with Production control. 
author: johanhoffmann
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: ProdParameters, RouteOpr, RouteOprTable, WorkCalendarTable, WorkTimeTable, WrkCtrTable
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.assetid: 1953059f-478d-4706-b461-25b89ace5fc3
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: johanho
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Production setup requirements

[!include [banner](../includes/banner.md)]

This article provides information about setup requirements before you can work with Production control. 

Production control is integrated with features in other modules. This interconnectivity lets you change production orders and make sure that they are automatically updated in all other related processes and calculations in the system. The following setup processes are listed in the order that you should complete them in.

## Required baseline setup in other modules
Information in other modules must be set up before you can work with Production control. This setup includes the following tasks:

-   Set up general company information.
-   Set up the general ledger.
-   Define item groups.
-   Set up ledger accounts for item groups.
-   Set up the inventory item table in Inventory management.
-   Create bills of materials (BOMs) and BOM versions in Product information management.

## Required calendar and resource setup
Before you use Production control, open Organization administration, and create and define the calendar and operations resources in the following order:

1.  **Working time templates** – Set up working time templates to define the times that are available for production scheduling.
2.  **Calendars** – Set up working time calendars to define the days of the year that are available for production scheduling.
3.  **Resource groups** – Set up resource groups to group the operations resources, so that you can get an overview of any free capacity when you run scheduling. You don't have to set up resource groups before you set up operations resources. However, we recommend that you understand how to group resources when you set up Production control.
4.  **Resources** – Set up operations resources to define the resources that are used to complete the production process and plan for capacity.

## Required production parameters setup
**Production control parameters** – Set up basic production parameters to define how the system handles and processes production orders. Define how production orders are created, estimated, scheduled, and consumed. You can also select what kind of feedback you want and how cost accounting is done.

## Required journal name identification
**Production journal names** – Specify the production journal names that are used to record and post transactions.

## Setup if you use operations
Operations represent the specific activities that are completed to produce the finished product. **Note:** You must know the types of activities that are required in order to produce your item, and the order and priorities of those activities. You must also know which resources are involved, and how many.

1.  **Operations** – Set up operations to represent the tasks that must be completed to produce the finished item.
2.  **Relations** – Set up operation relations to establish detailed properties. To define operation relations, click **Relations** on the **Operations** page.

## Setup if you use routes
If you're working with routes, operations must be defined for every production route that you set up. The route represents the path that the item takes from operation to operation, from the start of the production process to the end.

1.  **Cost categories** – Set up cost categories to define the cost per hour of specified processes and setup times.
2.  **Cost groups** – Set up cost groups to create and maintain different types of costing.
3.  **Route groups** – Set up route groups to define parameters that are related to groups of routes. You must set up route groups before you can create production routes.
4.  **Routes** – Set up production routes, and define default settings to control scheduling, costing, and pricing of route operations, and to control progress reporting.
5.  **Route version** – Set up route versions to enable item variations in production.

## Optional advanced settings
1.  **Production groups** – Set up production groups to establish relationships between the production order and ledger accounts. The ledger accounts are used to post or group orders for reporting.
2.  **Production pools** – Create production pools to group production orders so that you can process urgent production orders, or delete and post groups of orders.
3.  **Properties** – Define properties to create special attributes that you can assign to your resources to control the order of productions. These attributes are connected to the working time template.






[!INCLUDE[footer-include](../../includes/footer-banner.md)]
