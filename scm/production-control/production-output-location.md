---
# required metadata

title: Production output location
description: This topic describes how the defaulting heirarchy of the production output location is identified.
author: johanhoffmann
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
# ms.reviewer: 2084
ms.search.scope: Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 221264
ms.assetid: dde49743-1541-4353-a030-63ca3069cd7d
ms.search.region: Global
# ms.search.industry: 
ms.author: johanho
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611
---

# Production output location

[!include[banner](../includes/banner.md)]

This topic describes how the defaulting heirarchy of the production output location is identified.

The production output location is the location where a finished good is first stored after being produced. This location is normally close to the production process that produces the finished good. The location serves as an intermediate storage for the material before it is moved on to, for example, the shipment area, a storage location or a production input location for a downstream production process. 
The production output location is defaulted when finished goods are reported on a production or batch order. The output location is identified by this defaulting hierarchy:
1.	Use the output location defined on the production or batch order header.

    -   If no location found: 

2.	Use the output location defined on the resource used by the last operation defined in the production route.

    -   If no location found:

3.	Use the output location defined on the resource group used by the resource for the last operation defined in the production route.

    -   If no location found:

4.	Use the location defined on the warehouse defined for the production order.

The production output location is only defaulted for products that are set up with advanced warehouse processes. When this type of item is reported as finished, warehouse work of the type Finished goods put away or Co-product and by-product put away is created. This type of work use the production output location as the pick location. The put away location is determined by the location directives.
