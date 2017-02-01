---
# required metadata

title: Cost object dimensions | Microsoft Docs
description: When you analyze costs, you use cost element dimensions to determine where costs flow to. You use cost object dimensions to determine where you should assign costs. This topic provides information about cost object dimensions.
author: YuyuScheller
manager: AnnBe
ms.date: 2016-11-01 13:17:57
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

keywords: CAMDimensionMember
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: 2094
ms.suite: Released- Dynamics 365 for Operations version 1611
# ms.tgt_pltfrm: 
ms.custom: 223174
ms.assetid: 275efd15-6be2-4305-9e64-91dd2373a601
ms.region: global
ms.industry: Manufacturing
ms.author: yuyus

---

# Cost object dimensions

When you analyze costs, you use cost element dimensions to determine where costs flow to. You use cost object dimensions to determine where you should assign costs. This topic provides information about cost object dimensions.

A cost object can be any type of object that you want to estimate, allocate costs to, or measure directly. Typical cost objects include products, projects, resources, departments, cost centers, and geographical regions. Management uses cost objects to quantify costs and also to drive profitability analysis.

## Cost object dimensions and cost object dimension members
Cost objects are known as *cost object dimensions*. After you’ve decided which entity the cost object dimension should refer to, you must specify the individual dimension values or import them into Cost accounting from other source systems. These individual dimension values are known as *cost object dimension members*. For example, you want to use the financial dimension that is named Cost center as the cost object dimension. To see how costs flow to the individual cost centers, you must import the cost object dimension members. In this case, the cost object dimension members are the actual cost centers, such as Sales, Production, Administration, and Geographic locations. The following screenshot shows an example of Cost Centers as the cost object dimension with its actual cost centers as cost object dimension members. [![cost-object-dimensions](./media/cost-object-dimensions.png)](./media/cost-object-dimensions.png)

## Import cost object dimension members through data connectors
To make the import of cost object dimension members easier, you use data connectors to retrieve the values from the entities that you want to use as cost object dimensions. You can use either the pre-built data connectors or custom data connectors that you build.

