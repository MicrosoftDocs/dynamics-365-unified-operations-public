---
# required metadata

title: Rename a local environment to enable access to Visual Studio Team Services | Microsoft Docs
description: Renaming a local development VMs is required in order to access a VSTS project across multiple machines.
author: MargoC
manager: AnnBe
ms.date: 2015-12-12 23:28:24
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
ms.custom: 25911
ms.assetid: d6eb97a5-de09-48a4-baa2-1349de3ac9b8
ms.region: Global
# ms.industry: 
ms.author: tabell

---

# Rename a local environment to enable access to Visual Studio Team Services

Renaming a local development VMs is required in order to access a VSTS project across multiple machines.

Visual Studio Team Services (VSTS) (formerly known as Visual Studio Online or VSO) is needed for version control. In development topologies, multiple VMs cannot access the same VSTS project if they have the same machine name. VSTS uses the machine name for identification. If you are developing on local VMs downloaded from Microsoft Lifecycle Services (LCS), you may encounter issues.

-   To work around this, rename and reboot the machine before you start development, then connect to VSTS.
-   After you do this you will also need to configure the SQL Server Reporting Server. To do that, change the SQL Server Name to (localhost) in the SQL Server Report Server Database connection string.

  [![4](./media/4.png)](./media/4.png)

