---
# required metadata

title: AX 2009 upgrade - Create definitions
description: This topic provides information about how to create package templates that you can use to migrate data from Dynamics AX 2009 to Finance and Operations.
author: kfend
manager: AnnBe
ms.date: 06/26/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form:  
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope:  Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
# ms.search.industry:
ms.author: kfend
ms.search.validFrom: 2018-06-21
ms.dyn365.ops.version: Platform update 17
---

# AX 2009 upgrade - Create definitions

[!include [banner](../includes/banner.md)]

When you create a definition for migration, you determine which entities should be packaged and exported together, and then put all of the entities together in a migration group. A migration group is a set of entities that must be processed in a sequence, or that can logically be grouped together. The entities in a migration group are exported together from the source to staging or directly to file package. In a migration group, you also associate legal entities. Migration groups must be set up before you begin the export process.

Complete the following steps to create a migration group.

1.	Data Management  
2.	Create Migration group 
3.	Select required entity for export 
4.	If required fill the gap for field mapping. 
5.	Apply sequence 
6.	If required, please set conversion rule or default value for data manipulation.

