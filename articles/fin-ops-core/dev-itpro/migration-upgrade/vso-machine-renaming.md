---
title: Rename a local development (VHD) environment
description: Learn about how to rename a local environment so that you can access a Microsoft Azure DevOps project and install One Version service updates.
author: josaw1
ms.author: josaw
ms.topic: how-to
ms.date: 03/17/2026
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 4f5ff29b-9ae5-4ba2-8b6e-1e5d94e004b3
---

# Rename a local development (VHD) environment

[!include [banner](../includes/banner.md)]

You must rename a local development (VHD) environment for the following scenarios:

* **Accessing a single Microsoft Azure DevOps project across multiple machines:** Azure DevOps is required for version control. In development topologies, multiple virtual machines (VMs) can't access the same Azure DevOps project if they have the same machine name. Azure DevOps uses the machine name for identification. If you're developing on local VMs that you downloaded from Microsoft Dynamics Lifecycle Services (LCS), you might encounter problems.
* **Installing One Version service updates:** To install One Version service updates, such as 8.1.x, in VHD environments, you must use a runbook. To help guarantee that the runbook finishes successfully, you must rename the VHD environments. You must also complete the additional steps described in this article.

## Rename the machine

Rename and restart the machine before you start development or connect to Azure DevOps. Make sure that the new name is unique among all the machines that you use with the Azure DevOps project.

## Update the server name in SQL Server

Update the server name in Microsoft SQL Server 2016 by running the following commands.

```sql
sp_dropserver [old_name];
GO
sp_addserver [new_name], local;
GO
```

In these commands, replace **old\_name** with the old name of the server and **new\_name** with the new name. By default, the old name is **MININT-F36S5EH**, but you can run **select @@servername** to get the old name. Also, be sure to restart the SQL Server service after the commands finish running.

## Update SQL Server Reporting Services

Update the SQL Server Reporting Service (SSRS) database by using the Reporting Services Configuration Manager. Select **Database**, select **Change Database**, and use the new server name. Make sure that you use Reporting Services Configuration Manager for SQL Server 2016.

## Additional steps to install One Version service updates

To install One Version service updates in a VHD environment, complete the following additional steps.

### Update the Azure Storage Emulator

Update the Azure Storage Emulator, and make sure that it's running. From the **Start** menu, open **Microsoft Azure Storage Emulator - v4.0**, and run the following commands.

This command starts the emulator.

```Console
AzureStorageEmulator.exe start
```

This command verifies that the emulator is running.

```Console
AzureStorageEmulator.exe status
```

Try the **init** option with the **-server** switch or the **-forcecreate** switch. Be sure to replace **new\_name** with the new name.

```Console
AzureStorageEmulator.exe init -server new_name
AzureStorageEmulator.exe init -forcecreate
```

If the **init** command fails, delete the storage emulator database by using SQL Server Management Studio. Then try the following command.

```Console
AzureStorageEmulator.exe init
```

When you run this command, you might receive the following error message: "Error: Cannot create database." However, the emulator usually still starts. You just need the emulator to start.

### Update financial reporting

Update the server name for financial reporting by using a script that is included in the One Version service update. To get the command, download and expand the One Version service update.

Open a Microsoft Windows PowerShell command window as an admin, and run the following command. This command contains the default passwords that you might need to update. Be sure to replace **new\_name** with the new name.

```powershell
cd <update folder>\MROneBox\Scripts\Update
.\ConfigureMRDatabase.ps1 -NewAosDatabaseName AxDB -NewAosDatabaseServerName new_name -NewMRDatabaseName ManagementReporter -NewAxAdminUserPassword AOSWebSite@123 -NewMRAdminUserName MRUser -NewMRAdminUserPassword MRWebSite@123 -NewMRRuntimeUserName MRUSer -NewMRRuntimeUserPassword MRWebSite@123 -NewAxMRRuntimeUserName MRUser -NewAxMRRuntimeUserPassword MRWebSite@123
```

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
