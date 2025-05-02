---
# required metadata
title: Add an SSIS node to an existing environment
description: Learn how to add a Microsoft SQL Server Integration Services (SSIS) node in an on-premises environment, including installation steps.
author: ttreen
ms.author: ttreen
ms.topic: article
ms.date: 02/04/2025
ms.custom:
ms.reviewer: 
audience: IT Pro
ms.search.region: Global
ms.search.validFrom: 2023-08-17
ms.search.form:
ms.dyn365.ops.version: Platform update 58
ms.service: dynamics-365-op
---

# Add an SSIS node to an existing environment

[!include[banner](../includes/banner.md)]

This article explains how to add a Microsoft SQL Server Integration Services (SSIS) node in an on-premises environment. SSIS nodes were introduced in version 10.0.32 (Platform update 56) and are used by the Data management framework.

## Installation steps

1. Confirm that your environment is on version 10.0.32 (Platform update 56) or later.
1. Download and extract the latest setup scripts from Microsoft Dynamics Lifecycle Services. For more information, see [Download the infrastructure scripts](./obtain-infrascripts-onprem.md#download-the-infrastructure-scripts).

    > [!IMPORTANT]
    > The scripts must be run from a computer that's in the same domain as the on-premises infrastructure.

1. Update the infrastructure scripts. For more information, see [Update the infrastructure scripts](./obtain-infrascripts-onprem.md#update-the-infrastructure-scripts).
1. In the *ConfigTemplate.xml* file, in the `SSISNodeType` section, modify the SSIS nodes. Confirm that the `disabled` parameter is set to *false*.

    ```XML
    <NodeType name="SSISNodeType" primary="false" namePrefix="SSIS" purpose="SSIS" disabled="false">
        <!-- Do not place hasSSIS on this node type. -->
        <VMList>
            <VM name="ssis1" ipAddress="10.179.108.22" faultDomain="fd:/fd0" updateDomain="ud0" />
            <VM name="ssis2" ipAddress="10.179.108.23" faultDomain="fd:/fd1" updateDomain="ud1" />
        </VMList>
    </NodeType>
    ```

1. Create the Data import/export framework (DIXF) group managed service account (gMSA). For more information, see [Step 8. Create gMSAs](./setup-deploy-on-premises-latest.md#setupgMSA). Option 1 creates just the new DIXF gMSA.

1. Run the following script to create the file share.

    ```powershell
    .\New-FileShares.ps1 -ConfigurationFilePath .\ConfigTemplate.xml -FileShareReference "dixf"
    ```

1. Run the following script to apply the required configuration and permissions to each file share.

    ```powershell
    .\Configure-FileShares.ps1 -ConfigurationFilePath .\ConfigTemplate.xml -FileShareReference "dixf"
    .\Configure-FileShares.ps1 -ConfigurationFilePath .\ConfigTemplate.xml -FileShareReference "aos"
    ```

1. Install SSIS on the required nodes. For more information, see [Step 12. Set up SSIS](./setup-deploy-on-premises-latest.md#setupssis).

1. Follow the instructions in [Add a node to an existing environment](./onprem-add-remove-node.md#add-a-node) to add the new node to the environment.

1. If your environment was originally deployed before version 10.0.32, you must add the predeployment script to enable the DIXF service. If you don't have the base predeployment script, set up the script, and enable the [TSG_EnableDixfService.ps1](./onprem-tsg-implementations.md#enableDixf) script. In the main predeployment script, uncomment the line for the DIXF script, and confirm that the DIXF share that you created in the previous step is set. For more information, see [Scripts for resolving issues in on-premises environments](../deployment/onprem-tsg-implementations.md).

1. Sign in to Lifecycle Services, and select the project and environment. Select **Maintain** \> **Update settings**, and then select **Prepare**. After the configuration is downloaded, select **Update** in Lifecycle Services to complete the process.
