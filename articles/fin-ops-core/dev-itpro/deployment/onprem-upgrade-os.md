---
title: Upgrade Windows Server in Microsoft Dynamics 365 Finance + Operations (on-premises) environments
description: Learn how to upgrade the Windows Server version that your Microsoft Dynamics 365 Finance + Operations (on-premises) environments are using.
author: faix
ms.author: osfaixat
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 02/03/2025
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2021-11-29
ms.service: dynamics-365-op
---

# Upgrade Windows Server in Microsoft Dynamics 365 Finance + Operations (on-premises) environments

This article explains how to upgrade Windows Server in your Microsoft Dynamics 365 Finance + Operations (on-premises) environments.

## Prerequisites for upgrading Windows Server

### Upgrade from Windows Server 2019 to Windows Server 2022

- The Dynamics 365 Finance + Operations (on-premises) environment must be on application version 10.0.38 or later.

### Upgrade from Windows Server 2016 to Windows Server 2019

- The Dynamics 365 Finance + Operations (on-premises) environment must be on application version 10.0.17 or later.
- The local agent must be on version 3.0.0 or later.

## Upgrade Active Directory Federation Services

### Upgrade paths

#### Upgrade a single AD FS instance

1. Schedule enough downtime to complete this operation, because users won't be able to sign in to Finance + Operations (on-premises) while it's occurring.
1. On your Active Directory Federation Services (AD FS) server, run the following command.

    ```powershell
    .\Get-DeploymentSettings.ps1 -ConfigurationFilePath .\ConfigTemplate.xml
    ```

1. Make a note of the following values: **Active Directory-\>Client ID for AOS application group** and **Active Directory-\>Client ID for Financial Reporting application group**.
1. Do an in-place upgrade by following the instructions in [Upgrade Windows Server 2016 to Windows Server 2019](/windows-server/upgrade/upgrade-2016-to-2019).

    > [!NOTE]
    > You'll receive a warning that states that you must reconfigure your AD FS role after the upgrade is completed. Because you've collected the information that's required to recreate the application group, this warning isn't an issue. If you have additional applications, be sure to back up the client IDs so that you can reuse them when you recreate the applications later.

