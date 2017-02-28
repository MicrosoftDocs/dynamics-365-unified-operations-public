---
# required metadata

title: Database synchronization
description: This wiki provides information about the importance of not synchronizing tables and views until they are fully compiled. 
author: RobinARH
manager: AnnBe
ms.date: 2015-12-12 23 - 28 - 35
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
ms.custom: 25931
ms.assetid: f1880ca8-b30a-40c8-9bc2-660414b31346
ms.search.region: Global
# ms.search.industry: 
ms.author: robadawy
ms.dyn365.ops.intro: 01-02-2016
ms.dyn365.ops.version: AX 7.0.0

---

# Database synchronization

This wiki provides information about the importance of not synchronizing tables and views until they are fully compiled. 

Tables and views cannot be synchronized against the database until they are fully compiled. After you complete a full build of the Application Platform, Application Foundation, and Application Suite, you can complete a Database Synchronization from the Dynamics 365 menu in Visual Studio. **Note**: If you try to synchronize the database before you have fully compiled assemblies, the Visual Studio database synchronization tool will display a message that synchronization has completed successfully, when in fact, the synchronization was not successful.

