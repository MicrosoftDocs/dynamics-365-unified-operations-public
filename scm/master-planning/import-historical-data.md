---
# required metadata

title: Import historical data for demand forecast
description: In order to get accuracy of demand forecast accuracy, you need historical demand per item or item allocation ke. Use data entities to import historical demand data from any systems to keep a longer history of demand forecast data.
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

# Import historical data for demand forecast

[!include[banner](../includes/banner.md)]


In order to get accuracy of demand forecast accuracy, you need as much historical demand per item or item allocation key as possible. If the historical demand data are not imported, use the **Historical external demand#** (ReqDemPlanHistoricalExternalDemandEntity) data entity in Microsoft Dynamics 365 for Finance and Operations, Enterprise Edition.

Navigate to the **Data management workspace** to get an overview of all the fields in the entity.

1. Click the **Data entities** tile.
2. Search the entity list for **Historical external demand**.
3. Click **Target fields**. The mandatory entity fields are: site (**DeliveringSiteId**), date (**DemandDate**), quantity (**DemandQuantity**), and either the item number (**ItemNumber**) or the item allocation key (**ProductAllocationKeyId**).

In order to use the data entity, prepare a Microsoft Excel file or CSV file with the historical demand. You can use this file as an example: HistoricalDemandData . The file contains the historical demand of item D0001 and only the mandatory fields: site, quantity and the demand date.

You can import the data file by following these steps:

Select the company to which you want to import the historical demand.
Go to the Data management workspace.
Click the Import tile.
Provide a name for the import project for example, Import historical demand for item D0001.
Set the Source data format to the file format. If you import the example file, select CSV.
Select the Historical external demand entity in the Entity name field.
Save the example file to your machine and upload it.
Click Import.
The Execution summary page opens automatically. Verify the imported data on the page.
After you have imported the historical demand forecast, you can generate forecast as described in Generating a statistical baseline forecast.







