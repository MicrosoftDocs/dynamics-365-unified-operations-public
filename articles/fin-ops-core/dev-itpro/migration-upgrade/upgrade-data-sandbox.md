---
# required metadata

title: Upgrade from AX 2012 - Data upgrade in sandbox environments
description: This topic explains how to perform a data upgrade from Microsoft Dynamics AX 2012 to Finance and Operations in a sandbox environment. 
author: laneswenka
manager: AnnBe
ms.date: 12/03/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: laswenka
ms.search.validFrom: 2017-06-16
ms.dyn365.ops.version: Platform update 8
---

# Upgrade from AX 2012 - Data upgrade in sandbox environments

[!include [banner](../includes/banner.md)]

[!include [upgrade banner](../includes/upgrade-banner.md)]

> [!NOTE]
> This topic is being phased out in favor of a new process that is based on the dacpac file format. For information about the new process, see [Upgrade from AX 2012 - Dacpac process to upgrade data in Sandbox Tiers 2-5 environments](upgrade-data-sandbox-dacpac.md).

The output of this task is an upgraded database that you can use in a sandbox environment. In this topic, we use the term *sandbox* to refer to a Standard or Premier Acceptance Testing (Tier 2/3) or higher environment connected to a SQL Azure database. On this environment business users and functional team members can validate application functionality. This functionality includes customizations and the data that was brought forward from Microsoft Dynamics AX 2012.

We strongly recommend that you run the data upgrade process in a development environment before you run it in a shared sandbox environment, because this approach will help reduce the overall time that is required for a successful data upgrade. For more information, see [Upgrade from AX 2012 - Pre-upgrade checklist for data upgrade](prepare-data-upgrade.md).

> [!NOTE]
> It's very important that you install the latest version of SQLPackage before you start this process. To do this, go to [Download and Install SQLPackage](/sql/tools/sqlpackage-download). We recommend that you use the .NET Core version. This can be saved and extracted to C:\temp.

## Overview of the sandbox data upgrade process
Before you start to upgrade data in a sandbox environment, you will have already upgraded data in a development environment, as explained in [Upgrade from AX 2012 - Pre-upgrade checklist for data upgrade](prepare-data-upgrade.md). The two processes are very similar. The main difference is that a sandbox environment uses Microsoft Azure SQL Database for data storage, whereas a development environment uses Microsoft SQL Server. This technical difference in the database layer requires that you  modify the data upgrade procedure slightly in a sandbox environment, because a backup from the AX 2012 database instance can't just be restored to SQL Database.

![Sandbox data upgrade process](./media/data-upgrade-sandbox.png)

Here are the high-level steps in the upgrade process.

1. Turn off the AX 2012 AOS instances.
2. Create a copy of the AX 2012 database. We strongly recommend that you use a copy, because you must delete some objects in the copy that will be exported.
3. Export the copied database to a bacpac file by using a free SQL Server tool that is named SQLPackage.exe. This tool provides a special type of database backup that can be imported into SQL Database.
4. Upload the bacpac file to Azure storage.
5. Download the bacpac file to the Application Object Server (AOS) machine in the sandbox environment, and then import it by using SQLPackage.exe. You must then run a script against the imported database to reset the SQL database users.
6. Run the appropriate data upgrade package against the imported database.

## Turn off the AX 2012 AOS instances

This task involves the AX 2012 system administrator and the server administrators.

Before you turn off AOS instances, you must stop all batch jobs that are running. A long-running batch job that has already started to run will prevent the system from stopping. Plan ahead, so that you can stop your AOS instances when needed. You might have to schedule batches so that they're completed some time before you turn off AX 2012.

You might have other systems that are integrated with the AX 2012 environment. You must also factor these systems into your plan to turn off AX 2012. For example, you might have to turn off the integrated systems some time before you turn off AX 2012 itself, so that any remaining in-flight transactions can be completed. The requirements for integrated systems vary widely from business to business. Therefore, your team of experts must plan for this scenario independently.

## Create a copy of the AX 2012 database

You must create a copy of the AX 2012 database that you're upgrading, because you must delete some objects from the database. These objects include any Microsoft Windows authentication users. These changes make the modified database unusable for AX 2012. During this step, you will create a copy of the database and delete these objects.

This step must be done by the database administrator (DBA) or a person who has similar knowledge and experience.

To create a database copy, make a backup of the original database, and restore it under a new name. Make sure that enough space is available for both databases. You can create the copy on a different server. The version of the SQL Server instance that runs the database isn't important.

