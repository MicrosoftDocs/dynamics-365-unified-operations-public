---
# required metadata
title: Update Service Fabric clusters for Microsoft Dynamics 365 Finance + Operations (on-premises) environments
description: Learn how to update your Microsoft Azure Service Fabric cluster for Dynamics 365 Finance + Operations (on-premises) environments.
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

# Update Service Fabric clusters for Microsoft Dynamics 365 Finance + Operations (on-premises) environments

[!INCLUDE [banner](../includes/banner.md)]

This article provides guidance about how to update your Microsoft Azure Service Fabric cluster for Dynamics 365 Finance + Operations (on-premises) environments. It describes the best way to update the code version and configuration of the Service Fabric cluster.

## Update the Service Fabric cluster runtime

Dynamics 365 Finance + Operations (on-premises) environments require a specific version of the Service Fabric runtime. You can find the minimum Service Fabric runtime version that your version of Finance + Operations requires in [Minimum Azure Service Fabric runtime](.\onprem-compatibility.md#minimum-azure-service-fabric-runtime).

To update the Service Fabric runtime for your cluster, follow these steps.

1. From a node that belongs to the Service Fabric cluster, run the following PowerShell commands to get a list of available Service Fabric runtime versions.

    
    ```powershell
    # Connect to the Service Fabric Cluster
    Connect-ServiceFabricCluster
    
    # Get the latest Service Fabric runtime version downloaded to your cluster
    Get-ServiceFabricRegisteredClusterCodeVersion
    ```

    > [!NOTE]
    > If your cluster has heavily restricted outbound internet access, you might not have the runtime predownloaded. In this case, follow the steps in [Upgrade clusters that have no connectivity to download the latest code and configuration](/azure/service-fabric/service-fabric-cluster-upgrade-windows-server#upgrade-clusters-that-have-no-connectivity-to-download-the-latest-code-and-configuration) before you continue.

1. Run the following command to update the cluster to a specific version.

    ```powershell
    # Update the Service Fabric runtime version
    Start-ServiceFabricClusterUpgrade -Code -CodePackageVersion <version> -Monitored -FailureAction Rollback
    ```

1. Optional: If your cluster has a single node for any node type, run the following command to skip the PreUpgradeSafetyCheck check, which can cause a time-out.

    ```powershell
    # If you are using a single Microsoft SQL Server Reporting Services node, use UpgradeReplicaSetCheckTimeout to skip PreUpgradeSafetyCheck check, otherwise it will timeout
    Update-ServiceFabricClusterUpgrade -UpgradeReplicaSetCheckTimeoutSec 30
    ```

1. Run the following command to monitor the status of the upgrade.

    ```powershell
    Get-ServiceFabricClusterUpgrade
    ```

## Update the Service Fabric cluster configuration

When you have a new Service Fabric cluster configuration file that you must apply to your cluster, run the following PowerShell commands to update your cluster's configuration.

```powershell
# Connect to the Service Fabric Cluster
Connect-ServiceFabricCluster

# Start the cluster configuration upgrade with the new configuration file
Start-ServiceFabricClusterConfigurationUpgrade -ClusterConfigPath ClusterConfig.json

# If you have a node type with a single node, use UpgradeReplicaSetCheckTimeout to skip PreUpgradeSafetyCheck check, otherwise it will time out
Update-ServiceFabricClusterUpgrade -UpgradeReplicaSetCheckTimeoutSec 30

# To monitor the status of the upgrade, run the following and note UpgradeState and UpgradeReplicaSetCheckTimeout
Get-ServiceFabricClusterUpgrade

# While monitoring the status of the upgrade, if UpgradeReplicaSetCheckTimeout was reset to the default (example 49710.06:28:15), run the following command again
Update-ServiceFabricClusterUpgrade -UpgradeReplicaSetCheckTimeoutSec 30

# When UpgradeState shows RollingForwardCompleted, the upgrade is finished
```

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