1. After the machine has been upgraded, open Server Manager, and complete the configuration of AD FS.
1. Configure AD FS by following the instructions in [Configure AD FS](./setup-deploy-on-premises-pu41.md#configureadfs). However, don't run the **Publish-ADFSApplicationGroup.ps1** script.
1. Run the following command.

    ```powershell
    # Host URL is your DNS record\host name for accessing the AOS
    .\Publish-ADFSApplicationGroup.ps1 -HostUrl 'https://ax.d365ffo.onprem.contoso.com' -ClientId <"Value of Active Directory->Client ID for AOS application group"> -FinancialReportingClientId <"Client ID for Financial Reporting application group"> -D365FOVersion <version>
    ```

#### Upgrade an AD FS farm

If you're using a Windows Internal Database (WID), follow the instructions in [Upgrading to AD FS in Windows Server 2016 using a WID database](/windows-server/identity/ad-fs/deployment/upgrading-to-ad-fs-in-windows-server).

If you're using a SQL Server database, follow the instructions in [Upgrading to AD FS in Windows Server 2016 with SQL Server](/windows-server/identity/ad-fs/deployment/upgrading-to-ad-fs-in-windows-server-sql).

#### Create a new AD FS farm/instance and replace your old AD FS farm/instance

1. Create a new AD FS federation farm/instance. For information about how to deploy AD FS, see [Windows Server AD FS Deployment Guide](/windows-server/identity/ad-fs/deployment/windows-server-2012-r2-ad-fs-deployment-guide).
1. Configure AD FS by following the instructions in [Configure AD FS](./setup-deploy-on-premises-pu41.md#configureadfs). However, don't run the **Publish-ADFSApplicationGroup.ps1** script.
1. In your existing AD FS farm, run the following command.

    ```powershell
    .\Get-DeploymentSettings.ps1 -ConfigurationFilePath .\ConfigTemplate.xml
    ```

1. Make a note of the following values: **Active Directory-\>Client ID for AOS application group** and **Active Directory-\>Client ID for Financial Reporting application group**.
1. In your new AD FS farm/instance, run the following command.

    ```powershell
    # Host URL is your DNS record\host name for accessing the AOS
    .\Publish-ADFSApplicationGroup.ps1 -HostUrl 'https://ax.d365ffo.onprem.contoso.com' -ClientId <"Value of Active Directory->Client ID for AOS application group"> -FinancialReportingClientId <"Client ID for Financial Reporting application group"> -D365FOVersion <version>
    ```

    Your new farm/instance is now ready to be used by Finance + Operations (on-premises).

1. If your new farm/instance endpoint differs from the old farm/instance endpoint, be sure to update the endpoint in Microsoft Dynamics Lifecycle Services (LCS) by selecting the **Update Settings** option and setting the **ADFS OpenID metadata endpoint** field to the new value.

1. If your new farm/instance identifier differs from the old farm/instance identifier, you must update the user info table so that it reflects the new configuration. As of version 2.17.0 of the infrastructure scripts, you can run the following command from one of your AOS nodes to automatically update and regenerate the configuration of each user.

    ```powershell
    Import-Module ".\D365FO-OP" -Force
    .\Reset-SID.ps1 -AxsfCodePath 'C:\ProgramData\SF\AOS_13\Fabric\work\Applications\AXSFType_App184\AXSF.Code.1.0.20190902'
    ```

### Post-upgrade actions

To correctly support authentication with the Office add-ins, AD FS on Windows Server 2019 or later requires that you set up Cross Origin Resource Sharing (CORS) headers. This information is available in [Configure AD FS](./setup-deploy-on-premises-pu41.md#configureadfs). If you aren't sure whether you're missing the configuration, run the following script.

```powershell
.\Test-ADFSConfiguration.ps1 -ConfigurationJsonFilePath "\\Fileserver\agent\wp\EN10\StandaloneSetup-746342\config.json" -D365FOVersion <version>
```

## Upgrade a node in your Service Fabric cluster

In Service Fabric standalone clusters, upgrade of a node's operating system is a machine-specific operation. (A node can be either a virtual machine \[VM\] or a physical machine.) There are two methods for doing an in-place upgrade for a node. In the first method, the upgrade operation preserves data and the operating system configuration. In the second method, the upgrade operation doesn't preserve data and the operating system configuration. You can also create new nodes and then add them to the cluster.

All the methods that are described in this section keeps your cluster up and running, and won't affect the availability of the service, provided that you don't upgrade all the nodes at the same time.

Regardless of the method that you use to upgrade the nodes, consider upgrading all the nodes in a node type before you proceed to another node type.

> [!IMPORTANT]
> If your cluster has only three seed nodes (**OrchestratorNodeType**), upgrade only one node at a time. Otherwise, the cluster won't be able to keep the system services running, and the cluster won't be available.
>
> If your cluster has only one Business Intelligence (BI)/Management Reporter (MR) node, you should schedule the node upgrade during a downtime window, because the related services won't be available during the upgrade process.

### Do an in-place upgrade that preserves operating system data

This method is the simplest option, because you deactivate the node, upgrade the operating system, and preserve all data. After the upgrade, node activation is required to bring the node back online.

1. In Service Fabric Explorer, deactivate (restart) the node that you want to upgrade.
1. Do an in-place upgrade by following the instructions in [Upgrade Windows Server 2016 to Windows Server 2019](/windows-server/upgrade/upgrade-2016-to-2019).
1. After the node is back-up, use the **Test-D365FOConfiguration.ps1** script to ensure that the upgrade didn't restore prerequisites to their default values. If the test script raises issues, run the **Configure-Prereqs.ps1** and **Complete-Prereqs.ps1** scripts to fix them.
1. In Service Fabric Explorer, activate the node.
1. Wait until the node is healthy again, and then repeat this procedure for the next nodes.

### Do an in-place upgrade that doesn't preserve operating system data

During the operating system upgrade, you remove all data. Therefore, the node has a fresh operating system installation. You'll have to complete all the configuration steps for each node before you add it back to the cluster.

1. In Service Fabric Explorer, deactivate (remove data for) the node that you want to upgrade.
1. Remove the node from the cluster by following the instructions in [Remove a node](./onprem-remove-reinstall-aos-node.md#remove-a-node).
1. Do an in-place upgrade by following the instructions in [Upgrade Windows Server 2016 to Windows Server 2019](/windows-server/upgrade/upgrade-2016-to-2019).
1. Add the node back to the cluster by following the instructions in [Add a node](./onprem-remove-reinstall-aos-node.md#add-a-node).
1. After the node is back up, activate it in Service Fabric Explorer.
1. Wait until the node is healthy again, and then repeat this procedure for the next nodes.

### Add new nodes to the cluster

This method resembles the previous method, but you spin up new nodes before you remove the existing nodes from the cluster. This approach helps maintain the performance of the service if you can't take nodes down.

1. Provision a new VM.
1. Add a node by following the instructions in [Add a node](./onprem-remove-reinstall-aos-node.md#add-a-node).
1. After the node has been added, and the services on it are healthy, repeat the previous steps to provision, configure, and add additional nodes.
1. After all the nodes have been added, remove the nodes that are running the older operating system by following the instructions in [Remove a node](./onprem-remove-reinstall-aos-node.md#remove-a-node).
