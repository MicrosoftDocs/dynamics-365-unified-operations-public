---
# required metadata

title: Upgrade Windows Server on your Microsoft Dynamics 365 Finance + Operations (on-premises) environments
description: This topic explains how to upgrade the Windows Server version that your environment is using.
author: faix
ms.date: 03/29/2022
ms.topic: article
audience: IT Pro
ms.reviewer: sericks
ms.search.region: Global
ms.author: osfaixat
ms.search.validFrom: 2021-11-29

---

# Upgrade Windows Server on your Microsoft Dynamics 365 Finance + Operations (on-premises) environments

This article explains how to upgrade Windows Server on your Microsoft Dynamics 365 Finance + Operations (on-premises) environments.

## Prerequisites for upgrading the SQL Server version

### Upgrade from Windows Server 2016 to Windows Server 2019

- The Dynamics 365 Finance + Operations (on-premises) environment must be on application version 10.0.17 or later.
- The local agent must be on version 3.0.0 or later.

## Upgrade Active Directory Federation Services (AD FS)

### Upgrade a single AD FS instance

1. Schedule ample downtime to be able to carry out this operation as users will not be able to log into Microsoft Dynamics 365 Finance + Operations (on-premises).

1. On your AD FS server, run the following command

    ```powershell
    .\Get-DeploymentSettings.ps1 -ConfigurationFilePath .\ConfigTemplate.xml
    ```
    
1. Take note of the following values **Active Directory->Client ID for AOS application group** and **Active Directory->Client ID for Financial Reporting application group**.

1. Follow [Upgrade Windows Server 2016 to Windows Server 2019](/windows-server/upgrade/upgrade-2016-to-2019) to go through an in-place upgrade.

    > [!NOTE]
    > You will get a warning stating that you will need to reconfigure your AD FS role after the upgrade is complete. This is not a problem as we have collected the necessary information to recreate the application group. However, if you have additional applications, make sure you back up the client IDs so you can recreate them again later with the same IDs.

1. Once the machine has been upgraded, open Server Manager and go through the configuration of AD FS.

