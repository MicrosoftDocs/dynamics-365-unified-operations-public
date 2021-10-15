---
# required metadata

title: Cost object dimensions
description: When you analyze costs, you use cost element dimensions to determine where costs flow to. You use cost object dimensions to determine where you should assign costs. This topic provides information about cost object dimensions.
author: AndersGirke
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: CAMDimensionMember, CAMCostObject
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
# ms.tgt_pltfrm: 
ms.custom: 223174
ms.assetid: 2a1cdd35-30cb-41e7-9506-67fd04a537c5
ms.search.region: global
ms.search.industry: Manufacturing
ms.author: roschlom
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611

---

# Cost object dimensions

[!include [banner](../includes/banner.md)]

When you analyze costs, you use cost element dimensions to determine where costs flow to. You use cost object dimensions to determine where you should assign costs. This topic provides information about cost object dimensions.

A cost object can be any type of object that you want to estimate, allocate costs to, or measure directly. Typical cost objects include products, projects, resources, departments, cost centers, and geographical regions. Management uses cost objects to quantify costs and also to drive profitability analysis.

## Cost object dimensions and cost object dimension members
Cost objects are known as *cost object dimensions*. After you’ve decided which entity the cost object dimension should refer to, you must specify the individual dimension values or import them into Cost accounting from other source systems. These individual dimension values are known as *cost object dimension members*. For example, you want to use the financial dimension that is named Cost center as the cost object dimension. To see how costs flow to the individual cost centers, you must import the cost object dimension members. In this case, the cost object dimension members are the actual cost centers, such as Sales, Production, Administration, and Geographic locations. The following screenshot shows an example of Cost Centers as the cost object dimension with its actual cost centers as cost object dimension members. 

[![Screenshot showing Cost Centers as cost object dimension.](./media/cost-object-dimensions.png)](./media/cost-object-dimensions.png)

## Import cost object dimension members through data connectors
To make the import of cost object dimension members easier, you use data connectors to retrieve the values from the entities that you want to use as cost object dimensions. You can use either the pre-built data connectors or custom data connectors that you build.





[!INCLUDE[footer-include](../../includes/footer-banner.md)]