---
# required metadata
title: Add or remove a node from an existing environment
description: Learn how to add or remove a node in your existing Microsoft Dynamics 365 Finance + Operations (on-premises) environment.
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

This article explains how to add or remove a node in your existing Microsoft Dynamics 365 Finance + Operations (on-premises) environment. It describes the generic procedures that can be used for any node type. Specific node types might require further steps. In this case, refer to the documentation for the node type or the service.

## Add a node

To add one or more nodes to your existing environment, follow these steps.

1. Ensure that you download the latest infrastructure scripts. Learn more in [Update the infrastructure scripts](./obtain-infrascripts-onprem.md#update-the-infrastructure-scripts). To complete this procedure, you must have version 2.23.1 or later of the scripts.
1. Update the ConfigTemplate.xml file with the new node information.
1. Run the following command to ensure that your cluster has all the node types defined in the ConfigTemplate.xml file.

    ```powershell
    .\Update-SFClusterConfig.ps1 -ConfigurationFilePath .\ConfigTemplate.xml -AddNodeTypes
    ```

1. If the previous command generates a configuration file and doesn't state that all node types already exist in the cluster, you must update the Azure Service Fabric cluster with the new configuration file. Learn more in [Update the Service Fabric cluster configuration](./onprem-update-sfcluster.md#update-the-service-fabric-cluster-configuration).
1. Run the following commands to generate the prerequisites for the new node.

    ```powershell
    .\Export-Certificates.ps1 -ConfigurationFilePath .\ConfigTemplate.xml
    .\Export-Scripts.ps1 -ConfigurationFilePath .\ConfigTemplate.xml -D365FOVersion <version of fno currently installed>
    ```

1. Run the following command to update the group managed service account (gMSA) account so that the new node can use it.

    ```powershell
    .\Create-GMSAAccounts.ps1 -ConfigurationFilePath .\ConfigTemplate.xml -Update
    ```

1. Run the following command to ensure that the Service Fabric diagnostic store can be accessed by the new node.

    ```powershell
    .\Configure-FileShares.ps1 -ConfigurationFilePath .\ConfigTemplate.xml -FileShareReference "sfDiagnostics"
    ```

1. Run the following commands to ensure that all prerequisites are installed for the new node.

    ```powershell
    .\Configure-PreReqs-AllVMs.ps1 -ConfigurationFilePath .\ConfigTemplate.xml -MSIFilePath <file-path> -ForcePushLBDScripts
    .\Complete-PreReqs-AllVMs.ps1 -ConfigurationFilePath .\ConfigTemplate.xml
    ```

1. Run the following command to validate that the new node meets all prerequisites.

    ```powershell
    .\Test-D365FOConfiguration-AllVMs.ps1 -ConfigurationFilePath .\ConfigTemplate.xml
    ```

1. Run the following command to add the new node to the Service Fabric cluster. This command should be run from an existing node in the cluster.

    > [!NOTE]
    > Run this command once for each new node that you want to add to the cluster.

    ```powershell
    .\Add-ServiceFabricNode.ps1 -ConfigurationFilePath .\ConfigTemplate.xml -VMName <vm name>
    ```

1. Wait until all the new nodes are added to the cluster and any services are deployed to them.
1. Run the following command to generate an updated cluster configuration file.

    ```powershell
    .\Update-SFClusterConfig.ps1 -ConfigurationFilePath .\ConfigTemplate.xml -UpdateServiceFabricSettings
    ```

1. Update the Service Fabric cluster with the new configuration file. Learn more in [Update the Service Fabric cluster configuration](./onprem-update-sfcluster.md#update-the-service-fabric-cluster-configuration).

## Remove a node

To remove one or more nodes from your existing environment, follow these steps.

1. Run the following command to generate an updated configuration file that instructs Service Fabric to remove the nodes. This command should be run from an existing node in the cluster.

    > [!NOTE]
    > This command is case-sensitive.

    ```powershell
    .\Update-SFClusterConfig.ps1 -ConfigurationFilePath .\ConfigTemplate.xml -RemoveNode -NodeNames @("node1", "node2")
    ```

1. Update the Service Fabric cluster with the new configuration file. Learn more in [Update the Service Fabric cluster configuration](./onprem-update-sfcluster.md#update-the-service-fabric-cluster-configuration).
1. After the Service Fabric cluster configuration is updated, you must run the following command to clean up the nodes from the cluster configuration.

    ```powershell
    .\Update-SFClusterConfig.ps1 -ConfigurationFilePath .\ConfigTemplate.xml -CleanupRemoveNode
    ```

1. Update the Service Fabric cluster with the new configuration file. Learn more in [Update the Service Fabric cluster configuration](./onprem-update-sfcluster.md#update-the-service-fabric-cluster-configuration).

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