To perform this action, right-click the source database, and then select **Tasks** \> **Backup**. Create a full-copy backup. To avoid overwriting your existing database backups, you might want to save the file under a different name in the backup directory.

## Run the T-SQL script to prepare the database

This script prepares the database by removing users, removing procedures related to the AX 2012 RTM model store, cleaning up schemas, dropping views, and dropping references to tempDB. 

After the copy is created, run the following Transact-SQL (T-SQL) script against it.

```sql
--remove NT users as these are not supported in Azure SQL Database
declare 
@SQL varchar(255),
@UserName varchar(255)

set quoted_identifier off

declare     userCursor CURSOR for
select name from sys.sysusers where (isntuser = 1 or isntgroup =1) and name <> 'dbo'

OPEN userCursor
    FETCH userCursor into @UserName
    WHILE @@Fetch_Status = 0
       BEGIN
           set @SQL = 'DROP USER [' + @UserName + ']'
           exec(@SQL)
           FETCH userCursor into @UserName
       END
CLOSE userCursor
DEALLOCATE userCursor

go

--remove any AX 2012 RTM model store procedures that still exist
declare 
@SQL varchar(255),
@procname varchar(255)

set quoted_identifier off

declare     procCursor CURSOR for
select name from sys.procedures where name like 'XI_%' or name like 'XU_%'

OPEN procCursor
    FETCH procCursor into @procname
    WHILE @@Fetch_Status = 0
       BEGIN
           set @SQL = 'DROP PROCEDURE [' + @procname + ']'
           exec(@SQL)
           FETCH procCursor into @procname
       END
CLOSE procCursor
DEALLOCATE procCursor

go

--If you receive a message that you cannot delete users because they own a schema, then check which schema the user owns. 
--Either change the ownership to another user (for example to dbo) or drop the schema if it does not contain any objects. 
--The examples below are for an AX 2012 demo environment. You will need to edit this for your specific environment.

    if exists (select 1 from sys.schemas where name = 'contoso\admin')
begin
    drop schema [contoso\admin]
end
if exists (select 1 from sys.schemas where name = 'contoso\Domain Users')
begin
    drop schema [CONTOSO\Domain Users]
end
go

--drop all views in the current database because some refresh the tempDB, which is not a supported action in Azure SQL Databases
declare 
@SQL2 varchar(255),
@ViewName varchar(255)

set quoted_identifier off

declare     viewCursor CURSOR for

select viewname = v.name
from sys.views v
order by v.name

OPEN viewCursor

FETCH viewCursor into @ViewName
    WHILE @@Fetch_Status = 0
       BEGIN
           set @SQL2 = 'DROP VIEW ' + @ViewName
           exec(@SQL2)
           FETCH viewCursor into @ViewName
       END
CLOSE viewCursor
DEALLOCATE viewCursor
go

-- Drop the following procedure because it contains a tempDB reference that is not supported in Azure SQL Database
If exists (select 1 from sys.procedures where name = 'MaintainShipCarrierRole')
begin
    drop procedure MaintainShipCarrierRole
end
```

## Export the copied database to a bacpac file

> [!NOTE]
> This topic is being phased out in favor of a new process that is based on the dacpac file format. For information about the new process, see [Upgrade from AX 2012 - Dacpac process to upgrade data in Sandbox Tiers 2-5 environments](upgrade-data-sandbox-dacpac.md).

Export the copied database to a bacpac file by using the SQLPackage.exe tool. This step should be done by the DBA or a team member who has equivalent knowledge.

> [!IMPORTANT]
> It's very important that you install the latest version of SQL Server Management Studio before you start this step. Although SQLPackage is present in earlier versions of Management Studio, it won't work correctly for this step unless you first install the latest version.


This step is important, because the export will have to be done again during the downtime before go-live. Here are some tips:

- The bacpac process is very I/O and CPU intensive. Therefore, run the export on a high-powered machine.
- SQLPackage should be run locally on the machine that hosts the database. Don't run SQLPackage on a local laptop that you connect to the database machine, because this process is also network intensive.

Next, open a **Command Prompt** window as an administrator, and run the following commands.

```Console
cd C:\Program Files (x86)\Microsoft SQL Server\130\DAC\bin\

SqlPackage.exe /a:export /ssn:localhost /sdn:<database to export> /tf:D:\Exportedbacpac\my.bacpac /p:CommandTimeout=1200 /p:VerifyFullTextDocumentTypesSupported=false
```

Here is an explanation of the parameters:

