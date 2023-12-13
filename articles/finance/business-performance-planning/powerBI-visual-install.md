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
# Install business performance planning visuals

This article describes how to install business performance planning visuals. To fully use the Business performance planning application, you must also install Microsoft Power BI visuals. For more information about how to install Power BI visuals, see [Power BI visuals](/power-bi/developer/visuals).

## Prerequisites for the installation of Power BI visuals

1. Import business performance planning visuals from [Microsoft AppSource](https://appsource.microsoft.com). For more information, see [Import visuals](/power-bi/developer/visuals/import-visual).
2. Connect Power BI to your Dataverse environment. For more information, see [Connect to Dataverse using a Connector](/power-apps/maker/data-platform/data-platform-powerbi-connector?tabs=Dataverse#connect-to-dataverse-using-a-connector) or [Use Direct Query in Power BI Desktop](/power-bi/connect-data/desktop-use-directquery).
3. To work with the visuals and publish to a Power BI workspace, a Power BI Premium licnese is required.  For more information, see [Licenses and subscriptions for business users](https://learn.microsoft.com/en-us/power-bi/consumer/end-user-license)

### Recommendations

- We recommend that you connect to SQL Server by using Direct Query. Then, after the cube is selected, enable the **Load selected tables** option to automatically select any dimension tables that are used in the cube.
- The names of planning cube tables have the "msdyn\_xpnacube" prefix, and the names of planning dimension tables have the "msdyn\_xpnadim" prefix. Use these prefixes to search for the cube or dimensions when you connect via SQL Server and Direct Query.
- After the cube is selected on the **Navigator** page, select **Select related tables** to automatically load data relationships between the cube and the dimension into Power BI.

## Installation

1. Open Power BI, and select the workspace or report where you intend to configure the visual.
2. Confirm that the visual was downloaded from AppSource.
3. Position the visual by dragging it onto the report canvas.
4. Select the visual on the report canvas, and then select the **Format visual** tab on the report canvas. In the **API Details** window for the visual, add your API base URL. This information provides the details that business performance planning requires to read data from the cube and write data to it. The API base URL is the URL of the environment where business performance planning is installed. The environment URL must be preceded by **https://** (for example, `https://environment.d365.com`). For more information, see [Find your environment and organization ID and name](/power-platform/admin/determine-org-id-name).

    > [!NOTE]
    > The **Format visual** tab is available only when a visual is selected on the report canvas.

5. Optional: You might have to add a **Cube name** or **Table name** value in the **API Details** window for the visual.
