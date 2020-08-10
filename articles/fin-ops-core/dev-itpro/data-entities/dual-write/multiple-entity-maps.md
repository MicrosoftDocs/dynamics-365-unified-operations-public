---

title: Handling multiple entity maps
description: This article describes how to select multiple entity maps, view a list of dependent entity maps, enable the entity maps and all of its related entities, and copy pre-existing data.
author: sabinn-msft
manager: AnnBe
ms.date: 08/10/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: v-douklo
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.custom:
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: sabinn
ms.search.validFrom: 2020-08-10
ms.dyn365.ops.version: AX 7.0.0
---

# Handling multiple entity maps

[!include [banner](../../includes/banner.md)]


As part of day to day operations, there may be a need to bulk handle entity maps. For example, you may want to simultaneously enable or pause a set of entity maps. Earlier you had to do this one by one, which is cumbersome and time consuming. You can now enable, pause, resume, or stop more than one entity map at the same time.

![Selecting multiple entity maps](media/select-multiple-entity-maps.png)
 
As part of enabling multiple entity maps, you also get to view the list of all the dependent entity maps by selecting **Show related entity map(s)**.

![Show related entity maps](media/show-related-entity-map.png)
 
To enable the selected entity map and all its related entities, select **Run** in the dialog box. If you want to copy the pre-existing data for the selected entity maps or its dependents, select the corresponding **Initial sync** checkbox. Alternatively, remove one or more of the related entities by clearing the corresponding checkbox. You can also drag and drop the entity maps to change the order that they'll be synced in.
