---
# required metadata

title: Find information about standard data entities
description: This topic describes how to get information about the standard data entities that are available for Microsoft Dynamics 365 for Finance and Operations, Enterprise edition.
author: sericks007
manager: AnnBe
ms.date: 12/14/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.custom: 202654
ms.assetid: 6ec8ea87-ea1e-4a10-9d67-2b6565c5c62e
ms.search.region: Global
# ms.search.industry: 
ms.author: sericks
ms.search.validFrom: 2016-05-31
ms.dyn365.ops.version: Platform update 1

---

# Find information about standard data entities

[!include[banner](../includes/banner.md)]

Microsoft Dynamics 365 for Finance and Operations, Enterprise edition, ships with many default data entities. Data entities are frequently updated, so for documentation, we rely on the data entity templates to indicate which order data entities should be imported in, and on reports for a list of data entities that ship with each release.  

## Data entity templates

## Data entity reports
Microsoft provides the following reports for data entities, which can be downloaded from [Technical reference reports](https://mbs.microsoft.com/customersource/northamerica/AX/downloads/reports/axtechrefrep): 
- **Data entities** (Analysis-AxDataEntitiesV2) lists each data entity that is available. The report indicates the data source of the entity and the fields included in the entity. The report also indicates whether the data entity is public.
- **Data entities fields** (Analysis-AxDataEntityFieldsV2) lists each field in a data entity, and the table that it originates from.
- **Aggregate data entities** (Analysis-AxAggregateDataEntitiesV2) lists the aggregate data entities, and the fields that each contains. 

You may also find the Tables report of interest--it lists each table, and its table group. (Analysis-AxTablesReportV2).  


## See also
[Data entities home page](data-entities.md).
