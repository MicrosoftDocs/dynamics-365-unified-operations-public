---
title: Find information about standard data entities
description: This article describes how to get information about the standard data entities that are available and how to download the scripts to run the reports.
author: peakerbl
ms.date: 09/18/2020
ms.topic: article
ms.prod: 
ms.technology: 
audience: Developer, IT Pro
ms.reviewer: twheeloc
ms.search.region: Global
ms.author: peakerbl
ms.search.validFrom: 2016-05-31
ms.dyn365.ops.version: Platform update 1
ms.custom: 202654
ms.assetid: 6ec8ea87-ea1e-4a10-9d67-2b6565c5c62e
---

# Find information about standard data entities

[!include [banner](../includes/banner.md)]


[!INCLUDE [PEAP](../../../includes/peap-3.md)]

The application ships with many default data entities. Data entities are frequently updated, so for documentation, we rely on the data entity templates to indicate which order data entities should be imported in, and on reports for a list of data entities that ship with each release.

## Configuration data packages

Configuration data packages on Microsoft Dynamics Lifecycle Services (LCS) contain configuration entity spreadsheets. Configuration entity spreadsheets contain best practice data that you can use to create an initial golden build of an implementation. The data entities in the data packages are also sequenced appropriately using an XML file to help guarantee a successful single-click import of the data. We recommend that you download and review the configuration data packages to understand how we recommend that you order your data imports. For more information, see [Configuration data templates](configuration-data-templates.md) and [Copy configuration data between companies or legal entities overview](copy-configuration.md).

## Reports

Microsoft provides the following reports for data entities, which can be downloaded from [Technical reference reports](/dynamics/s-e/global/axtechrefrep_61):

- Aggregate data entities: Lists the aggregate data entities, and the fields that each contains.
- Aggregate measures: Lists the aggregate measures.
- Config keys: Lists the configuration keys. 
- Config key groups: Lists the configuration key groups.
- Data entities: Lists each data entity. The report indicates the data source of the entity and the fields included in the entity. The report also indicates whether the data entity is public.
- Data entities fields: Lists each field in a data entity, and the table that it originates from.
- KPIs: Lists the KPIs.
- License codes: Lists the license code associated with each configuration key.
- Menu items: Lists the menu items associated with each configuration key.
- SSRS reports: Lists each report. The report indicates the data set used for each report, as well as the filters and fields available on each report.
- Tables: Lists each table and its table group.
- Workflow type: Lists each type of workflow. The report also describes what each type of workflow is used for and indicates whether the workflows of each type are associated with a specific company in the organization or with the whole organization.

## Scripts

You can download the scripts to run these reports from [fin-ops-doc-scripts](https://github.com/microsoft/fin-ops-doc-scripts).

## Additional resources

[Data entities overview](data-entities.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
