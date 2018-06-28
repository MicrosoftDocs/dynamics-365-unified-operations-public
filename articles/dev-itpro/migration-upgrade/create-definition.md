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

1. In Dynamics AX 2009, from the navigation pane, click **Data Migration** > **Common forms** > **Create migration group**.
2. On the **Migration group** form, click CTRL+N or the **New** icon, to create a new migration group.  
3. Enter a name for the migration group, tab to the **Company** field, and then click **Select company**.
4. On the **Select company accounts** form, select one or more companies to add ot the migration group and then click **OK**.
5. On the **Migration group** form, click **Entity** and select the lines to be included in the migration. 
6. If needed, fill in any gaps in for field mapping. 
5. Click **Apply sequence** and then close the form.  


