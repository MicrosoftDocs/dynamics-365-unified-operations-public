---
# required metadata

title: Development system requirements | Microsoft Docs
description: This wiki lists the system requirements for development.
author: RobinARH
manager: AnnBe
ms.date: 2016-02-09 21:11:24
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# keywords: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: 61
ms.suite: Released- Dynamics AX 7.0.0
# ms.tgt_pltfrm: 
ms.custom: 33221
ms.assetid: ddeeaebf-e6b3-4adf-822a-25c2c965ea0c
ms.region: Global
# ms.industry: 
ms.author: robadawy

---

# Development system requirements

This wiki lists the system requirements for development.

Development environments can be hosted locally or in Microsoft Azure. The build process, X++ compilation and generation of cross reference information, will typically run satisfactorily on machines with 16 GB of memory and 2 CPU cores. However, the compiler will use available resources, so more RAM and more cores may translate into faster compilations, especially if there is contention for the resources from other processes running concurrently. In such cases, we recommend 24 GB of memory with 4 cores. At a minimum, 2 CPU cores are recommended because the developer environment contains many components that may be running concurrently, including the AOS web application, Visual Studio, Management Reporter, and SQL Server.

