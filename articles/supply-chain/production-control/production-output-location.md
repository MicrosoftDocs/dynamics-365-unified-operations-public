---
# required metadata

title: Production output location
description: This topic describes the hierarchy that is used to identify the production output location.
author: johanhoffmann
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
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

[!include [banner](../includes/banner.md)]

This topic describes the hierarchy that is used to identify the production output location.

The production output location is the location where a finished good is first stored after it's produced. Usually, this location is close to the production process that produces the finished good. The production output location is used as intermediate storage for the material before it's moved on to the shipment area, a storage location, a production input location for a downstream production process, and so on. 

A default production output location is set when finished goods are reported on a production order or batch order. The following hierarchy is used to identify this output location:

1. Use the output location that is defined on the production order or batch order header.
2. If no location is found there, use the output location that is defined on the resource that is used by the last operation that is defined in the production route.
3. If no location is found there, use the output location that is defined on the resource group that is used by the resource for the last operation that is defined in the production route.
4. If no location is found there, use the output location that is defined on the warehouse that is defined for the production order.

A default production output location is set only for products that are set up by using advanced warehouse processes. When this type of item is reported as finished, warehouse work of the **Finished goods put away** or **Co-product and by-product put away** type is created. This type of work uses the production output location as the pick location. The put-away location is determined by the location directives.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]