1. Configure AD FS according to [Configure AD FS](./setup-deploy-on-premises-pu41.md#configureadfs). However, do not run the **Publish-ADFSApplicationGroup.ps1** script.

1. Run the following command

    ```powershell
    # Host URL is your DNS record\host name for accessing the AOS
    .\Publish-ADFSApplicationGroup.ps1 -HostUrl 'https://ax.d365ffo.onprem.contoso.com' -ClientId <"Value of Active Directory->Client ID for AOS application group"> -FinancialReportingClientId <"Client ID for Financial Reporting application group">
    ```

### Upgrade an AD FS farm

If using a Windows Internal Database (WID), follow the instructions in [Upgrading to AD FS in Windows Server 2016 using a WID database](/windows-server/identity/ad-fs/deployment/upgrading-to-ad-fs-in-windows-server).

If using a SQL Server database, follow the instructions in [Upgrading to AD FS in Windows Server 2016 with SQL Server](/windows-server/identity/ad-fs/deployment/upgrading-to-ad-fs-in-windows-server-sql).

### Create a new AD FS farm/instance and replace your old AD FS farm/instance

1. Create a new AD FS federation farm/instance. For information about how to deploy AD FS, see [Windows Server AD FS Deployment Guide](/windows-server/identity/ad-fs/deployment/windows-server-2012-r2-ad-fs-deployment-guide).

1. Configure AD FS according to [Configure AD FS](./setup-deploy-on-premises-pu41.md#configureadfs). However, do not run the **Publish-ADFSApplicationGroup.ps1** script.

1. On your existing AD FS farm, run the following command.

    ```powershell
    .\Get-DeploymentSettings.ps1 -ConfigurationFilePath .\ConfigTemplate.xml
    ```

1. Take note of the following values **Active Directory->Client ID for AOS application group** and **Active Directory->Client ID for Financial Reporting application group**.

1. On your new AD FS farm/instance, run the following command.

    ```powershell
    # Host URL is your DNS record\host name for accessing the AOS
    .\Publish-ADFSApplicationGroup.ps1 -HostUrl 'https://ax.d365ffo.onprem.contoso.com' -ClientId <"Value of Active Directory->Client ID for AOS application group"> -FinancialReportingClientId <"Client ID for Financial Reporting application group">
    ```

1. Your new farm/instance is ready to be used by Microsoft Dynamics 365 Finance + Operations (on-premises).

1. If your new farms/instance endpoint is different from that of the old farm/instance, then ensure that you update the endpoint in LCS by using the **Update Settings** option and setting the **ADFS OpenID metadata endpoint** configuration to the new value.

## Upgrade a node in your Service Fabric cluster

In Service Fabric standalone clusters, upgrading the operating system of a node (VM or physical machine) is a machine-specific operation. There are two possibilities to doing an in-place upgrade for a node. The first is where the operating system upgrade preserves data and configuration, and the second one is where the upgrade operation does not preserve data and the operating system configuration. It is also possible to create new nodes and then add those new nodes into the cluster.

All of the options listed below will keep your cluster up and running without impacting availability of the service as long as not all nodes are upgraded at the same time.

Regardless of the method chosen to upgrade the nodes, consider upgrading all of the nodes within a node type first, and then proceeding with another node type.

> [!IMPORTANT]
> If your cluster only has three seed nodes (OrchestratorNodeType), then only upgrade one of the nodes at a time. Otherwise the cluster will not be able to keep the system services running and the cluster won't be available.
> If your cluster only has one BI/MR node, then you should schedule the node upgrade during a downtime window, as the related services will not be available throughout the upgrade process. 

### In-place upgrade preserving operating system data

This is the simplest option as you will be deactivating the node, upgrading the operating system and preserving all data. After the upgrade a node activation is required to bring the node back online. 

1. Navigate to Service Fabric explorer and deactivate (restart) the node you intend to upgrade.

1. Follow the instructions in [Upgrade Windows Server 2016 to Windows Server 2019](/windows-server/upgrade/upgrade-2016-to-2019) to go through an in-place upgrade.

1. Once the node is back up, use the Test-D365FOConfiguration.ps1 script to ensure that the upgrade did not restore prerequisites to their default values. If there are issues brought up by the test script, run the **Configure-Prereqs.ps1** and **Complete-Prereqs.ps1** scripts to resolve the issues. 

1. Navigate to Service Fabric explorer and activate the node.

1. Wait for the node to be healthy again. Once it is healthy, repeat the same steps with the next nodes.

### In-place upgrade without preserving operating system data

During the operating system upgrade, you will be removing all data, so the node will have a fresh operating system installation. However, this means that you will need to go through all of the configuration steps for each node before adding the node back to the cluster.

1. Navigate to Service Fabric explorer and deactivate (remove data) for the node you intend to upgrade.

1. Follow the documentation to [remove a node](./onprem-remove-reinstall-aos-node.md#remove-a-node) from the cluster.

1. Follow the instructions in [Upgrade Windows Server 2016 to Windows Server 2019](/windows-server/upgrade/upgrade-2016-to-2019) to go through an in-place upgrade.

1. Follow the documentation to [add a node](./onprem-remove-reinstall-aos-node.md#add-a-node) back to the cluster.

1. Once the node is back up, navigate to Service Fabric explorer and activate the node.

1. Wait for the node to be healthy again. Once it is healthy, repeat the same steps with the next nodes.

### Adding new nodes to the cluster

This option is pretty similar to the one above, however you are spinning up your new nodes before you remove nodes from the cluster. This will help keep the performance of the service in case you can't take nodes down.

1. Provision a new virtual machine.

1. Follow the documentation to [add a node](./onprem-remove-reinstall-aos-node.md#add-a-node).

1. Once the node has been added and the services on the node are healthy, proceed to provision, configure, and add additional nodes.

1. After you have added all nodes, start removing the nodes running the older operating system by using [remove a node](./onprem-remove-reinstall-aos-node.md#remove-a-node).
