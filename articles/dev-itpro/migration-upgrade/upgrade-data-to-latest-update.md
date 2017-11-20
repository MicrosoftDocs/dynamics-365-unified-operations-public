---
# required metadata

title: Upgrade data in development, demo, or sandbox environments
description: This topic provides instructions for upgrading your Microsoft Dynamics 365 for Finance and Operations, Enterprise edition, database to the latest update.
author: tariqbell
manager: AnnBe
ms.date: 11/10/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: margoc
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.custom: 106163
ms.assetid: 0c78b7a9-a360-4ef8-92ef-e4e9ff70cee7
ms.search.region: Global
# ms.search.industry: 
ms.author: tabell
ms.search.validFrom: 2016-05-31
ms.dyn365.ops.version: Platform update 1

---

# Upgrade data in development, demo, or sandbox environments

[!include[banner](../includes/banner.md)]

This topic provides instructions for upgrading your Microsoft Dynamics 365 for Finance and Operations, Enterprise edition, database in a Tier 1 environment to the latest update. A Tier 1 environment is also known as a development box, one-box, or demo environment. 

In some Tier 2 or higher environments, the Microsoft Service Engineering Team (DSE) will run the data upgrade for you. For more information, see the end-to-end upgrade process in [Overview of moving to the latest update of Microsoft Dynamics 365 for Finance and Operations](upgrade-latest-update.md#scenario-3-upgrade-to-the-most-current-application-release).

This topic describes how to upgrade an older source database to the latest Finance and Operations update. To copy a database from a production environment back to a one-box demo or development environment, follow the steps in [Copy a Microsoft Dynamics 365 for Finance and Operations database from Azure SQL Database to a Microsoft SQL Server Environment](..\database\copy-database-from-azure-sql-to-sql-server.md). 

> [!IMPORTANT]
> - You do **not** have to upgrade your database if you're updating to the latest platform of Finance and Operations. Platform updates are backward-compatible. This topic applies only to the process of upgrading between releases of Finance and Operations applications, such as an upgrade from release 1611 (November 2016) to the July 2017 release.
> - This process doesn't apply to the upgrade of data in the Financial reporting database. It also doesn't apply to the upgrade of document attachments that are stored in Microsoft Azure blob storage.

## Before you begin
1. Back up your current database. 
2. You must have a functional one-box demo or development environment that is already successfully running with the latest Finance and Operations update.
3. If you're upgrading from the Microsoft Dynamics AX February 2016 release (also known as RTW) to the May 2016 release, the following hotfixes must be installed in the destination environment:

    - KB 3170386, "Upgrade script error: ReleaseUpdateDB70\_DMF. updateIntegrationActivityExecutionMessageIdPreSync."
    - KB 3180871, "Data upgrade from RTW to Update 1 causes errors when synchronizing views involving disabled configuration keys." This hotfix is a binary hotfix that will cause the database synchronization process to fail.

    If you're upgrading to a version that is newer than the May 2016 release, you do **not** have to install these hotfixes. They are already included.

4. In your source environment, you must install one of the following hotfix, based on the version that you're upgrading from. These hotfixes correct a bug in the SysSetupLog logic, so that the upgrade process can detect the version that you're upgrading from:

    - If you're upgrading from the February 2016 release (also known as RTW or 7.0) 7.0.1265.3015: KB 4023685, "'Could not find source system version information' error when you upgrade to the latest Application Release"
    - If you're upgrading from the November 2016 release (also known as 1611 or 7.1) 7.1.1541.3036: KB 4023686, "'Could not find source system version information' error when you upgrade to the latest Application Release"
    - If you're upgrading from the July 2017 release (also known as 7.2) 7.2.11792.56024: No hotfix is required for this version.

5. In any one-box environment, after you install the application hotfixes from step 4, run a full database synchronization. This step is especially important for golden database environments. A full database synchronization is required, because this step fills a table (SysSetupLog) that is used when the database is upgraded. Don't run the database synchronization from Microsoft Visual Studio for this step, because the SysSetup interface won't be triggered. To trigger the SysSetup interface, run the following command from an Administrator **Command Prompt** window.

    ```
    cd J:\\AosService\\WebRoot\\bin>
    
    Microsoft.Dynamics.AX.Deployment.Setup.exe -bindir "J:\\AosService\\PackagesLocalDirectory" -metadatadir        J:\\AosService\\PackagesLocalDirectory -sqluser axdeployuser -sqlserver localhost -sqldatabase axdb -setupmode sync -syncmode fullall -isazuresql false -sqlpwd \<password for axdeployuser\>
    ```

5. If you are upgrading to the July 2017 release (also known as 7.2) 7.2.11792.56024, apply the following application X++ hotfixes in the destination environment before running the data upgrade in that environment. These will prevent various errors occurring during the data upgrade:

    - KB 4036156 - Retail minor version upgrade - 'Variant number sequence is not set.' This hotfix package also includes KB 4035399 and KB 4035751. Note that you must have a minimum of Platform Update 9 to use this package. If you are unsure, install the latest binaries.
    - KB 4045801 - "Scheduler job has failed" error encountered when upgrading from Fall 2016 update to July 2017 update.
    
6. If you are upgrading from Microsoft Dynamics AX 2012, install the following application X++ hotfixes in the destination environment before you run the data upgrade:
    - KB 4033183 - Dynamics AX 2012 R2 or Dynamics AX 2012 R3 Pre-CU8 non-retail upgrade fails with Object not found for dbo.RETAILTILLLAYOUTZONE.
    - KB 4040692 - Dynamics AX 2012 R3 to Microsoft Dynamics 365 for Operations 7.2 upgrade fails on RetailSalesLine duplicate index on SalesLineIdx.
    - KB 4035490 - Performance issue with GeneralJournalAccountEntry MainAccount field upgrade script.

7. If you're upgrading a database that began as a standard demo data database, you must also run the following script. This step is required, because the demo data contains bad records for some kernel X++ classes.

    ```
    delete from classidtable where id >= 0xf000 and id <= 0xffff
    ```

8. Make sure that all Commerce Data Exchange (CDX) jobs have been successfully run, and that you have no unsynchronized transactional data in the cloud version of the channel database.
9.  Delete the cloud version of the retail channel database in the source environment. This database will be re-created as part of the upgrade. Delete the primary cloud-hosted channel database by running the following script. 

    > [!NOTE]
    > If you have customizations that rely on the retail channel database schema, you might encounter errors in the following steps. If you encounter errors, you must delete your channel database customizations, and then rerun the script.
    
    ```
    /* Drop all non-system stored procs under schema crt and ax */
    DECLARE @schemaCrt INT
    DECLARE @schemaAx INT
    DECLARE @schemaExt INT

    SELECT @schemaCrt = schema_id FROM sys.schemas WHERE [NAME] = 'crt'
    SELECT @schemaAx = schema_id FROM sys.schemas WHERE [NAME] = 'ax'
    SELECT @schemaExt = schema_id FROM sys.schemas WHERE [NAME] = 'ext'

    DECLARE @name NVARCHAR(128)
    DECLARE @objId INT
    DECLARE @SQL NVARCHAR(1024)

    SELECT TOP 1 @name = [name], @objId = [object_id] FROM sys.procedures WHERE [schema_id] IN (@schemaCrt,@schemaAx,@schemaExt) ORDER BY [create_date] DESC

    WHILE @name is not null AND len(@name) > 0
    BEGIN
        SELECT @SQL = 'DROP PROCEDURE [' + OBJECT_SCHEMA_NAME(@objId) + '].[' + RTRIM(@name) +']'
        EXEC (@SQL)
        PRINT @SQL  
        SELECT @name = NULL, @objId = 0  
        SELECT TOP 1 @name = [name], @objId = [object_id] FROM sys.procedures WHERE [schema_id] IN (@schemaCrt,@schemaAx,@schemaExt) ORDER BY [create_date] DESC
    END
    GO

    /* Drop all views under schema crt, ax and ext */
    DECLARE @schemaCrt INT
    DECLARE @schemaAx INT
    DECLARE @schemaExt INT

    SELECT @schemaCrt = schema_id FROM sys.schemas WHERE [NAME] = 'crt'
    SELECT @schemaAx = schema_id FROM sys.schemas WHERE [NAME] = 'ax'
    SELECT @schemaExt = schema_id FROM sys.schemas WHERE [NAME] = 'ext'

    DECLARE @name NVARCHAR(128)
    DECLARE @objId INT
    DECLARE @SQL NVARCHAR(1024)

    /* Order by id DESC to remove the later view first since there may be some dependency between different views */
    SELECT TOP 1 @name = [name], @objId = [object_id] FROM sys.views WHERE [schema_id] IN (@schemaCrt,@schemaAx,@schemaExt) ORDER BY [create_date] DESC

    WHILE @name is not null AND len(@name) > 0
    BEGIN
        SELECT @SQL = 'DROP VIEW [' + OBJECT_SCHEMA_NAME(@objId) + '].[' + RTRIM(@name) +']'
        EXEC (@SQL)
        PRINT @SQL	
        SELECT @name = NULL, @objId = 0
        SELECT TOP 1 @name = [name], @objId = [object_id] FROM sys.views WHERE [schema_id] IN (@schemaCrt,@schemaAx,@schemaExt) ORDER BY [create_date] DESC
    END
    GO

    /* Drop all functions under schemas crt, ax and ext*/
    DECLARE @schemaCrt INT
    DECLARE @schemaAx INT
    DECLARE @schemaExt INT

    SELECT @schemaCrt = schema_id FROM sys.schemas WHERE [NAME] = 'crt'
    SELECT @schemaAx = schema_id FROM sys.schemas WHERE [NAME] = 'ax'
    SELECT @schemaExt = schema_id FROM sys.schemas WHERE [NAME] = 'ext'

    DECLARE @name NVARCHAR(128)
    DECLARE @objId INT
    DECLARE @SQL NVARCHAR(1024)

    SELECT TOP 1 @name = [name], @objId = id FROM sysobjects WHERE [type] IN (N'FN', N'IF', N'TF', N'FS', N'FT') AND OBJECT_SCHEMA_NAME(id) IN ('crt','ax','ext') ORDER BY [crdate] DESC

    WHILE @name IS NOT NULL AND len(LTRIM(RTRIM(@name))) > 0
    BEGIN
        SELECT @SQL = 'DROP FUNCTION [' + OBJECT_SCHEMA_NAME(@objId) + '].[' + RTRIM(@name) +']'
        EXEC (@SQL)
        PRINT @SQL
        SELECT @name = NULL, @objId = 0
        SELECT TOP 1 @name = [name], @objId = id FROM sysobjects WHERE [type] IN (N'FN', N'IF', N'TF', N'FS', N'FT') AND OBJECT_SCHEMA_NAME(id) IN ('crt','ax','ext') ORDER BY [crdate] DESC
        PRINT @name
    END
    GO

    /* Drop all foreign key constraints under schemas crt, ax and ext*/
    DECLARE @schemaCrt INT
    DECLARE @schemaAx INT
    DECLARE @schemaExt INT

    SELECT @schemaCrt = schema_id FROM sys.schemas WHERE [NAME] = 'crt'
    SELECT @schemaAx = schema_id FROM sys.schemas WHERE [NAME] = 'ax'
    SELECT @schemaExt = schema_id FROM sys.schemas WHERE [NAME] = 'ext'

    DECLARE @name NVARCHAR(128)
    DECLARE @constraint NVARCHAR(254)
    DECLARE @tableSchema NVARCHAR(254)
    DECLARE @SQL NVARCHAR(1024)

    SELECT TOP 1 @name = TABLE_NAME, @tableSchema = TABLE_SCHEMA FROM INFORMATION_SCHEMA.TABLE_CONSTRAINTS WHERE constraint_catalog=DB_NAME() AND CONSTRAINT_TYPE = 'FOREIGN KEY' AND CONSTRAINT_SCHEMA IN ('crt','ax','ext') ORDER BY TABLE_NAME

    WHILE @name is not null
    BEGIN
        SELECT @constraint = NULL
        SELECT @constraint = (SELECT TOP 1 CONSTRAINT_NAME FROM INFORMATION_SCHEMA.TABLE_CONSTRAINTS WHERE constraint_catalog=DB_NAME() AND CONSTRAINT_TYPE = 'FOREIGN KEY' AND TABLE_NAME = @name AND CONSTRAINT_SCHEMA IN ('crt','ax','ext') ORDER BY CONSTRAINT_NAME)
        WHILE @constraint IS NOT NULL
        BEGIN
            SELECT @SQL = 'ALTER TABLE [' + @tableSchema + '].[' + RTRIM(@name) +'] DROP CONSTRAINT [' + RTRIM(@constraint) +']'
            EXEC (@SQL)
            PRINT @SQL
            SELECT @constraint = NULL		
            SELECT @constraint = (SELECT TOP 1 CONSTRAINT_NAME FROM INFORMATION_SCHEMA.TABLE_CONSTRAINTS WHERE constraint_catalog=DB_NAME() AND CONSTRAINT_TYPE = 'FOREIGN KEY' AND CONSTRAINT_NAME <> @constraint AND TABLE_NAME = @name AND CONSTRAINT_SCHEMA IN ('crt','ax','ext') ORDER BY CONSTRAINT_NAME)
        END
    SELECT TOP 1 @name = TABLE_NAME, @tableSchema = TABLE_SCHEMA FROM INFORMATION_SCHEMA.TABLE_CONSTRAINTS WHERE constraint_catalog=DB_NAME() AND CONSTRAINT_TYPE = 'FOREIGN KEY' AND CONSTRAINT_SCHEMA IN ('crt','ax','ext') ORDER BY TABLE_NAME
    END
    GO

    /* Drop all tables under schemas crt, ax and ext */
    DECLARE @schemaCrt INT
    DECLARE @schemaAx INT
    DECLARE @schemaExt INT

    SELECT @schemaCrt = schema_id FROM sys.schemas WHERE [NAME] = 'crt'
    SELECT @schemaAx = schema_id FROM sys.schemas WHERE [NAME] = 'ax'
    SELECT @schemaExt = schema_id FROM sys.schemas WHERE [NAME] = 'ext'

    DECLARE @name NVARCHAR(128)
    DECLARE @objId INT
    DECLARE @SQL NVARCHAR(1024)

    SELECT TOP 1 @name = [name], @objId = [object_id] FROM sys.tables WHERE [schema_id] IN (@schemaCrt,@schemaAx,@schemaExt) ORDER BY [create_date] DESC

    WHILE @name IS NOT NULL
    BEGIN	
        SELECT @SQL = 'DROP TABLE [' + OBJECT_SCHEMA_NAME(@objId) + '].[' + RTRIM(@name) +']'
        EXEC (@SQL)
        PRINT @SQL	
        SELECT @name = NULL, @objId = 0
        SELECT TOP 1 @name = [name], @objId = [object_id] FROM sys.tables WHERE [schema_id] IN (@schemaCrt,@schemaAx,@schemaExt) ORDER BY [create_date] DESC
    END
    GO

    /* Drop all types under schemas crt, ax and ext */
    DECLARE @schemaCrt INT
    DECLARE @schemaAx INT
    DECLARE @schemaExt INT

    SELECT @schemaCrt = schema_id FROM sys.schemas WHERE [NAME] = 'crt'
    SELECT @schemaAx = schema_id FROM sys.schemas WHERE [NAME] = 'ax'
    SELECT @schemaExt = schema_id FROM sys.schemas WHERE [NAME] = 'ext'

    DECLARE @name NVARCHAR(128)
    DECLARE @schemaId INT
    DECLARE @SQL NVARCHAR(1024)

    /* Order by id DESC to remove the later type first since there may be some dependency between different types */
    SELECT TOP 1 @name = [name], @schemaId = [schema_id] FROM sys.types WHERE [schema_id] IN (@schemaCrt,@schemaAx,@schemaExt) ORDER BY [user_type_id] DESC

    WHILE @name is not null AND len(@name) > 0
    BEGIN
        SELECT @SQL = 'DROP TYPE [' + SCHEMA_NAME(@schemaId) + '].[' + RTRIM(@name) +']'
        EXEC (@SQL)
        PRINT @SQL	
        SELECT @name = NULL, @schemaId = 0
        SELECT TOP 1 @name = [name], @schemaId = [schema_id]  FROM sys.types WHERE [schema_id] IN (@schemaCrt,@schemaAx,@schemaExt) ORDER BY [user_type_id] DESC
    END
    GO

    /* Drop retail full text search catalog */
    IF EXISTS (SELECT 1 FROM sys.fulltext_catalogs WHERE [name] = 'COMMERCEFULLTEXTCATALOG')
    BEGIN
        DROP FULLTEXT CATALOG [COMMERCEFULLTEXTCATALOG]
    END

    /* Drop retail db roles */
    IF EXISTS (SELECT 1 FROM sys.procedures WHERE [name] = 'DropDatabaseRoleExt')
    BEGIN
        DROP PROCEDURE dbo.DropDatabaseRoleExt
    END
    GO

    CREATE PROCEDURE dbo.DropDatabaseRoleExt
    (
        @RoleName NVARCHAR(255)
    )
    AS BEGIN
        IF  EXISTS (SELECT * FROM dbo.sysusers WHERE name = @RoleName AND issqlrole = 1)
        BEGIN 
            DECLARE @RoleMemberName sysname	  
            /* Cursor to Loop in for Each Member have the Role Privilege and Drop RoleMember */
            DECLARE Member_Cursor CURSOR FOR
            SELECT [name]
            FROM dbo.sysusers
            WHERE UID IN (
                SELECT memberuid
                FROM dbo.sysmembers
                WHERE groupuid IN (
                    SELECT UID FROM dbo.sysusers WHERE [name] = @RoleName AND issqlrole = 1)) 
            OPEN Member_Cursor;

            FETCH NEXT FROM Member_Cursor INTO @RoleMemberName

            WHILE @@FETCH_STATUS = 0
            BEGIN 
                EXEC sp_droprolemember @rolename=@RoleName, @membername= @RoleMemberName 
                FETCH NEXT FROM Member_Cursor INTO @RoleMemberName
            END;

            CLOSE Member_Cursor;
            DEALLOCATE Member_Cursor;
            /* End Of Cursor */ 
        END
        /* Checking If Role Name Exists In Database */
        IF  EXISTS (SELECT * FROM sys.database_principals WHERE name = @RoleName AND TYPE = 'R')
        BEGIN
            DECLARE @SqlStatement NVARCHAR(1024)
            SELECT @SqlStatement = 'DROP ROLE ' + @RoleName
            EXEC sp_executesql @SqlStatement
        END
    END
    GO

    EXEC dbo.DropDatabaseRoleExt 'DataSyncUsersRole'
    EXEC dbo.DropDatabaseRoleExt 'ReportUsersRole'
    EXEC dbo.DropDatabaseRoleExt 'db_executor'
    EXEC dbo.DropDatabaseRoleExt 'PublishersRole'
    EXEC dbo.DropDatabaseRoleExt 'UsersRole'
    EXEC dbo.DropDatabaseRoleExt 'DeployExtensibilityRole'
    GO

    IF EXISTS (SELECT 1 FROM sys.procedures WHERE [name] = 'DropDatabaseRoleExt')
    BEGIN
        DROP PROCEDURE dbo.DropDatabaseRoleExt
    END
    GO

    /* Drop retail schema crt, ax, ext */
    IF EXISTS (SELECT 1 FROM sys.schemas WHERE [name] = 'crt')
    BEGIN
        DROP SCHEMA crt
    END
    GO

    IF EXISTS (SELECT 1 FROM sys.schemas WHERE [name] = 'ax')
    BEGIN
        DROP SCHEMA ax
    END
    GO

    IF EXISTS (SELECT 1 FROM sys.schemas WHERE [name] = 'ext')
    BEGIN
        DROP SCHEMA ext
    END
    GO
    ```

## Download the latest data upgrade deployable packages
To obtain the latest data upgrade deployable packages for your target environment that is running the latest Finance and Operations update, download the latest binary updates from Microsoft Dynamics Lifecycle Services (LCS).

1. In LCS, in the **Environments** section, select your target Finance and Operations environment, scroll to the bottom of the page, and then select the **All binary updates** tile (or **Platform updates** tile).
2. On the **Binary updates** page, select **Download binaries**. On the next page, select **Save package** to save it to the LCS Asset library.
3. Go to the **Asset library** > **Software deployable package** tab and download the package. Extract it and then go to the following directory to find the appropriate data upgrade deployable package file: ..\\CustomDeployablePackage

    The name of the data upgrade deployable packages varies, depending on the version that you're upgrading from and the version that you're upgrading to:

    - If you're upgrading from Microsoft Dynamics AX 2012, the packages are named **MajorVersionDataUpgrade.zip** and **MajorversionDataUpgrade_Retail.zip**. Both packages need to be run one after the other. To find these packages, download the latest binary updates.
    - If you're upgrading from a previous release of Finance and Operations, the packages are named **MinorVersionDataUpgrade.zip** and **MinorVersionDataUpgrade_Retail.zip**. Both packages need to be run one after the other. To find these packages, download the latest binary updates (In versions before Platform update 4, there was one package named **DataUpgrade.zip**).

> [!NOTE]
> Computers that are deployed from LCS will already have a local data upgrade package. However, that file is out of date and includes issues that have been resolved in later hotfixes. Always download the latest version of the file from LCS.

## Remove encryption certification rotation
1. Extract the MinorVersionDataUpgrade.zip deployable package to C:\\Temp or a location of your choice.
2. In a text editor, open the C:\\Temp\\DataUpgrade\\RotateConfigData\\ServicingRotations.json file. Modify the file as shown here, and save it. This step is required only for one-box environments. Because you're removing the need for encryption certificate rotations, old data in encrypted fields in your database will no longer be readable. This issue is a technical limitation for a one-box data upgrade. New data that goes into those fields after the upgrade is completed won't be affected. For information about the affected fields, see the ["Encrypted fields in demo data"](#encrypted-fields-in-demo-data) section later in this topic.

    ```
    {
        "AosService": {
            "EncryptionThumbprint": null,
            "SigningThumbprint": null,
            "Certificates": [
                ],
            "CertificateThumbprints": [
                ],
            "KeyValues": [
                ]
        }
    }
    ```

3. Run the Windows PowerShell Integrated Scripting Environment (ISE) as an administrator.
4. Open C:\\Temp\\DataUpgrade\\RotateConfigData\\Scripts\\EncryptRotationConfigData.ps1.
5. Press F5 to run the script.

### Fix the duplicate key issue (February 2016 release only)

This step is required if you're upgrading a database from the February 2016 release (also known as RTW).

1. In a text editor, open the C:\\Temp\\DataUpgrade\\AOSService\\Scripts\\AutoDataUpgradePreReqs.ps1 file.
2. Comment out or remove the following line.

    ```
    Invoke-SQL -sqlCommand:$adjustsqlseq
    ```

3. Save the file.

## Upgrade the database
1. Install the deployable package from the C:\\Temp\\DataUpgrade folder (the location that you extracted the deployable package to earlier). For instructions, see [Install a deployable package](../deployment/install-deployable-package.md).
2. Import or restore a backup of the source database to your one-box demo or development environment that is already running the latest Finance and Operations update that you want to upgrade to. Leave the existing database in place and name your new database **imported_new**.

    > [!NOTE]
    > For better upload/download speed between Azure virtual machines (VMs), we recommend that you use AzCopy. For information about how to download and use AzCopy to copy to or from an Azure blob store, see [Transfer data with the AzCopy Command-Line Utility](https://azure.microsoft.com/en-us/documentation/articles/storage-use-azcopy/).

3. Run the runbook file from the deployable package until you reach Step 4: GlobalBackup.
4. Rename the existing database suffixing it with "_orig", and rename the newly restored database with the original database name, so they switch places:

    ```
    ALTER DATABASE <original D365 database> MODIFY NAME = <original D365 database>_ORIG
    ALTER DATABASE imported_new MODIFY NAME = <original D365 database>
    ```

5. Create a backup of the source database, in case you need to revert to it, because the following steps will modify the source database.
6. Mark Step 4 of the runbook as completed, and continue to run the runbook until it's completed. 

> [!NOTE]
> When upgrading to Platform update 8 or later or when upgrading from AX 2012 - you need to repeat the steps above in the **Upgrade the database section** for the related _Retail package after running the first package.

## Re-enable SQL change tracking
Run the following SQL against the upgraded database to make sure that change tracking is enabled at the database level. You must specify the name of your database in the **alter database** command.

```
ALTER DATABASE [<your AX database name>] SET CHANGE_TRACKING = ON (CHANGE_RETENTION = 6 DAYS, AUTO_CLEANUP = ON)
```

## Additional steps for financial reporting

Reset the financial reporting data mart by following the steps in [Resetting the financial reporting data mart after restoring a database](../analytics/reset-financial-reporting-datamart-after-restore.md). Then reimport the building block groups that you exported in an earlier step.

## Troubleshoot upgrade script errors
The following sections provide information that can help you troubleshoot.

### Rerun the runbook after a data upgrade script failure

A data upgrade deployable package enables the runbook to be rerun in a more granular manner than a typical deployable package. The data upgrade scripts begin to be run at Step 5 of the runbook. If you experience a failure during Step 5, view the output in the command window to learn which substep you reached. For example, if you reached substep 5.3, use the following command to rerun from that substep.

```
AXUpdateInstaller.exe execute -runbookid=upgrade -rerunstep=5.3
```

When you're debugging, you can keep rerunning a script that fails without having to rerun the whole data upgrade piece and database synchronization.

### View more details about a script error

Upgrade scripts run in X++ by using a batch process that the runbook installer starts. In Application Explorer in Visual Studio, there are classes that you can view that are prefixed with **ReleaseUpdate**. If an upgrade script fails during the runbook process, you can learn more details about the reason for the error by opening Management Studio and querying ReleaseUpdateScriptsErrorLog as follows.

```
select \* from RELEASEUPDATESCRIPTSERRORLOG
```

You can add that code to a new runnable class in Visual Studio, and directly observe, debug, and rework its behavior.

### Skip failed scripts

> [!IMPORTANT]
> This process is intended to be used only in a development scenario. 

You can skip all scripts that have failed a specific number of times and move to the next viable scripts. This functionality helps with troubleshooting process. By design, the process is very manual, so that you're less likely to unintentionally skip scripts. 

In the ReleaseUpdateConfiguration table, there is a new field that is named **ScriptRetryCount**. The value in this field controls how many times the runbook process will rerun scripts before it ignores them. When the runbook is run, the system updates the **ReleaseUpdateScriptsErrorLog.ErrorCount** field every time that a specific script fails. A new row is created for each script. 

In the DataUpgrade package folder, under ..\\AosServices\\Scripts\\, there is a script that is named IgnoreBlockingScripts.ps1. Run this script from an Administrator Windows PowerShell window to skip all scripts where **ScriptRetryCount**=**ErrorCount**. Then rerun the runbook step that failed, so that scripts will be ignored. The **ReleaseUpdateScriptsErrorLog.Ignored** field will also be set for each script that is skipped. Therefore, you can easily identify skipped scripts later.

### Monitor the duration of scripts that are run

Every script that is successfully run records the number of minutes that it took in the **ReleaseUpdateScriptsLog.DurationMins** column. Therefore, you can easily identify the longest-running scripts when you're trying to tune the performance of the data upgrade process. Note that the duration is the amount of time that each script takes to run. However, because multiple scripts run in parallel, the sum of values in the **DurationMins** column will exceed the overall duration of the upgrade process.

## Known issues
### A duplicate key was found for the object that is named dbo.RESOURCESETUP
When you upgrade a database, you might receive the following error message during the database synchronization phase of the runbook process:

> Database execution failed: The CREATE UNIQUE INDEX statement terminated because a duplicate key was found for the object name 'dbo.RESOURCESETUP' and the index name 'I_6716AK'

This issue is a known issue that will be resolved in a future hotfix. The workaround is to delete the duplicate rows from the table by running the following SQL script against the database from Management Studio.

```
delete RS from ResourceSetup as RS
join ResResourceIdentifier as RRI on RRI.RecId = RS.Resource_
join WrkCtrTable as WCT on WCT.RecId = RRI.RefRecId
join DirPartyTable as DPT on DPT.DataArea = WCT.DataAreaId
where DPT.DataArea != '' and RS.LegalEntity != DPT.RecId
```

### A record can't be selected in Dimension hierarchy nodes (CAMDataDimensionHierarchyNode)
When you upgrade a database, you might receive the following error message during the database synchronization phase of the runbook process:

>  Cannot select a record in Dimension hierarchy nodes (CAMDataDimensionHierarchyNode). Dimension hierarchy: 0. The SQL database has issued an error. Object Server DynamicsAXBatchManagement:  [Microsoft][ODBC Driver 13 for SQL Server][SQL Server]Invalid column name 'RELATIONTYPE'. 

This issue is a known issue that will be resolved in a future release. The workaround is to create a missing field in several tables by running the following SQL script against the database from Management Studio.

```
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
DROP PROCEDURE IF EXISTS [DBO].PATCHRELATIONTYPE
GO 

CREATE PROCEDURE [DBO].PATCHRELATIONTYPE
        @TABLENAME SYSNAME
    AS
    BEGIN
        DECLARE @TABLEID		INT	;
        DECLARE @FIELDID		INT	;
        DECLARE @FIELDNAME		SYSNAME;
        DECLARE @SQLTATEMENT NVARCHAR(1024);
        DECLARE @TOTALRECORDS	INT;
        DECLARE @ParmDefinition			NVARCHAR(150);

        SET NOCOUNT ON;

        SELECT @FIELDNAME = 'RELATIONTYPE';
        SELECT @FIELDID = 61453; --Hardcoded in code DBFIELD_DISCRIMINATOR
        IF OBJECT_ID(@TABLENAME, 'U') IS NULL 
        BEGIN
            PRINT @TABLENAME + ' table does not exists. Please provide a base table';
            RETURN;
        END

        IF EXISTS(SELECT 1 FROM SYS.COLUMNS
            WHERE NAME = @FIELDNAME
            AND OBJECT_ID = OBJECT_ID(@TABLENAME))
        BEGIN
            PRINT @TABLENAME + ' table contains RelationType. No patching needed.';
            RETURN;
        END
        PRINT @TABLENAME + ' table does not contain RelationType.';
        SELECT @TABLEID = ID FROM TABLEIDTABLE WHERE NAME = @TABLENAME;
        IF @@ROWCOUNT <> 1
        BEGIN
            PRINT @TABLENAME + ' was not present in TABLEIDTABLE. Cannot proceed!!';
            RETURN;
        END 

        -- Ensure that instancerelationtype is added. We don't want to randomly add relationtype to any table.
        IF NOT EXISTS (SELECT \* FROM SQLDICTIONARY WHERE TABLEID = @TABLEID AND NAME = 'InstanceRelationType')		
        BEGIN
            PRINT @TABLENAME + ' table does not exist. Please provide a base table';
            RETURN;
        END

        -- Ensure SQLDictionary is populated
        IF NOT EXISTS (SELECT \* FROM SQLDICTIONARY WHERE TABLEID = @TABLEID AND FIELDID = @FIELDID)
        BEGIN
            INSERT INTO SQLDICTIONARY (TABLEID, FIELDID, ARRAY, NAME, SQLNAME, FIELDTYPE, STRSIZE, SHADOW, RIGHTJUSTIFY, NULLABLE, FLAGS, RECVERSION)
            VALUES (@TABLEID,@FIELDID,1, @FIELDNAME, @FIELDNAME, 49, 0, 0, 0, 0, 0, 1);
            PRINT 'Inserted into SqlDictionary';
        END

        -- Actual alter statement
        SELECT @SQLTATEMENT = 'ALTER TABLE ' + @TABLENAME +  ' ADD ' + @FIELDNAME + ' BIGINT NOT NULL DEFAULT 0';
        PRINT 'Issuing ' + @SQLTATEMENT;
        EXEC (@SQLTATEMENT);

        SELECT @SQLTATEMENT = 'UPDATE ' + @TABLENAME +  ' SET RELATIONTYPE = 0';
        PRINT 'Issuing ' + @SQLTATEMENT;
        EXEC (@SQLTATEMENT);
    END;
GO
exec PatchRelationType  'CAMDATADIMENSIONHIERARCHYNODE'
exec PatchRelationType  'CAMDataJournal'
exec PatchRelationType  'CAMDataCostAccountingLedgerSourceEntryProvider'
exec PatchRelationType  'CAMDataImportedDimensionMember'
```

### An index can't be created on InventDistinctProduct
When you upgrade a database, you might receive the following error message during the database synchronization phase of the runbook process:

> Cannot create index on InventDistinctProduct a duplicate key exists on column Product.

This issue is a known issue that will be resolved in a future release. The workaround is to delete all records in the InventDistinctProduct table and then resume the runbook from the current step. The records in the InventDistinctProduct table are disposable. They will be regenerated the first time that Finance and Operations is started, when an item is created, or when MRP is run. To delete all records in InventDistinctProduct, run the following query against the current database from Management Studio.

```
truncate table InventDistinctProduct
```

To resume the runbook from the current step, run the following command.

```
axupdateinstaller execute -runbookid=<your runbook name> -rerunstep=<the last step number>
```

For example, you can use this command.

```
axupdateinstaller execute -runbookid=dataupgrade -rerunstep=5.4
```

### An exchange rate can't be found when demo data is upgraded

When you upgrade a demo database, you might receive the following error message when you deploy the DataUpgrade package:

> An exchange rate cannot be found for exchange rate type Default between currencies INR and BRL on exchange date 12/1/2014.

Because you're upgrading demo data, look in the TrvUnreconciledExpenseTransaction table, which is where the expense line is. Change the currency to **USD**. (Because the data is demo data, you don't have to be careful to preserve this expense line.)

```
update TrvUnreconciledExpenseTransaction
set transactioncurrencycode = 'USD'
where transactioncurrencycode = 'INR'
```

Alternatively, go to the original environment that the data came from (such as the old version), and add the missing exchange rate at **General Ledger** &gt; **Currencies** &gt; **Currency exchange rates**. You must add a record for INR and BRL that covers 2014. Then bring that database into your new environment, and start the upgrade against that database.

### The interpreter evaluation stack has grown during a call to the kernel

If you've enabled database logging on a kernel table such as UserInfom, you might receive the following error message:

> Executing step: 5.1  
> prereq for data upgrade  
> prereq for data upgrade  
> Unhandled exception More Information: The interpreter evaluation stack has grown during a call to the kernel method xRecord::Delete (), height before call: 0, height after call: 3. Unhandled exception More Information: KernelInstance: Kernel is accessing deleted memory  
> The step failed

To resolve this issue, review the database log setup at **System administration** &gt; **Setup** &gt; **Database log setup**. Remove records for kernel tables as you require.

### The batch process fails to start

The batch process can fail if the environment has been left in [maintenance mode](../sysadmin/maintenance-mode.md) after a change to the configuration keys. To resolve this issue, turn maintenance mode off, and then resume the runbook process.

### The system fails to locate or generate a user GUID

You might receive the following error message:

> …Unhandled exception More Information: System failed to locate or generate a user GUID…

To resolve this issue, rerun the runbook step that failed. You will then be able to continue.

### Pre-sync or post-sync errors on ReleaseUpdateDB71\_LedgerPeriodClose

You might receive one of the following error messages on the **preSyncLedgerPeriodCloseTemplateTask**, **updateMenuItemTypeForCurrencyReval**, or **updateLedgerPeriodCloseTemplateTask** method in the **ReleaseUpdateDB71\_LedgerPeriodClose** class:

> Cannot execute the required database operation. The SQL database has issued an error. Object Server DynamicsAXBatchManagement: \[Microsoft\]\[SQL Server Native Client 11.0\]\[SQL Server\]Invalid column name 'TEMPLATE'. INSERT INTO LedgerPeriodCloseTemplateTaskTmp ( TEMPLATE, AREA, NAME, MENUITEM, MENUITEMTYPE, TARGETDAYSFROMPROJECTCOMPLETE, DUETIME, LEGALENTITYSELECTION, RECVERSION, PARTITION, RECID, CLOSINGROLE, LINENUM) SELECT T1.TEMPLATE, T1.AREA, T1.NAME, T1.MENUITEM, T1.MENUITEMTYPE, T1.TARGETDAYSFROMPROJECTCOMPLETE, T1.DUETIME, T1.LEGALENTITYSELECTION, T1.RECVERSION, T1.PARTITION, T1.RECID, T1.CLOSINGROLE, 0 FROM LedgerPeriodCloseTemplateTask T1 session 1013 (Admin) Microsoft.Dynamics.Ax.Xpp.ErrorException: Cannot execute the required database operation. The SQL database has issued an error.

> Cannot execute the required database operation. The SQL database has issued an error. Object Server DynamicsAXBatchManagement: \[Microsoft\]\[SQL Server Native Client 11.0\]\[SQL Server\]Invalid column name 'MENUITEMTYPE'. UPDATE LedgerPeriodCloseTemplateTaskTmp SET MENUITEMTYPE = 0 WHERE MENUITEMTYPE = 2 AND MENUITEM = 'LedgerExchAdj' AND PARTITION = 5637144576 session 1013 (Admin) Microsoft.Dynamics.Ax.Xpp.ErrorException: Cannot execute the required database operation. The SQL database has issued an error.

> Cannot execute the required database operation. The SQL database has issued an error. Object Server DynamicsAXBatchManagement: \[Microsoft\]\[SQL Server Native Client 11.0\]\[SQL Server\]Invalid column name 'TEMPLATE'. INSERT INTO LedgerPeriodCloseTemplateTask ( TEMPLATE, AREA, NAME, MENUITEM, MENUITEMTYPE, TARGETDAYSFROMPROJECTCOMPLETE, DUETIME, LEGALENTITYSELECTION, RECVERSION, PARTITION, RECID, CLOSINGROLE, LINENUM) SELECT T1.TEMPLATE, T1.AREA, T1.NAME, T1.MENUITEM, T1.MENUITEMTYPE, T1.TARGETDAYSFROMPROJECTCOMPLETE, T1.DUETIME, T1.LEGALENTITYSELECTION, T1.RECVERSION, T1.PARTITION, T1.RECID, T1.CLOSINGROLE, T1.LINENUM FROM LedgerPeriodCloseTemplateTaskTmp T1 session 1013 (Admin)

To resolve this issue, manually drop the LedgerPeriodCloseTemplateTaskTmp table from the database by using Management Studio. Then rerun the runbook step. This issue will be fixed in a future hotfix.

### KB number 3170386

If KB number 3170386 isn't installed, you will receive the following error message:

> GlobalUpdate script for service model: AOSService on machine …. Etc …. UpgradeServiceHelper::WaitForDataUpgradeToComplete(Object\[\]… The step failed

This error is caused by a failure in the pre-sync or the post-sync substep of the data upgrade. Follow these steps to determine which substep failed and the details of the failure. 

> [!NOTE]
> You can't rerun the failed runbook step until the pre-sync or post-sync substep has been manually completed, and the AutoDataUpgrade.config file has been updated to skip the substeps that have already been run.

1. In File Explorer, in the **DataUpgradeAosServiceScripts** folder, sort by descending order of date modified, and then look at the file at the top of the list to determine which substep failed.

    - If the top file is named **dbUpgrade*PreSync*Monitor.error.log**, the pre-sync substep failed.
    - If the top file is named **dbUpgrade*PostSync*Monitor.error.log**, the post-sync substep failed.

2. In Management Studio, run the following **SELECT** statement.

    ```
    SELECT * FROM RELEASEUPDATELOG
    ```

    The second-to-last record in the result set will have the errors and call stacks for all the failures.

### DMF errors

If you receive either of the following Data Migration Framework (DMF) errors, download hotfix KB number 3170386, and then restart the upgrade process.

#### DMF pre-sync error

> Batch error: initial.DAT.ReleaseUpdateDB70\_DMF.updateIntegrationActivityExecutionMessageIdPreSync (Batch:AOS-F01B9F0CCC8, 9, Info, Error, ):\[\[1\]\[3,Cannot execute the required database operation. The SQL database has issued an error.\]\[3,Object Server DynamicsAXBatchManagement: \]\[3,\[Microsoft\]\[SQL Server Native Client 11.0\]\[SQL Server\]Incorrect syntax near 'GO'.\]\[3,

#### DMF post-sync error

> Batch error: initial.DAT.ReleaseUpdateDB70\_DMF.updateIntegrationActivityExecutionMessageIdPostSync (Batch:AOS-F01B9F0CCC8, 9, Info, Error, ):\[\[1\]\[3,Cannot execute the required database operation. The SQL database has issued an error.\]\[3,Object Server DynamicsAXBatchManagement: \]\[3,\[Microsoft\]\[SQL Server Native Client 11.0\]\[SQL Server\]Incorrect syntax near 'GO'.\]\[3,

## Encrypted fields in demo data
After upgrade, values in encrypted fields in the database will be unreadable. However, new values that are entered in these fields after upgrade will be readable. This behavior occurs because of a technical limitation that is related to the certificate that is used for data encryption. The following table shows the fields that are affected.

| Table.Field                                                      | Data exists in demo data |
|------------------------------------------------------------------|--------------------------|
| CreditCardAccountSetup.SecureMerchantProperties                  | Yes                      |
| ExchangeRateProviderConfigurationDetails.Value                   | Yes                      |
| RetailChannelPaymentConnectorLine.SecureMerchantProperties       | Yes                      |
| RetailConnDatabaseProfile.ConnectionString                       | Yes                      |
| RetailHardwareProfile.SecureMerchantProperties                   | Yes                      |
| RetailHardwareProfileMerchantInfoEntity.SecureMerchantProperties | Yes                      |
| FiscalEstablishment\_BR.ConsumerEFDocCsc                         | No                       |
| FiscalEstablishmentEntity.CSC                                    | No                       |
| FiscalEstablishmentStaging.CSC                                   | No                       |
| HcmPersonIdentificationNumber.PersonIdentificationNumber         | No                       |
| HcmWorkerActionHire.PersonIdentificationNumber                   | No                       |
| SysEmailSMPTPassword.Password                                    | No                       |
| SysOAuthUserTokens.EncryptedAccessToken                          | No                       |
| SysOAuthUserTokens.EncryptedRefreshToken                         | No                       |

## See also

[Overview of moving to the latest update of Microsoft Dynamics 365 for Finance and Operations](upgrade-latest-update.md)