- **ssn** (source server name) – The name of the SQL Server to export from. For this process, the parameter should always be set to **localhost**.
- **sdn** (source database name) – The name of the database to export.
- **tf** (target file) – The path and name of the file to export to. The folder should already exist, but the file will be created by the process.
- **/p:CommandTimeout** – The per-query timeout value. This parameter enables larger tables to be exported without a timeout.

## Upload the bacpac file to Azure storage or the LCS Asset Library

The bacpac file you have created will need to be copied to the AOS machine in your Azure hosted sandbox environment. There are several reasons for this:
1. The Azure SQL Database instance used by your Tier 2 (or higher) sandbox environment has firewall rules preventing access from outside of the environment itself.
2. Performance of bacpac import is multiple times faster when importing from a machine within the same Azure datacenter as the Azure SQL database instance.

You can choose how you would like to move the bacpac file to the AOS machine - you may have your own SFTP or other secure file transfer service. We recommend to use our Azure storage, which would require that you acquire your own Azure storage account on your own Azure subscription (this is not provided within the Dynamics subscription itself). There are free tools to help you to move files between Azure storage, from a command line you can use [Azcopy](/azure/storage/storage-use-azcopy), or for a GUI experience you can use [Microsoft Azure storage explorer](https://storageexplorer.com/). Use one of these tools to first upload the backup from your on-premises environment to Azure storage and then on your download it on your development environment.

Another option is to use the Asset library in Microsoft Dynamics Lifecycle Services (LCS). However, the upload and download will take longer than Azure storage. To use this option:
1. Sign in to your project in LCS and go to your Asset library.
2. Select the Database backup tab.
3. Upload the bacpac file.
Since the removal of RDP access to Sandbox AOS servers, we recommend that you use a cloud hosted environment running in the same region as the sandbox environment to import the file. You can download the bacpac onto the cloud hosted VM by logging into LCS on that and downloading it from the LCS Asset library.

## Import the bacpac file into SQL Database

> [!NOTE]
> This topic is being phased out in favor of a new process that is based on the dacpac file format. For information about the new process, see [Upgrade from AX 2012 - Dacpac process to upgrade data in Sandbox Tiers 2-5 environments](upgrade-data-sandbox-dacpac.md).

During this step, you will import the exported bacpac file into the SQL Database instance that your sandbox environment uses. As stated above, since the removal of RDP access to Sandbox AOS servers, we recommend that you use a cloud hosted environment running in the same region as the sandbox environment to import the file. Although you can request JIT access to the database and run from a local server, to do that follow the process for [Enable just-in-time database access](../database/database-just-in-time-JIT-access.md) to allow-list your IP address to the database.

You must first install the latest version of Management Studio on your cloud hosted VM or local server. You will then import the file by using the SQLPackage.exe tool.

If using a cloud hosted environment, for performance reasons, we recommend that you put the bacpac file on drive D on the AOS machine. On Azure virtual machines (VMs), drive D is a physical disk that typically has higher performance than other available disks.

Open a **Command Prompt** window as an administrator, and run the following commands.

```Console
cd C:\Program Files (x86)\Microsoft SQL Server\130\DAC\bin\

SqlPackage.exe /a:import /sf:D:\Exportedbacpac\my.bacpac /tsn:<azure sql database server name>.database.windows.net /tdn:<New database name> /tu:sqladmin /tp:<password from LCS> /mp:64 /p:CommandTimeout=1200 /p:DatabaseEdition=<Edition> /p:DatabaseServiceObjective=<Service objective> /p:DatabaseMaximumSize=<Maximum size>
```

Here is an explanation of the parameters:

- **sf** (source file) – The path and name of the file to import from.
- **tsn** (target server name) – The name of the SQL Azure server to import to. The name can be found in LCS. Suffix it with **.database.windows.net**.
- **tdn** (target database name) – The name of the database to import to. The database should not already exist. The import process will create it.
- **tu** (target user) – The SQL user name for the target SQL Database instance. We recommend that you use **sqladmin**. You can retrieve the password for this user from your LCS project.
- **tp** (target password) – The SQL password for the target SQL database instance.
- **mp** (max parallelism) - Specifies the degree of parallelism for concurrent operations running against a database. The default value is 8. A value of 64 provides the best performance in most scenarios.
- **/p:CommandTimeout** – The per-query timeout value. This parameter enables larger tables to be exported without a timeout.
- **/p:DatabaseEdition** – Specifies the edition of the database such as Basic, Standard, Premium, GeneralPurpose, BusinessCritical, or Hyperscale. To meet performance requirements and comply with your service agreement, use the same service objective level as the current Finance and Operations database (AXDB) on this environment. You can check the value for the existing database by using Management Studio. Right-click the database, and then select **Properties**.
- **/p:DatabaseServiceObjective** – Specifies the performance level of the database such as S1, P2, P4, or GP_Gen5_8. To meet performance requirements and comply with your service agreement, use the same service objective level as the current Finance and Operations database (AXDB) on this environment. You can check the value for the existing database by using Management Studio. Right-click the database, and then select **Properties**.
- **/p:DatabaseMaximumSize** – Defines the maximum size in GB of an Azure SQL database. You may need to use this parameter to allow a large database to be imported.

After you run the commands, you may receive the following warning. You can safely ignore it.

![Sandbox error](./media/sandbox-2.png)

If you receive an error message about a non-valid value, double-check your parameters. If they are okay, you may need to use a newer version of SqlPackage. You can use the [Windows .NET Core](/sql/tools/sqlpackage-download) version without the need to install. It is a .zip file that can be extracted to C:\Temp\Sqlpackage-dotnetcore, for example. Now when you import the database, instead of using the Sqlpackage.exe under C:\Program Files (x86) you can use the Sqlpackage.exe in C:\Temp\Sqlpackage-dotnetcore.


## Run a T-SQL script to update the database
Run the following script against the imported database. The script performs the following actions:

-   Recreates database users
-   Sets the correct performance parameters
-   Enables the SQL Query Store feature

```sql
CREATE USER axdeployuser FROM LOGIN axdeployuser
EXEC sp_addrolemember 'db_owner', 'axdeployuser'

CREATE USER axdbadmin WITH PASSWORD = 'password from lcs'
EXEC sp_addrolemember 'db_owner', 'axdbadmin'

CREATE USER axruntimeuser WITH PASSWORD = 'password from lcs'
EXEC sp_addrolemember 'db_datareader', 'axruntimeuser'
EXEC sp_addrolemember 'db_datawriter', 'axruntimeuser'

CREATE USER axmrruntimeuser WITH PASSWORD = 'password from lcs'
EXEC sp_addrolemember 'ReportingIntegrationUser', 'axmrruntimeuser'
EXEC sp_addrolemember 'db_datareader', 'axmrruntimeuser'
EXEC sp_addrolemember 'db_datawriter', 'axmrruntimeuser'

CREATE USER axretailruntimeuser WITH PASSWORD = 'password from lcs'
EXEC sp_addrolemember 'UsersRole', 'axretailruntimeuser'
EXEC sp_addrolemember 'ReportUsersRole', 'axretailruntimeuser'

CREATE USER axretaildatasyncuser WITH PASSWORD = 'password from lcs'
EXEC sp_addrolemember 'DataSyncUsersRole', 'axretaildatasyncuser'

ALTER DATABASE SCOPED CONFIGURATION  SET MAXDOP=2
ALTER DATABASE SCOPED CONFIGURATION  SET LEGACY_CARDINALITY_ESTIMATION=ON
ALTER DATABASE SCOPED CONFIGURATION  SET PARAMETER_SNIFFING= ON
ALTER DATABASE SCOPED CONFIGURATION  SET QUERY_OPTIMIZER_HOTFIXES=OFF
ALTER DATABASE imported-database-name SET COMPATIBILITY_LEVEL = 130;
ALTER DATABASE imported-database-name SET QUERY_STORE = ON;
```

## Run the data upgrade deployable package

For Tier-2 sandbox environments, you can now run the data upgrade package directly from LCS, just as you can do for Tier-1 DevTest environments. To apply the package, go to your environment in LCS, and select **Maintain** \> **Apply updates**. Scroll to the bottom of the list, and wait for the data upgrade packages to be loaded from the Shared asset library. It might take some time for the packages to be loaded. If no data upgrade packages appear in the list, go to your project settings in LCS, and make sure that your legacy system is set to **AX2012 Upgrade**. You can then apply the packages.

The name of the package that you select should match your version. For example, to upgrade to version 10.0.14, select **AX2012DataUpgrade-10-0-14**.

For more information, see [Upgrade data in development or demo environments](upgrade-data-to-latest-update.md). 

### Upgrade a copy of the database in a development environment

It is highly recommended to have upgraded the same database in a development environment. If you have a copy of the database available for development environments, it will be much easier to investigate bugs that are found in the upgraded sandbox environment.
