---
# required metadata

title: Allocation bases
description: Allocation bases are key components in Cost accounting and mostly used to allocate overhead costs. Every allocation base used is the basis for overhead costs being assigned to departments. 
author: YuyuScheller
manager: AnnBe
ms.date: 05/24/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

ms.search.form: CAMDimensionMember
# ROBOTS: 
audience: Application User
# ms.devlang: 
# ms.reviewer: YuyuScheller
ms.search.scope: Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 223174
ms.assetid: 
ms.search.region: global
ms.search.industry: Manufacturing
ms.author: YuyuScheller
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611

---

# Allocation bases 

[!include[banner](../includes/banner.md)]

An allocation base is the basis upon which Cost accounting allocates its overhead costs. An allocation base can be a quantity, for example, machine hours used, kilowatt hours consumed, or square footage occupied. Allocation bases are mostly used to assign overhead costs to produced inventory.

Here are a few examples of allocation bases:
-	An IT department allocates its expenses based on the number of personal computers used by each department.
-	A janitorial department allocates its expenses based on the square footage occupied by each department.
-	A human resources department allocate its expenses based on the number of employees working in each department.

# Typical allocation process 
The typical allocation process starts xxx  

There are three types of allocation bases in Cost accounting:
-	Predefined dimension member allocation bases
-	Hierarchy allocation bases
-	Formula allocation bases

## Predefined dimension member allocation bases

The predefined dimension member allocation bases are created automatically by the system when a dimension member is created. This applies to 
- Statistical dimension members 
- Cost element dimension members


[!NOTE] The predefined dimension member allocation bases that are based on a cost element dimension member only consider the values from the data source provider, for example, general ledger or budget.


## Hierarchy allocation bases


## Formula allocation bases









Cost objects are known as *cost object dimensions*. After you’ve decided which entity the cost object dimension should refer to, you must specify the individual dimension values or import them into Cost accounting from other source systems. These individual dimension values are known as *cost object dimension members*. For example, you want to use the financial dimension that is named Cost center as the cost object dimension. To see how costs flow to the individual cost centers, you must import the cost object dimension members. In this case, the cost object dimension members are the actual cost centers, such as Sales, Production, Administration, and Geographic locations. The following screenshot shows an example of Cost Centers as the cost object dimension with its actual cost centers as cost object dimension members. 

[![cost-object-dimensions](./media/cost-object-dimensions.png)](./media/cost-object-dimensions.png)

## Import cost object dimension members through data connectors
To make the import of cost object dimension members easier, you use data connectors to retrieve the values from the entities that you want to use as cost object dimensions. You can use either the pre-built data connectors or custom data connectors that you build.
