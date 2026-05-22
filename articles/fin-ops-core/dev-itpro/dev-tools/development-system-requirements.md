---
title: Development system requirements
description: Learn about the system requirements for development, which can be hosted locally or in Microsoft Azure. System requirements are provided for both environments.
author: josaw1
ms.author: josaw
ms.topic: article
ms.date: 03/03/2026
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: f39dbe39-7dc3-463c-923e-f22af231b979
---

# Development system requirements

[!include [banner](../includes/banner.md)]

This article lists the system requirements for development.

You can host development environments locally or in Microsoft Azure. The build process, X++ compilation, and generation of cross reference information, typically run satisfactorily on machines with 16 GB of memory and two CPU cores. The compiler uses available resources, so more RAM and more cores can speed up compilation, especially if other concurrent processes contend for the resources. If you're running concurrent processes, use 24 GB of memory with four cores. At a minimum, use two CPU cores because the developer environment contains many components that might run concurrently. The components include the AOS web application, Visual Studio, Management Reporter, and SQL Server.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
