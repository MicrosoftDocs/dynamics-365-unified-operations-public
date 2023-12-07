---
# required metadata

title: Install business performance planning visuals 
description: This article describes how to install business performance planning visuals.
author: ShielaSogge
ms.date: 12/07/2023
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 

# ms.tgt_pltfrm: 
ms.custom: 7521
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2023-12-03
ms.dyn365.ops.version: 

---
# Copy visual

This article describes how to install business performance planning visuals. You must also install Power BI visuals to fully use the planning application. To learn more about installing Power BI visuals, see [Power BI visuals](/power-bi/developer/visuals).


## PowerBI visual install

## Prerequisites

1.  Import business performance planning visuals from [Microsoft AppSource](https://appsource.microsoft.com). For more information, see [Import visuals](/power-bi/developer/visuals/import-visual)
2.  Connect PowerBI to your Dataverse environment. [Connect to Dataverse using a Connector](/power-apps/maker/data-platform/data-platform-powerbi-connector?tabs=Dataverse#connect-to-dataverse-using-a-connector) or [Use DirectQuery in Power BI Desktop](/power-bi/connect-data/desktop-use-directquery)

### Recommendations  
- It is recommended to connect to SQL Server using **Direct query**. When using direct query, after the cube is selected, there's an option to **Load selected tables**. Select this option will auto-select any dimension tables that are used in the cube.
- Planning cube tables will be prefixed with **msdyn_xpnacube** and planning dimension tables will be prefixed with **msdyn_xpnadim**. Use these prefixes to search for the cube and/or dimensions when connecting via SQL server and direct query.
- After the cube is selected in the **Navigator** page, click **Select related tables** for data relationships between the cube and the dimension to auto-load into Power BI.

## Installation 

1.  Open Power BI: Launch the Power BI application and access your desired workspace or report where you intend to configure the visual.
2.  Ensure that the visual has been downloaded from AppSource.  See Pre-requisite step 1 above.  
3.  Position the visual: Drag the visual to the report canvas.
4.  Add your **API Base URL** to the API Details window of the visual. This will provide business performance planning app the details it needs to read and write data from the Cube. To add the API details, select the **Format visual** tab in the report canvas.  The API base URL will be the Environment URL where planning has been installed.  The environment URL must be preceded by https://.  For example:  https://environment.d365.com. For more information about environment ID, see [Find your environment and organization ID and name](/power-platform/admin/determine-org-id-name)  Note:The visual must be selected in the report canvas for the Format visual tab to display.
5.  Optionally you may need to add your **Cube name** or **Table name** in the API Details window of the visual.



