---
# required metadata

title: Obtain the infrastructure scripts for your Finance + Operations (on-premises) deployment
description: This article explains how to download or update the infrastructure scripts from one version to another.
author: faix
ms.date: 1/11/2023
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
search.app:
  - financeandoperationsonprem-docs
---

# Obtain the infrastructure scripts for your Finance + Operations (on-premises) deployment

This article explains how to download or update the infrastructure scripts for your deployment of Microsoft Dynamics 365 Finance + Operations (on-premises) from one version to another.

## Download the infrastructure scripts

To download the infrastructure scripts, follow these steps.

1. Sign in to [Microsoft Dynamics Lifecycle Services](https://lcs.dynamics.com/v2).
1. On the dashboard, select the **Shared asset library** tile.
1. Select **Model** as the asset type.
1. Find assets that are labeled **Microsoft Dynamics 365 Finance + Operations (on-premises), Deployment scripts version X.X.X**.
1. Download the latest version that's available.
1. After the zip file has been downloaded, select and hold (or right-click) it, and then select **Properties**. In the **Properties** dialog box, select the **Unblock** checkbox.
1. Create a file share, and copy the zip file into it.
1. Unzip the files into a folder that's named **Infrastructure**.

> [!IMPORTANT]
> It's important that you put the **Infrastructure** folder in a file share (for example, \\\\LBDEN01FS01\\Install). In this way, the scripts can be run on any machine without requiring that the folder be copied to each machine. Make sure that all edits are made to the ConfigTemplate.xml file in this folder.

## Update the infrastructure scripts

1. Rename the original **Infrastructure** folder that you created as part of the download process **InfrastructureOld**.
1. Download the latest setup scripts by following the instructions in the previous section. Unzip the files into a file share that can be accessed by all machines in the cluster. Name the folder **Infrastructure**.

    > [!NOTE]
    > As of version 2.14.0, each version of the scripts will have its own entry in the Shared asset library.

1. Copy your old configuration template into the new **Infrastructure** folder. You can overwrite the existing configuration template.
1. Update your configuration template so that it matches the new schema.

    ```powershell
    .\Update-ConfigTemplate.ps1 -ConfigurationFilePath .\ConfigTemplate.xml
    ```

Depending on the output of the script execution, you might have to perform additional actions:

- If the script returns an error message like "The file ConfigTemplate.xml does not have a schema version available," your existing configuration file didn't have a tracked schema version and must be manually migrated. To migrate the configuration file, manually fill in the new version of the template with the details from your existing template.
- If the script returns an error message like "There is no defined upgrade path from 1.4 to 1.5," your existing configuration file is too old, and no automated schema migration was implemented for it. Therefore, it must be manually migrated. To migrate the configuration file, manually fill in the new version of the template with the details from your existing template.
- If the script succeeds, it will return a message like "The schema has been successfully upgraded from version 1.8 to version 1.9." This message will be followed by other output that indicates what has been done. Output will also indicate whether you must fill in additional information. For example, if you update from schema 1.8 to 1.9, the output will include the following message: "A new gmsa account has been added, please fill out the details for it." In this case, you must fill in the details for the new group managed service account (gMSA) account that has been added, and also create it.

> [!NOTE]
> Only newer versions of the scripts (version 2.14.0 and later) that introduce changes to the schema of the configuration file will include logic that migrates the configuration file to the new schema.
