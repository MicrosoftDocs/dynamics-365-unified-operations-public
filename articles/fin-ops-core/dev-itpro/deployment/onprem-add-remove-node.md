---
# required metadata
title: Add or remove a node from an existing environment
description: Learn how to add or remove a node to your existing Microsoft Dynamics 365 Finance + Operations (on-premises) environment.
author: faix
ms.author: osfaixat
ms.topic: article
ms.date: 02/03/2025
ms.custom:
ms.reviewer: 
audience: IT Pro
ms.search.region: Global
ms.search.validFrom: 2025-01-30
ms.search.form:
ms.dyn365.ops.version: Platform update 66
ms.service: dynamics-365-op
---

# Add or remove a node from an existing environment

[!INCLUDE [banner](../includes/banner.md)]

This article goes over how to add or remove a node from your existing Microsoft Dynamics 365 Finance + Operations (on-premises) environment. This is a generic process that can be used for any node type. There may be additional steps required for specific node types, in which case you should refer to the documentation for that node type or service.

## Add a node

To add a node or nodes to your existing environment, follow these steps:

1. Ensure that you download the latest infrastructure scripts. For information, see [Update the infrastructure scripts](./obtain-infrascripts-onprem.md#update-the-infrastructure-scripts). You will need at least version 2.23.0 of the scripts to carry out these steps.

1. Update the ConfigTemplate.xml file with the new node information.

1. Ensure that your cluster has all the node types defined in the ConfigTemplate.xml file. Run the following command to ensure that all the node types are defined in the cluster:

    ```powershell
    .\Update-SFClusterConfig.ps1 -ConfigurationFilePath .\ConfigTemplate.xml -AddNodeTypes
    ```

1. If the previous command generates a configuration file and does not state that all node types already exist in the cluster you will have to update the Service Fabric cluster with the new configuration file. For more information, see [Update the Service Fabric cluster configuration](./onprem-update-sfcluster.md#update-the-service-fabric-cluster-configuration).

1. Run the following commands to generate the prerequisites for the new node:

    ```powershell
    .\Export-Certificates.ps1 -ConfigurationFilePath .\ConfigTemplate.xml
    .\Export-Scripts.ps1 -ConfigurationFilePath .\ConfigTemplate.xml -D365FOVersion <version of fno currently installed>
    ```

1. Run the following command to update the gMSA account so the new node can use it:

    ```powershell
    .\Create-GMSAAccounts.ps1 -ConfigurationFilePath .\ConfigTemplate.xml -Update
    ```

1. Run the following command to ensure that the Service Fabric diagnostic store is accessible by the new node:

    ```powershell
    .\Configure-FileShares.ps1 -ConfigurationFilePath .\ConfigTemplate.xml -FileShareReference "sfDiagnostics"
    ```

1. Run the following command to ensure that the new node has all prerequisites installed:

    ```powershell
    .\Configure-PreReqs-AllVMs.ps1 -ConfigurationFilePath .\ConfigTemplate.xml -MSIFilePath <file-path> -ForcePushLBDScripts
    .\Complete-PreReqs-AllVMs.ps1 -ConfigurationFilePath .\ConfigTemplate.xml
    ```

1. Run the following command to add the new node to the Service Fabric cluster. This command should be run from an existing node in the cluster:

    ```powershell
    .\Add-ServiceFabricNode.ps1 -ConfigurationFilePath .\ConfigTemplate.xml -VMName <vm name>
    ```
    > [!NOTE]
    > The command above should be run once for each new node that you want to add to the cluster.

1. Run the following command to generate an updated cluster configuration file:

    ```powershell
    .\Update-SFClusterConfig.ps1 -ConfigurationFilePath .\ConfigTemplate.xml -UpdateServiceFabricSettings
    ```

1. Update the Service Fabric cluster with the new configuration file. For more information, see [Update the Service Fabric cluster configuration](./onprem-update-sfcluster.md#update-the-service-fabric-cluster-configuration).

## Remove a node
To remove a node or nodes from your existing environment, follow these steps:

1. Run the following command to generate an updated configuration file that will instruct Service Fabric to remove the nodes. This command should be run from an existing node in the cluster:

    ```powershell
    .\Update-SFClusterConfig.ps1 -ConfigurationFilePath .\ConfigTemplate.xml -RemoveNode -NodeNames @("node1", "node2")
    ```
    > [!NOTE]
    > The command above is case sensitive.

1. Update the Service Fabric cluster with the new configuration file. For more information, see [Update the Service Fabric cluster configuration](./onprem-update-sfcluster.md#update-the-service-fabric-cluster-configuration).

1. Once the Service Fabric cluster configuration has been updated, you have to cleanup the nodes from the cluster configuration:
    ```powershell
    .\Update-SFClusterConfig.ps1 -ConfigurationFilePath .\ConfigTemplate.xml -CleanupRemoveNode
    ```

1. Update the Service Fabric cluster with the new configuration file. For more information, see [Update the Service Fabric cluster configuration](./onprem-update-sfcluster.md#update-the-service-fabric-cluster-configuration).

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
