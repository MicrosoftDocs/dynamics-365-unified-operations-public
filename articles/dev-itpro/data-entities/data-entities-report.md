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

## Configuration entity spreadsheets
Configuration entity spreadsheets are released as part of configuration data packages on Microsoft Dynamics Lifecycle Services (LCS). Configuration entity spreadsheets contain best practice data that you can use to create an initial golden build of a Finance and Operations implementation. The data entities in the data packages are also sequenced appropriately to help guarantee a successful single-click import of the data. We recommend that you download and review the configuration entity spreadsheets to understand how we recommend that you order your data imports. For more information, see [Configuration data packages](configuration-data-packages.md).

## Data entity reports
Microsoft provides the following reports for data entities, which can be downloaded from [Technical reference reports](https://mbs.microsoft.com/customersource/northamerica/AX/downloads/reports/axtechrefrep): 
- **Data entities** (Analysis-AxDataEntitiesV2) lists each data entity that is available. The report indicates the data source of the entity and the fields included in the entity. The report also indicates whether the data entity is public.
- **Data entities fields** (Analysis-AxDataEntityFieldsV2) lists each field in a data entity, and the table that it originates from.
- **Aggregate data entities** (Analysis-AxAggregateDataEntitiesV2) lists the aggregate data entities, and the fields that each contains. 

You may also find the Tables report of interest--it lists each table, and its table group. (Analysis-AxTablesReportV2).  


## See also
[Data entities home page](data-entities.md).
