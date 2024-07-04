---
title: Configure the Azure DevOps mapping during code migration
description: Learn about how to map your development box to the Azure DevOps project after the LCS code upgrade service has completed.
author: sericks007
ms.author: sericks
ms.topic: article
ms.date: 01/10/2022
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
---

# Configure the Azure DevOps mapping during code migration

[!include [banner](../includes/banner.md)]

This tutorial shows how to map your development box to the Azure DevOps project after the Lifecycle Services (LCS) code upgrade service has completed. 

The LCS code upgrade service automatically checks your upgraded code into Azure DevOps. You will then need to map your development box to the upgrade folder/branch in your Azure DevOps project (The name of the upgrade folder/branch depends on the version you migrated to). Within your upgraded folder, you will find three folders:

- Export
- Metadata
- Projects

## Key concepts
- **Export** is the project that contains the XML files after exporting from Microsoft Dynamics AX 2012. This project is your metadata in XML format before it is upgraded. This project is only relevant if you are upgrading from Dynamics AX 2012.
- **Metadata** is your upgraded code (metadata XML file).
- **Projects** are solutions that you can use during upgrade. One solution, CodeMergeSolution, is the solution that contains projects with the elements that have conflicts and need to be resolved. Another solution, UpgradedSolution, contains a collection of projects, one for each upgraded model.

## Map Azure DevOps to your development box
1.  In Visual Studio, open the **Team Explorer** window by selecting **View &gt; Team Explorer** from the top menu.
2.  In the **Team Explorer** window, select **Connect**, and then select **Manage Connections > Connect to a Project**.
3.  Follow the prompts to connect. From the list of available projects for your account, choose the project that you want to work on. Select **Connect**.
4.  Now you need to map your workspace to the Azure DevOps folders. Go to the **Source Code Explorer** and do this mapping:
    1.  Projects &gt;
        - Select a folder where you plan to save your projects, or use the default **Visual Studio** folder: C:\\Users\\&lt;username&gt;\\source\\repos
    2.  Metadata &gt; C:\\AOSService\\PackagesLocalDirectory
        -   On cloud VMs, this folder is located on the I:\\, J:\\ or K:\\ drive
        -   **Important**:
            -   If you are migrating from Dynamics AX 2012 R3 or earlier, you will be mapping to the metadata folder under the **Main** branch.
            -   If you are migrating between two product versions, you will be mapping to the metadata folder under one of the **Releases** branch.

[![vstsmapping.](./media/vstsmapping.png)](./media/vstsmapping.png) 

After you have mapped these folders, you can synchronize the code to your local box. Right-click **Metadata** and select **Get latest**. Similarly synchronize the Projects folder. After synchronizing the metadata folder, refresh your models in Visual Studio from **Finance and operations** &gt; **Model Management** &gt; **Refresh Models**. [![VSRefreshModels.](./media/vsrefreshmodels.png)](./media/vsrefreshmodels.png) You are now ready to open your projects, resolve conflicts, build, test, and complete your code migration.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]

