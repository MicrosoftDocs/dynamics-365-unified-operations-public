---
title: Install business performance planning visuals
description: Learn how to install business performance planning visuals, including prerequisites and a step-by-step process for connecting your data.
author: ShielaSogge
ms.author: twheeloc
ms.topic: article
ms.date: 08/10/2024
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2023-12-03
ms.search.form: 
ms.dyn365.ops.version: 
---

# Install business performance planning visuals

This article describes how to install business performance planning visuals. To fully use the Business performance planning application, you must also install Microsoft Power BI visuals. For more information about how to install Power BI visuals, see [Power BI visuals](/power-bi/developer/visuals).

## Prerequisites for the installation of Power BI visuals

1. Import business performance planning visuals from [Microsoft AppSource](https://appsource.microsoft.com). For more information, see [Import visuals](/power-bi/developer/visuals/import-visual).
2. Connect Power BI to your Dataverse environment. For more information, see [Use Direct Query in Power BI Desktop](/power-bi/connect-data/desktop-use-directquery).
3. To work with the visuals and publish to a Power BI workspace, a Power BI license is required. For more information, see [Licenses and subscriptions for business users](/power-bi/consumer/end-user-license).
4. You must have authentication for Power BI enabled for the visuals to work. For more information, see [Obtain Microsoft Entra access token](/fabric/admin/organizational-visuals#obtain-microsoft-entra-access-token).
5. When you connect to a cube in Power BI, you must select SQL Server as the data source.


    > [!NOTE]
    > - You must have the AppSource Custom Visuals SSO feature enabled in step 4. If this feature isn't enabled, you receive the following error: **Unable to authenticate to Dataverse service**.
    > - In step 5, don't use Dataverse connector, because there are limits on the import of data that has logical names. This data is required for visual write-back functionality.

## Connect to your data

When you connect to the data in Power BI, you must select SQL Server as the data source.

To select SQL Server as a data source, follow these steps.

1. In Power BI, go to **Get data**, or select **SQL Server**, or select **SQL Server** on the ribbon.
2. After you select SQL Server as the data source, set the data connectivity mode to **Direct query**.
3. After you select the cube, enable the **Load selected tables** option to automatically select any dimension tables that are used in the cube.
4. If you're prompted to sign in, on the **Microsoft account** tab, select **Sign in**.
5. At the top of the **Navigator** page, search for your cube.

    > [!NOTE]
    > The names of planning cube tables have the "msdyn\_xpnacube" prefix, and the names of planning dimension tables have the "msdyn\_xpnadim" prefix. If you're unsure of the name of your cube, go to **Business performance planning**, and select the cube to add.

6. In the cube properties section, copy the **Write back** table name, and enter it in the search bar at the top of the **Navigator** page.
7. After the cube is found on the **Navigator** page, select the checkbox to the left of the cube name.
8. At the bottom of the **Navigator** page, select **Select related tables** to import the entire data model. (This import brings in all the dimensions in the cube.)
9. After all the dimensions in the cube have a check mark next to them, select **Load**. This operation might take a few minutes. After it's completed, your data appears in the **Data** view in Power BI.

### Recommendations

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
