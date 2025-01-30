---
# required metadata
title: Updating Service Fabric clusters for Microsoft Dynamics 365 Finance and Operations (on-premises) environments
description: Learn how to add or remove a node to your existing Microsoft Dynamics 365 Finance + Operations (on-premises) environment.
author: faix
ms.author: osfaixat
ms.topic: article
ms.date: 01/30/2025
ms.custom:
ms.reviewer: 
audience: IT Pro
ms.search.region: Global
ms.search.validFrom: 2025-01-30
ms.search.form:
ms.dyn365.ops.version: Platform update 66
ms.service: dynamics-365-op
---

# Updating Service Fabric clusters for Microsoft Dynamics 365 Finance and Operations (on-premises) environments

[!INCLUDE [banner](../includes/banner.md)]

This article provides guidance on how to update your Service Fabric cluster for Microsoft Dynamics 365 Finance and Operations (on-premises) environments. It covers the best way to update the Service Fabric cluster code version and configuration.


## Update the Service Fabric cluster runtime

Microsoft Dynamics 365 Finance and Operations (on-premises) environments require a specific version of the Service Fabric runtime. You can check the minimum Service Fabric runtime that your version of Finance and Operations requires in [Minimum Azure Service Fabric Runtime](.\onprem-compatibility.md#minimum-azure-service-fabric-runtime).

To update the Service Fabric runtime for your cluster, follow these steps:

1. From a node belonging to the Service Fabric cluster, run the following PowerShell commands:
    
    ```powershell
    # Connect to the Service Fabric Cluster
    Connect-ServiceFabricCluster

    # Get the latest Service Fabric runtime version downloaded to your cluster
    Get-ServiceFabricRegisteredClusterCodeVersion
    ```

    > [!NOTE]
    > If your cluster has heavily restricted outbound internet access, you might not have the runtime pre-downloaded. In this case, please follow the steps in [Upgrade clusters that have no connectivity to download the latest code and configuration](/azure/service-fabric/service-fabric-cluster-upgrade-windows-server#upgrade-clusters-that-have-no-connectivity-to-download-the-latest-code-and-configuration) before proceeding.

1. The command above will return a list of available Service Fabric runtime versions. To update the cluster to a specific version, run the following command:

    ```powershell
    # Update the Service Fabric runtime version
    Start-ServiceFabricClusterUpgrade -Code -CodePackageVersion <version> -Monitored -FailureAction Rollback
    ```

1. (optional) If your cluster has a single node for any node type, you can use the following command to skip the PreUpgradeSafetyCheck check, which can cause a timeout:

    ```powershell
    # If you are using a single Microsoft SQL Server Reporting Services node, use UpgradeReplicaSetCheckTimeout to skip PreUpgradeSafetyCheck check, otherwise it will timeout
    Update-ServiceFabricClusterUpgrade -UpgradeReplicaSetCheckTimeoutSec 30
    ```

1. To monitor the status of the upgrade, run the following command:

    ```powershell
    Get-ServiceFabricClusterUpgrade
    ```

## Update the Service Fabric cluster configuration

Once you have a new Service Fabric cluster configuration file that you need to apply to your cluster, run the following PowerShell commands to update your clusters configuration.

```powershell
# Connect to the Service Fabric Cluster
Connect-ServiceFabricCluster

# Start the cluster configuration upgrade with the new configuration file
Start-ServiceFabricClusterConfigurationUpgrade -ClusterConfigPath ClusterConfig.json

# If you have a node type with a single node, use UpgradeReplicaSetCheckTimeout to skip PreUpgradeSafetyCheck check, otherwise it will timeout
Update-ServiceFabricClusterUpgrade -UpgradeReplicaSetCheckTimeoutSec 30

# To monitor the status of the upgrade, run the following and note UpgradeState and UpgradeReplicaSetCheckTimeout
Get-ServiceFabricClusterUpgrade

# While monitoring the status of the upgrade, if UpgradeReplicaSetCheckTimeout was reset to the default (example 49710.06:28:15), run the following command again
Update-ServiceFabricClusterUpgrade -UpgradeReplicaSetCheckTimeoutSec 30

# When UpgradeState shows RollingForwardCompleted, the upgrade is finished
```

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]