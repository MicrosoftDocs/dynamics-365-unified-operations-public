---
# required metadata

title: Import Electronic Reporting configurations
description: How to import Electronic reporting (ER) configurations from LCS to an on-prem application
author: kfend
manager: AnnBe
ms.date: 06/02/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

ms.search.form: ERSolutionTable, ERWorkspace, ERSolutionRepositoryTable, ERSolutionImport
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: annbe
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.custom: 27621
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: nselin
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Import Electronic Reporting configurations

This topic explains how to download Electronic reporting (ER) configurations from Microsoft Dynamics Lifecycle Services (LCS) to an application that is deployed on-prem and how to upload the ER configurations to the on-prem application from LCS.

1.  Sign in to your on-prem application using one of the following roles:
    * Electronic reporting developer
    * Electronic reporting functional consultant
    * System administrator
2.	Go to **Organization administration > Electronic reporting**.
3.	In the **Configuration providers** section, select the tile of ER provider that is associated with your company.
    
    **Note**: Play the **Create a configuration provider and mark it as active** task guide to learn how a new ER solution provider can be registered.
4.	On the selected tile, click **Repositories**.

    ![Picture 1](media/ger-providers-tiles.png)

5.	On the **Configuration repositories** page, in the grid, select the existing repository of the **FILE SYSTEM** type. If this repository doesn't appear in the grid, follow these steps:
    1. Click **Add** to add a new repository.
    2. Select **FILE SYSTEM** as the repository type.
    3. Click **Create repository**.
    4. Enter a name and description for the repository.
    5. Enter a path of the work directory pointing to a folder of the local file system where the belonging to this repository ER configurations will be stored.
    6. Click **OK** to confirm the new repository entry.
6.	In the grid, select the new repository of the **FILE SYSTEM** type.

    ![Picture 2](media/ger-file-repository.png)
    
7.	In another tab of using web browser, login to LCS.
    * Open the Shared asset library.
    * Select the **GER configuration** asset type.
    * Click **DOWNLOAD ALL**.

    ![Picture 3](media/ger-lcs-shared-asset-library.png)
    
    **Note**: All ER configurations will be placed to a zipped file that will be downloaded from LCS.
    
8.	Open the downloaded zipped file, select all ER configurations in it and copy them to the folder that has been defined as a work directory for entered repository of the **FILE SYSTEM** type.
9.	In the Dynamics 365 for Operations tab on the ER repositories form, click **Open** to view the list of ER configurations for the selected repository of the **FILE SYSTEM** type.
10.	In the configurations tree in the left pane, select the ER configuration that you require.
11.	On the **Versions** FastTab, select the required version of the selected ER configuration.
12.	Click **Import** to download the selected version from this repository to the current Dynamics 365 for Operations instance. 

    **Note**: The **Import** button is unavailable for ER configuration versions that are already presented in the current Dynamics 365 for Operations instance. 

**Note**: Depending on the ER settings, configurations are validated after they are imported. You might be notified about any inconsistency issues that are discovered. You must resolve those issues before you can use the imported configuration version. For more information, see the list of related articles for this topic. 

## Frequently asked questions

**Q**: Why did I get the warning “Zip generation is in progress, please try again in a few minutes.” instead of downloaded zip file after clicking **DOWNLOAD ALL** in the Shared asset library for the **GER configurations** asset type?

**A**: It happened since a new configuration has been added to the Shared asset library and the archiving of GER configurations is in progress.

