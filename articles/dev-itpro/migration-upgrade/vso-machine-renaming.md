---
# required metadata

title: Renaming a local development (VHD) environment to access Azure DevOps or install One Version service updates
description: Renaming a VHD environment is required in order to access a Azure DevOps project across multiple machines and to successfully install One Version service updates.
author: MargoC
manager: AnnBe
ms.date: 12/04/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: robinr
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.custom: 25911
ms.assetid: 4f5ff29b-9ae5-4ba2-8b6e-1e5d94e004b3
ms.search.region: Global
# ms.search.industry: 
ms.author: tabell
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Rename a local development (VHD) environment to access Azure DevOps and install One Version service updates

[!include [banner](../includes/banner.md)]

## Renaming a VHD environment is required for the following scenarios
* Access a single Azure DevOps project across multiple machines
* Install One Version service updates such as 8.1.x

Azure DevOps (formerly known as Visual Studio Online (VSO) or Visual Studio Team Services (VSTS)) is needed to support using version control. In development topologies, multiple VMs cannot access the same Azure DevOps project if they have the same machine name. Azure DevOps uses the machine name for identification. If you are developing on local VMs downloaded from Microsoft Lifecycle Services (LCS), you may encounter issues.

One Version service updates must be installed on VHD environments using a runbook. These steps are needed to ensure the runbook will complete successfully.

## Rename the machine
Rename and reboot the machine before you start development or connect to Azure DevOps. Make sure the new name is unique within all the machines used with the Azure DevOps project.

## Update the server name in SQL Server
Update the server name in SQL Server 2016 by running the following commands. The default old name is *MININT-F36S5EH* or you can use **select @@servername** to get the old name. Make sure to update the **new_name** in the command and to restart the SQL Server service when this is done. 

    sp_dropserver [old_name];
    GO
    sp_addserver [new_name], local;
    GO

## Update SQL Server Reporting Services
Update the SQL Server Reporting Service database using the Reporting Services Configuration Manager. To do that, select Database then Change Database and use the new server name. Make sure you use Reporting Services Configuration Manager for SQL Server 2016.

## Additional steps required to install One Version service updates
The following steps are required to install One Version service updates on a VHD environment.

## Update the Azure Storage Emulator
Update the Azure Storage Emulator and make sure it is running. From the start menu, Open the *Microsoft Azure Storage Emulator - v4.0* and use the following commands.

This command starts the emulator.

    AzureStorageEmulator.exe start

This command checks the emulator to verify it is running.

    AzureStorageEmulator.exe status

Try the init option with *-server* switch or the *-forcecreate* switch. Make sure to update the **new_name** in the commmand.

    AzureStorageEmulator.exe init -server new_name
    AzureStorageEmulator.exe init -forcecreate

If the init command fails, delete the storage emulator database using SQL Server Management Studio and try the following command. The command may return the error *Error: Cannot create database.* but the emulator will usually still start and that all that is needed.

    AzureStorageEmulator.exe init

## Update financial reporting
Update the server name for financial reporting using a script included in the One Version service update. To get the command, you have to download and expand the One Version service update. Open a PowerShell command window as an administrator and run the following command. The command contains the default passwords that may need to be updated. Make sure to update the **new_name** in the command.

    cd <update folder>\MROneBox\Scripts\Update
    .\ConfigureMRDatabase.ps1 -NewAosDatabaseName AxDB -NewAosDatabaseServerName new_name -NewMRDatabaseName ManagementReporter -NewAxAdminUserPassword AOSWebSite@123 -NewMRAdminUserName MRUser -NewMRAdminUserPassword MRWebSite@123 -NewMRRuntimeUserName MRUSer -NewMRRuntimeUserPassword MRWebSite@123 -NewAxMRRuntimeUserName MRUser -NewAxMRRuntimeUserPassword MRWebSite@123
