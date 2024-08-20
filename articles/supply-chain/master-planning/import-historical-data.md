---
title: Import historical data for demand forecasts
description: Learn how to use data entities to import historical demand data from any system, so that you have a longer history of demand forecast data.
author: t-benebo
ms.author: benebotg
ms.topic: article
ms.date: 05/10/2017
ms.custom: 
ms.reviewer: kamaybac
ms.search.form:  ReqDemPlanCreateForecastDialog
ms.assetid: 59c0d269-9db0-48e7-b8c7-9a388781a9ca
---

# Import historical data for demand forecasts

[!include [banner](../includes/banner.md)]
[!INCLUDE [demand-planning-banner](../includes/demand-planning-banner.md)]

To help guarantee the accuracy of demand forecasts, you must have as much historical demand data as you can get per item or item allocation key. If the historical demand data isn't already imported, use the **Historical external demand** (ReqDemPlanHistoricalExternalDemandEntity) data entity in Dynamics 365 Supply Chain Management to import it.

In the **Data management** workspace, you can see an overview of all the fields in the entity.

1. Open the **Data management** workspace.
2. Select the **Data entities** tile.
3. Search the entity list for **Historical external demand**.
4. Select **Target fields**. The following entity fields are mandatory: site (**DeliveringSiteId**), date (**DemandDate**), quantity (**DemandQuantity**), and either item number (**ItemNumber**) or item allocation key (**ProductAllocationKeyId**).

To use the data entity, you must have a Microsoft Excel file or comma-separated values (CSV) file that contains the historical demand data. The following example shows how to import the data from a CSV file.

For more information about how to import data, including how to clean up data after an import, see [Data import and export jobs overview](../../fin-ops-core/dev-itpro/data-entities/data-import-export-job.md) and its related articles.

Learn more in [Generate a statistical baseline forecast](generate-statistical-baseline-forecast.md).

[!INCLUDE[footer-include](../../includes/footer-banner.md)]