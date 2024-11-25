---
title: Configure your environment with a dedicated Data Management Framework service
description: Learn how to configure environments to use a separate, dedicated service for the Data Management Framework for new and existing environments.
author: faix
ms.author: osfaixat
ms.topic: how-to
ms.date: 01/21/2024
ms.custom: 
  - bap-template
ms.reviewer: johnmichalak
audience: IT Pro
ms.search.region: Global
ms.search.validFrom: 2021-03-21
ms.search.form:
ms.dyn365.ops.version: 10.0.32
---

# Configure your environment with a dedicated Data Management Framework service

[!include[banner](../includes/banner.md)]

You can have dedicated nodes that contain Microsoft SQL Server Integration Services (SSIS), or you can install SSIS on other node types. If you want dedicated SSIS nodes, specify which machines host the node type by entering the details for the nodes in your ConfigTemplate.xml file.

If your use of the Data Management Framework (DMF) is low, you might not want to have dedicated nodes. Instead, you can specify which nodes SSIS is installed on. In the **ServiceFabricCluster** section of your ConfigTemplate.xml file, update the **hasSSIS** attribute to **true** for each virtual machine (VM). In this case, you should set the **disabled** attribute to **true** for the **SSISNodeType** node type in the ConfigTemplate.xml file.

> [!NOTE]
> If you disable the **SSISNodeType** node type but don't set the **hasSSIS** attribute on any node, the scripts and installation logic provision the DMF service to all nodes of the **BatchOnlyAOSNodeType** type. If that node type doesn't exist, the DMF service is provisioned to all nodes of the **AOSNodeType** type.

## New environments (10.0.32 and later)

If you deploy an environment as of Application Version 10.0.32, it contains a dedicated service for DMF.

## Existing environments (10.0.31 and earlier)

If you deployed your Dynamics 365 for Finance + Operations (on-premises) environment before Application Version 10.0.32, you can manually configure it to use a dedicated service for DMF.

> [!IMPORTANT]
> If you use an environment that was deployed before Application Version 10.0.32, you must update the environment to Application Version 10.0.32 or later before you can configure it to use a dedicated service for DMF.

### Use new nodes

For information about how to add a new node to your cluster, see [Add an SSIS node to an existing environment](./ssis-node.md).

### Use existing nodes

1. Ensure that you download the latest infrastructure scripts. For information, see [Update the infrastructure scripts](./obtain-infrascripts-onprem.md#update-the-infrastructure-scripts).
1. If you don't already have a group managed service account (gMSA) for the DMF service, create it by updating your ConfigTemplate.xml file, and run the following command.

    ```powershell
    .\Create-GMSAAccounts.ps1 -ConfigurationFilePath .\ConfigTemplate.xml
    ```

1. Run the following script to create the file share.

    ```powershell
    .\New-FileShares.ps1 -ConfigurationFilePath .\ConfigTemplate.xml -FileShareReference "dixf"
    ```

1. Run the following script to apply the required configuration and permissions to each file share.

    ```powershell
    .\Configure-FileShares.ps1 -ConfigurationFilePath .\ConfigTemplate.xml -FileShareReference "dixf"
    .\Configure-FileShares.ps1 -ConfigurationFilePath .\ConfigTemplate.xml -FileShareReference "aos"
    ```

1. If you want the DMF service to run on specific nodes, you can update your ConfigTemplate.xml file. Set the **hasSSIS** property to **true** for the nodes that you want.

    > [!NOTE]
    > As of infrastructure scripts 2.20.0 and local agent 3.3.0, node tag management is automatically performed, and no action is required if a node is restarted. If you use an older version of the infrastructure scripts or local agent, you must run the following command from a node that belongs to the Azure Service Fabric cluster.
    >
    > ```powershell
    > .\Set-SFDynamicNodeTags.ps1 -ConfigurationFilePath .\ConfigTemplate.xml
    > ```

1. Export the certificates.

    ```PowerShell
    # Exports certificates into a directory VMs\<VMName>. All of the certs are written to the infrastructure\Certs folder.
    .\Export-Certificates.ps1 -ConfigurationFilePath .\ConfigTemplate.xml
    ```

1. Export the scripts.

    ```PowerShell
    .\Export-Scripts.ps1 -ConfigurationFilePath .\ConfigTemplate.xml -D365FOVersion <application version: i.e. 10.0.40>
    ```

1. Complete the prerequisites.

    ```powershell
    .\Complete-PreReqs-AllVMs.ps1 -ConfigurationFilePath .\ConfigTemplate.xml
    ```

1. Set up the following predeployment script: [TSG_EnableDixfService.ps1](./onprem-tsg-implementations.md#enableDixf).
1. In Microsoft Dynamics Lifecycle Services, use the **Apply updates** option to apply an update to the environment. The servicing flow automatically enables and deploys the new DMF service.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
