---
# required metadata

title: Database synchronization | Microsoft Docs
description: This wiki provides information about the importance of not synchronizing tables and views until they are fully compiled. 
author: RobinARH
manager: AnnBe
ms.date: 2015-12-12 23:28:35
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
ms.custom: 25931
ms.assetid: 8521ded8-b50e-4fc7-8563-48c60d8563d9
ms.region: Global
# ms.industry: 
ms.author: robadawy

---

# Database synchronization

This wiki provides information about the importance of not synchronizing tables and views until they are fully compiled. 

Tables and views cannot be synchronized against the database until they are fully compiled. After you complete a full build of the Application Platform, Application Foundation, and Application Suite, you can complete a Database Synchronization from the Dynamics 365 menu in Visual Studio. **Note**: If you try to synchronize the database before you have fully compiled assemblies, the Visual Studio database synchronization tool will display a message that synchronization has completed successfully, when in fact, the synchronization was not successful.

