---
# required metadata

title: Import historical data for demand forecasts
description: To get accurate demand forecasts, you require historical demand data per item or item allocation key. This topic explains how to use data entities to import historical demand data from any system, so that you have a longer history of demand forecast data.
author: YuyuScheller
manager: AnnBe
ms.date: 05/10/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form:  ReqDemPlanCreateForecastDialog
audience: Application User
# ms.devlang: 
# ms.reviewer: YuyuScheller
# ms.search.scope: AX 7.0.0, Operations, Core
# ms.tgt_pltfrm: 
# ms.custom: 
ms.assetid: 59c0d269-9db0-48e7-b8c7-9a388781a9ca
ms.search.region: Global
# ms.search.industry: Manufacturing
ms.author: roxanad
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: AX 7.0.0

---

# Import historical data for demand forecasts

[!include[banner](../includes/banner.md)]

To help guarantee the accuracy of demand forecasts, you must have as much historical demand data as you can get per item or item allocation key. If the historical demand data isn't already imported, use the **Historical external demand** (ReqDemPlanHistoricalExternalDemandEntity) data entity in Microsoft Dynamics 365 for Operations to import it.

In the **Data management** workspace, you can see an overview of all the fields in the entity.

1. Open the **Data management** workspace.
2. Click the **Data entities** tile.
3. Search the entity list for **Historical external demand**.
4. Click **Target fields**. The following entity fields are mandatory: site (**DeliveringSiteId**), date (**DemandDate**), quantity (**DemandQuantity**), and either item number (**ItemNumber**) or item allocation key (**ProductAllocationKeyId**).

To use the data entity, you must have a Microsoft Excel file or comma-separated values (CSV) file that contains the historical demand data. The following example shows how to import the data from a CSV file.

## Example

You can use the following file as an example: HistoricalDemandData. This file contains the historical demand data for item D0001. It contains only the following mandatory fields: site, quantity, and the demand date.

1. Select the company to import the historical demand data into.
2. Open the **Data management** workspace.
3. Click the **Import** tile.
4. Enter a name for the import project, such as **Import historical demand for item D0001**.
5. In the **Source data format** field, select the file format of the file that you're importing. To import the HistoricalDemandData file for this example, select **CSV**.
6. In the **Entity name** field, select **Historical external demand**.
7. Save the file to your computer, and then upload it.
8. Click **Import**.
9. The **Execution summary** page is opened automatically. Verify the imported data on the page.

After you've imported the historical demand data, you can generate a demand forecast.

## See also

[Generate a statistical baseline forecast](generate-statistical-baseline-forecast.md)
