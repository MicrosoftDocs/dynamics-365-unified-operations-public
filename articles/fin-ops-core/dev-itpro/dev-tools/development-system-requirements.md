---
title: Development system requirements
description: This article lists the system requirements for development.
author: gianugo
ms.date: 06/20/2017
ms.topic: article
audience: Developer
ms.reviewer: josaw
ms.search.region: Global
ms.author: gianura
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: f39dbe39-7dc3-463c-923e-f22af231b979
---

# Development system requirements

[!include [banner](../includes/banner.md)]

This article lists the system requirements for development.

Development environments can be hosted locally or in Microsoft Azure. The build process, X++ compilation, and generation of cross reference information, typically run satisfactorily on machines with 16 GB of memory and two CPU cores. The compiler uses available resources, so more RAM and more cores can speed up compilation, especially if there is contention for the resources from other concurrent processes. If you are running concurrent processes, then we recommend 24 GB of memory with four cores. At a minimum, two CPU cores are recommended because the developer environment contains many components that may be running concurrently. The components include the AOS web application, Visual Studio, Management Reporter, and SQL Server.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
