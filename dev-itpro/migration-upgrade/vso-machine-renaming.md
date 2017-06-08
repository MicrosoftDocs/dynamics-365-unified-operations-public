---
# required metadata

title: Rename a local environment to enable access to Visual Studio Team Services
description: Renaming a local development VMs is required in order to access a VSTS project across multiple machines.
author: MargoC
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
# ms.reviewer: 61
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 25911
ms.assetid: 4f5ff29b-9ae5-4ba2-8b6e-1e5d94e004b3
ms.search.region: Global
# ms.search.industry: 
ms.author: tabell
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Rename a local environment to enable access to Visual Studio Team Services

[!include[banner](../includes/banner.md)]


Renaming a local development VMs is required in order to access a VSTS project across multiple machines.

Visual Studio Team Services (VSTS) (formerly known as Visual Studio Online or VSO) is needed for version control. In development topologies, multiple VMs cannot access the same VSTS project if they have the same machine name. VSTS uses the machine name for identification. If you are developing on local VMs downloaded from Microsoft Lifecycle Services (LCS), you may encounter issues.

-   To work around this, rename and reboot the machine before you start development, then connect to VSTS.
-   After you do this you will also need to configure the SQL Server Reporting Server. To do that, change the SQL Server Name to (localhost) in the SQL Server Report Server Database connection string.

  [![4](./media/4.png)](./media/4.png)



