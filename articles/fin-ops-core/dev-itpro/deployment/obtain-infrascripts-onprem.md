---
# required metadata

title: Obtain the Infrastructure Scripts for your Microsoft Dynamics 365 Finance + Operations (on-premises) deployment
description: This article explains how to download or update the infrastructure scripts from one version to another.
author: faix
ms.date: 12/22/2022
ms.topic: article
ms.prod: dynamics-365 
ms.service:
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: osfaixat
ms.search.validFrom:
ms.dyn365.ops.version: 

---

# Obtain the Infrastructure Scripts for your Microsoft Dynamics 365 Finance + Operations (on-premises) deployment

## Download the Infrastructure Scripts

1. Sign in to [LCS](https://lcs.dynamics.com/v2).
2. On the dashboard, select the **Shared asset library** tile.
3. Select **Model** as the asset type.
4. Find assets that are labeled **Microsoft Dynamics 365 Finance + Operations (on-premises), Deployment scripts version X.X.X**.
5. Download the latest version available.
6. After the zip file is downloaded, select and hold (or right-click) it, and then select **Properties**. In the **Properties** dialog box, select the **Unblock** checkbox.
7. Create a file share, and copy the zip file into it.
8. Unzip the files into a folder that is named **Infrastructure**.

> [!IMPORTANT]
> It's important that you put the **Infrastructure** folder in a file share (for example, \\\\LBDEN01FS01\\Install). This way, the scripts can be run on any machine without requiring that the folder be copied to each machine. 
> Make sure that all edits are made to the ConfigTemplate.xml file in this folder.

## Update the Infrastructure Scripts

1. Rename the original **Infrastructure** folder that you created during as part of the download process. Rename the folder to **InfrastructureOld**.

1. Download the latest setup scripts according to the download section above. Unzip the files into a file share that can be accessed by all machines in the cluster. Name the folder **Infrastructure**.

    > [!NOTE]
    > As of version 2.14.0, each version of the scripts will have its own entry in the Shared asset library.

1. Copy your old configuration template to the new **Infrastructure** folder. You can overwrite the existing configuration template.

1. Update your configuration template to match the new schema.

```powershell
.\Update-ConfigTemplate.ps1 -ConfigurationFilePath .\ConfigTemplate.xml
```

According to the output from the script execution you may have to do additional actions:

- If the script returns an error message similar to: The file ConfigTemplate.xml does not have a schema version available. In this case, your existing configuration file did not have a tracked schema version and has to be migrated manually. You can do this by manually filling out the new version of the template with the details from your existing template.

- If the script returns an error message similar to: There is no defined upgrade path from 1.4 to 1.5. In this case your existing configuration file is too old and did not have an automated schema migration implemented and has to be migrated manually. You can do this by manually filling out the new version of the template with the details from your existing template.

- If the script succeeds it will output a text similar to: The schema has been successfully upgraded from version 1.8 to version 1.9. After this text, there will be some additional output that indicates what has been done. If you need to fill in additional information this will be mentioned in the output. For example, when update from schema 1.8 to 1.9 you will see this in the output: A new gmsa account has been added, please fill out the details for it. In this case, a new gmsa account has been added and you need to fill out the details for it as well as create it.

> [!NOTE]
> Only newer versions of the scripts (version 2.14.0 and later) that introduce changes to the schema of the configuration file will include logic that migrates the configuration file to the new schema.