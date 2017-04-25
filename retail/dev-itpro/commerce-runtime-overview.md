---
# required metadata

title: Commerce runtime overview
description: This article provides information about the architecture and configuration of the Microsoft Dynamics 365 for Operations Commerce Runtime (CRT). The CRT is a collection of portable .NET libraries that encapsulate business logic. It serves as the engine for the retail channel. 
author: MargoC
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
# ms.reviewer: robinr
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 218654
ms.assetid: ac422f7e-bc71-4b42-b8c1-4702c6c18421
ms.search.region: Global
# ms.search.industry: 
ms.author: yabinl
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Commerce runtime overview

[!include[banner](../includes/banner.md)]


This article provides information about the architecture and configuration of the Microsoft Dynamics 365 for Operations Commerce Runtime (CRT). The CRT is a collection of portable .NET libraries that encapsulate business logic. It serves as the engine for the retail channel. 

Commerce Runtime architecture
-----------------------------

The following diagram shows the components of the Microsoft Dynamics 365 for Operations Commerce Runtime (CRT). 

[![Commerce Runtime components](./media/crt-architecture-1024x793.jpg)](./media/crt-architecture.jpg)

### Data access

On top of the database is a data access layer. In the data access layer, raw data is translated into objects in memory. For example, an object might be a product. Products have attributes, such as price and color. The data access layer has functions that you can use to manipulate the objects. Stored procedures pass packets of data from the database to data entities that can be used in services and workflows. You can update the packets of data to include new fields that you add in Dynamics 365 for Operations.

### Services

On top of the data access layer is a services layer. Services query for real-time data. You can use these services to customize existing functionality, or you can add your own services that include new functionality.

### Workflows

On top of the services layer is the workflow layer. A workflow is a collection of services and business logic that, together, define business processes. For example, when a customer adds an item to the cart, you can use a workflow to get the price, perform validation, check the inventory quantity, calculate shipping charges, calculate tax, and calculate discounts. You can use the workflows that are included in Dynamics 365 for Operations, or you can create new workflows. You can even use a workflow to connect to a third-party system as part of your business processes.

### API

On top of the workflow layer is the application programming interface (API) layer. You can use the API for tasks such as getting information about items, calculating prices, calculating shipping charges, and placing orders. You can extend the API to fit your business processes.

## Commerce Runtime configuration
Services are enumerated as types in the CRT configuration file. You can add types in the CRT configuration file to control which services are loaded in the CRT. Services are loaded in the order in which they are listed in the configuration file. All the default services are loaded automatically. However, if you add a new service above one of the default services, the new service replaces the default service.


