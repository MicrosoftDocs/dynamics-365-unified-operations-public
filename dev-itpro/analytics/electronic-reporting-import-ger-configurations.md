---
# required metadata

title: Import Electronic Reporting configurations
description: Import Electronic reporting (ER) configurations from LCS to a local business data application.
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

This topic explains how to download Electronic reporting (ER) configurations from Microsoft Dynamics Lifecycle Services (LCS) to a local business data application  and how to upload the ER configurations to the local business data application from LCS.

1.  Sign in to your local business data application using one of the following roles:
    * Electronic reporting developer
    * Electronic reporting functional consultant
    * System administrator
2.	Go to **Organization administration > Electronic reporting**.
3.	In the **Configuration providers** section, select the tile of ER provider that is associated with your company.
    
    **Note**: To learn how to register a new ER solution provider, play the **Create a configuration provider and mark it as active** task guide.
4.	On the selected tile, click **Repositories**.

    ![Picture 1](media/ger-providers-tiles.png)

5.	On the **Configuration repositories** page, in the grid, select the existing repository of the **FILE SYSTEM** type. If the repository doesn't appear in the grid, complete the follwoing steps:
    1. Click **Add** to add a new repository.
    2. Select **FILE SYSTEM** as the repository type.
    3. Click **Create repository**.
    4. Enter a name and description for the repository.
    5. Enter a path of the work directory pointing to a folder of the local file system where the belonging to this repository ER configurations will be stored.
    6. Click **OK** to confirm and save the new repository.
6.	In the grid, select the new repository of the **FILE SYSTEM** type.

    ![Picture 2](media/ger-file-repository.png)
    
7.	In your browser, open another tab and log in to LCS.
8. In the **Shared asset** library, select the **GER configuration** asset type, and then click **Download all**.

    ![Picture 3](media/ger-lcs-shared-asset-library.png)
    
    **Note**: All of the ER configurations will be placed into a zipped file for download.
    
9.	Open the file, select all of the ER configurations, and then copy them to the working directory for the **FILE SYSTEM** type repository.
10.	On the **Dynamics 365 for Operations** tab on the **ER repositories** form, click **Open** to view the list of ER configurations for the selected repository.
11.	In the **Configurations** tree in the left pane, select an ER configuration.
12.	On the **Versions** FastTab, select the required version of the ER configuration.
13.	Click **Import** to download the selected version from this repository to the current Dynamics 365 for Operations instance. 

    **Note**: The **Import** button is unavailable for existing ER configuration versions. 

**Note**: Depending on the ER settings, configurations are validated after they are imported. You may be notified regarding inconsistencies or issues that are discovered. These must be resolved before you can use the imported configuration version. For more information, see the list of related articles for this topic. 

## Frequently asked questions

**Q**: Why did I get the warning “Zip generation is in progress, please try again in a few minutes.” when I clicked **DOWNLOAD ALL** in the **Shared asset** library?

**A**: Because a new configuration is added to the **Shared asset** and the GER configuration is being archived.

