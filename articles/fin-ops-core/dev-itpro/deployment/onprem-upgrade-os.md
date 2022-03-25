---
# required metadata

title: Upgrade Windows Server on your Microsoft Dynamics 365 Finance + Operations (on-premises) environments
description: This topic explains how to upgrade the Windows Server version that your environment is using.
author: faix
ms.date: 12/14/2021
ms.topic: article
audience: IT Pro
ms.reviewer: sericks
ms.search.region: Global
ms.author: osfaixat
ms.search.validFrom: 2021-11-29

---

# Upgrade Windows Server on your Microsoft Dynamics 365 Finance + Operations (on-premises) environments

## Prerequisites for upgrading the SQL Server version

### Upgrade from Windows Server 2016 to Windows Server 2019

- The environment must be on application version 10.0.17 or later.
- The local agent must be on version 3.0.0 or later.

## Upgrade Active Directory Federation Services

### Upgrade a single AD FS instance

1. Schedule ample downtime to be able to carry out this operation as users will not be able to login into Microsoft Dynamics 365 Finance + Operations (on-premises).

1. On your AD FS server, run the following command
    ```powershell
    .\Get-DeploymentSettings.ps1 -ConfigurationFilePath .\ConfigTemplate.xml
    ```

1. Take note of the following values **Active Directory->Client ID for AOS application group** and **Active Directory->Client ID for Financial Reporting application group**

1. Follow [Upgrade Windows Server 2016 to Windows Server 2019](https://docs.microsoft.com/windows-server/upgrade/upgrade-2016-to-2019) to go through an in-place upgrade.

> [!NOTE]
> You will get a warning stating that you will need to reconfigure your AD FS role after the upgrade is complete. This is not a problem as we have collected the necessary information to recreate the application group. However, if you have additional applications make sure you back up the client Ids so you can recreate them again later with the same Ids.

1. Once the machine has been upgraded, open Server Manager and go through the configuration of AD FS.

1. Configure AD FS according to [Configure AD FS](./setup-deploy-on-premises-pu41.md#configureadfs). However, do not run the **Publish-ADFSApplicationGroup.ps1** script.

1. Run the following command
    ```powershell
    # Host URL is your DNS record\host name for accessing the AOS
    .\Publish-ADFSApplicationGroup.ps1 -HostUrl 'https://ax.d365ffo.onprem.contoso.com' -ClientId <"Value of Active Directory->Client ID for AOS application group"> -FinancialReportingClientId <"Client ID for Financial Reporting application group">
    ```

### Upgrade an AD FS farm

If using a Windows Internal Database (WID) follow [Upgrading to AD FS in Windows Server 2016 using a WID database](https://docs.microsoft.com/windows-server/identity/ad-fs/deployment/upgrading-to-ad-fs-in-windows-server).

If using a SQL Server database follow [Upgrading to AD FS in Windows Server 2016 with SQL Server](https://docs.microsoft.com/windows-server/identity/ad-fs/deployment/upgrading-to-ad-fs-in-windows-server-sql)

### Create a new AD FS farm/instance and replace your old AD FS farm/instance

1. Create a new AD FS federation farm/instance. For information about how to deploy AD FS, see [Windows Server AD FS Deployment Guide](https://docs.microsoft.com/windows-server/identity/ad-fs/deployment/windows-server-2012-r2-ad-fs-deployment-guide).

1. Configure AD FS according to [Configure AD FS](./setup-deploy-on-premises-pu41.md#configureadfs). However, do not run the **Publish-ADFSApplicationGroup.ps1** script.

1. On your existing AD FS farm, run the following command
    ```powershell
    .\Get-DeploymentSettings.ps1 -ConfigurationFilePath .\ConfigTemplate.xml
    ```

1. Take note of the following values **Active Directory->Client ID for AOS application group** and **Active Directory->Client ID for Financial Reporting application group**

1. On your new AD FS farm/instance, run the following command
    ```powershell
    # Host URL is your DNS record\host name for accessing the AOS
    .\Publish-ADFSApplicationGroup.ps1 -HostUrl 'https://ax.d365ffo.onprem.contoso.com' -ClientId <"Value of Active Directory->Client ID for AOS application group"> -FinancialReportingClientId <"Client ID for Financial Reporting application group">
    ```

1. Your new farm/instance is ready to be used by Microsoft Dynamics 365 Finance + Operations (on-premises).

1. If your new farms/instance endpoint is different from that of the old farm/instance, then ensure that you update the endpoint in LCS by using the Update Settings option and setting the **ADFS OpenID metadata endpoint** configuration to the new value.

## Upgrade a node in your Service Fabric cluster

In Service Fabric standalone clusters, upgrading the operating system of a node (VM or physical machine) is a machine specific operation. There are two possibilities to doing an in-place upgrade for a node. The first is where the OS upgrade does not wipe out data and OS configuration, and the second one if where the upgrade operation wipes out data and OS configuration. It is also possible to create new nodes and then add those new nodes into the cluster.

Regardless of the method chosen to upgrade the nodes consider upgrading all of the nodes within a node type first and then proceeding with another node type.

### In-place upgrade without wiping out OS data

This process has the advantage that it will keep your cluster up and running without impacting availability of the service as long as not all nodes are upgraded at the same time.

> [!IMPORTANT]
> If your cluster only has 3 seed nodes (OrchestratorNodeType), then only upgrade one of the nodes at a time. Otherwise the cluster will not be able to keep the system services running and the cluster won't be available.
> If your cluster only has 1 BI/MR node, then you should schedule the node upgrade during a downtime window, as the related services will not be available throughout the upgrade process. 

Azure vs standalone

In Azure for SFRP deployed / managed cluster, each node type is backed by a Scaleset and upgrading the US may not necessarily be supported if there is no upgrade path between the current Image and the image that you are trying to move to for the new OS version. Anything going wrong while the scaleset instances are being upgraded can get the nodetype / scaleset in a state that may be very hard / impossible to recover. Creating a new Saleset/Node Type allows more flexibility as any failures in provisioning new scaleset / node type does not impact availability and easy to recover from.

In standalone environments, OS upgrade of a node (VM/physical machine) is a machine specific operation. Limitations associated with Scaleset don’t necessarily apply. Following will work.

Assumes that OS upgrade preserves data i.e. OS upgrade does not wipe out data and OS configuration

•	Disable Node -Intent Restart
•	Upgrade the OS
•	Enable Node
•	Wait for Node to be healthy and continues to be healthy for some duration
•	Repeat for next Node

If OS upgrade operation wipes out data/OS configuration
•	Disable Node -Intent RemoveNode
•	Remove the Node from the cluster (Remove-ServiceFabricNode)
•	Update machine
•	Add VM to the cluster (Add-ServiceFabricNode)
•	Wait for Node to be healthy and continues to be healthy for some duration
•	Repeat for next Node


### In-place upgrade

1. Go to Service Fabric explorer and Deactivate(Restart) the node you intend to upgrade.

1. Follow [Upgrade Windows Server 2016 to Windows Server 2019](https://docs.microsoft.com/windows-server/upgrade/upgrade-2016-to-2019) to go through an in-place upgrade.

1. 

1. run through windows installation