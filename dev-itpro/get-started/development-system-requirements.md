---
# required metadata

title: Development system requirements
description: This wiki lists the system requirements for development.
author: RobinARH
manager: AnnBe
ms.date: 2016-02-09 21 - 11 - 24
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
# ms.reviewer: 61
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 33221
ms.assetid: f43a9e3e-0d41-4418-b5d4-05f43d273aea
ms.search.region: Global
# ms.search.industry: 
ms.author: robadawy
ms.dyn365.intro: Feb-16
ms.dyn365.version: AX 7.0.0

---

# Development system requirements

This wiki lists the system requirements for development.

Development environments can be hosted locally or in Microsoft Azure. The build process, X++ compilation and generation of cross reference information, will typically run satisfactorily on machines with 16 GB of memory and 2 CPU cores. However, the compiler will use available resources, so more RAM and more cores may translate into faster compilations, especially if there is contention for the resources from other processes running concurrently. In such cases, we recommend 24 GB of memory with 4 cores. At a minimum, 2 CPU cores are recommended because the developer environment contains many components that may be running concurrently, including the AOS web application, Visual Studio, Management Reporter, and SQL Server.

