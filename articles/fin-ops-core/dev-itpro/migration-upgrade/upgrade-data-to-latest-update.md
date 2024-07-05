---
title: Upgrade data in development or demo environments
description: Access instructions for upgrading your finance and operations application release, including an overview on selecting the correct data upgrade deployable package.
author: laneswenka
ms.author: laswenka
ms.topic: article
ms.date: 11/01/2021
ms.custom: 
ms.reviewer: johnmichalak 
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2016-05-31
ms.search.form:
ms.dyn365.ops.version: Platform update 1
---

# Upgrade data in development or demo environments

[!include [banner](../includes/banner.md)]

> [!IMPORTANT]
> The process that is described here is now deprecated for data upgrade between older versions of finance and operations apps and the latest version. For more information about Dynamic AX 2012 upgrades, see [Upgrade from AX 2012 to finance and operations](upgrade-overview-2012.md).

This article explains how to upgrade an older database to the latest finance and operations application release.

The article provides instructions for upgrading your finance and operations database in a Tier 1 environment to the latest update. A Tier 1 environment is also known as a development, one-box, or demo environment. 

In Tier 2 or higher environments, including Production, you will run through the self-service upgrade steps as outlined in [Self-service upgrade to the latest version](self-service-upgrade.md).

> [!IMPORTANT]
> - You do **not** have to upgrade your database if you're updating to the latest **platform** of finance and operations. Platform updates are backward-compatible. This article applies only to the process of upgrading between releases of finance and operations applications, such as an upgrade from Microsoft Dynamics 365 for Operations version 1611 (November 2016) to Finance and Operations 8.0.
> - This process doesn't apply to the upgrade of document attachments that are stored in Microsoft Azure blob storage.
> - All upgraded custom code has to be applied on the environment before running the data upgrade process.
> - If you are on version 8.0 or later, there is no longer a data upgrade between application versions.

## Before you begin

1. Back up your current database.
1. You must have a functional environment that is already successfully running the update.
1. In the **source** environment, you must install one of the following hotfixes, depending on the version that you're upgrading from. These hotfixes correct an issue in the SysSetupLog logic, so that the upgrade process can detect the version that you're upgrading from:

   - **If you're upgrading from the November 2016 release (also known as 1611 or 7.1, build 7.1.1541.3036):** KB 4023686, "'Could not find source system version information' error when you upgrade to the latest Application Release."
   - **If you're upgrading from the July 2017 release (also known as 7.2, build 7.2.11792.56024):** No hotfix is required for this version.
   - After you install application hotfixes required in this step, run a full database synchronization. This step is especially important for golden database environments. A full database synchronization fills the SysSetupLog table, which is used when the database is upgraded. Don't run the database synchronization from Microsoft Visual Studio for this step, because the SysSetup interface won't be triggered. To trigger the SysSetup interface, run the following command from an Administrator **Command Prompt** window.

     ```Console
     cd J:\AosService\WebRoot\bin>

     Microsoft.Dynamics.AX.Deployment.Setup.exe -bindir "J:\AosService\PackagesLocalDirectory" -metadatadir        J:\AosService\PackagesLocalDirectory -sqluser axdeployuser -sqlserver localhost -sqldatabase axdb -setupmode sync -syncmode fullall -isazuresql false -sqlpwd \<password for axdeployuser\>
     ```

1. If you're upgrading to Dynamics 365 Finance version 10.0.9 or 10.0.10, install the quality updates in the destination environment before you run the data upgrade.
1. If you're upgrading a database that began as a standard demo data database, you must also run the following script. This step is required because the demo data contains bad records for some kernel X++ classes.

    ```sql
    delete from classidtable where id >= 0xf000 and id <= 0xffff
    ```

1. Make sure that all Commerce Data Exchange (CDX) jobs have been successfully run, and that there is no unsynchronized transactional data in the cloud version of the channel database.

## Select the correct data upgrade deployable package

To obtain the latest data upgrade deployable package for a target environment that is running the latest update, download it from the Microsoft Dynamics Lifecycle Services (LCS) Shared asset library.
1. Sign in to [LCS](https://lcs.dynamics.com/).
2. Select the **Shared asset** library tile.
3. In the Shared asset library, under **Select asset type**, select **Software deployable package**.
4. In the list of deployable package files, find the data upgrade package that corresponds to your upgrade.

    - If you're upgrading from AX 2012, the package name starts with **AX2012DataUpgrade**. Select the package that corresponds to the release you are upgrading to. For example, **AX2012DataUpgrade-10-0**.
    - If you're upgrading from a previous release to the latest 10.0.X release, the package name is  **DataUpgrade-10-0**. 
    - If you're upgrading from a previous release to a preview release, the package name contains PREVIEW. For example, **DataUpgrade-10-0-2-PREVIEW**.
5. Select the package that corresponds to the release that you are upgrading to. 

## Upgrade the database

1. Extract the data upgrade deployable package to **C:\\Temp** or a location of your choice.
   > [!NOTE] 
   > Skip this step if this is a development environment that is connected to LCS and you are planning to execute the data upgrade process directly from LCS.

2. Import or restore a backup of the source database (the database that you will be upgrading) to the demo or development environment that is already running the latest update that you want to upgrade to. Leave the existing database in place, and name your new database **imported\_new**.

    > [!NOTE]
    > If you are validating the data upgrade of your production database running on the earlier release: To copy a database from a production environment back to a demo or development environment, follow the steps in [Export a copy of the standard user acceptance testing (UAT) database](../database/dbmovement-scenario-exportuat.md).   
    > 
    > For better upload/download speed between Azure virtual machines (VMs), we recommend that you use AzCopy. For information about how to download AzCopy, and how to use it to copy to or from an Azure blob store, see [Transfer data with the AzCopy Command-Line Utility](/azure/storage/common/storage-use-azcopy-v10).

3. Rename the original database by adding the suffix **\_orig**. Rename the newly restored database so that it has the same name as the original database. In this way, the two databases switch places.

    ```sql
    ALTER DATABASE <original Dynamics 365 database> MODIFY NAME = <original Dynamics 365 database>_ORIG
    ALTER DATABASE imported_new MODIFY NAME = <original Dynamics 365 database>
    ```

4. Create a backup of the source database, in case you have to revert to it. This step is important because the following steps will modify the source database.

5. Execute the data upgrade package from the **C:\\Temp\\DataUpgrade** folder (the location that you extracted the deployable package to earlier). Executing a data upgrade package is similar to installing any software deployable package. For detailed instructions, see [Install deployable packages from the command line](../deployment/install-deployable-package.md#generate-a-runbook-from-the-topology). Start at the section titled **Generate a runbook from the topology** then execute the steps in the section 
**Install a deployable package**. 

> [!NOTE]
> If you are upgrading a database on a development environment, you can instead execute the data upgrade package directly from the LCS environment page, using the **Maintain > Apply Updates** servicing functionality. This does not require the user to be a local Administrator on the development VM. This is available as of the [February](https://blogs.msdn.microsoft.com/lcs/2018/02/13/lcs-february-2018-release-1-release-notes/) release of LCS. 
>
> This will upgrade your finance and operations database, channel database, and reset the Financial reporting database.

## Re-enable SQL change tracking

Run the following SQL against the upgraded database to make sure that change tracking is enabled at the database level. You must specify the name of your database in the **alter database** command.

```sql
ALTER DATABASE [<your AX database name>] SET CHANGE_TRACKING = ON (CHANGE_RETENTION = 6 DAYS, AUTO_CLEANUP = ON)
```

## Refresh the data entities list

If you have upgraded to Platform update 14 or later, then you will need refresh the data entity list in the Data management workspace (**Data management** > **Framework parameters** > **Entity settings** > **Refresh entity list**) to ensure that the entity list is rebuilt on the latest platform and that the required metadata is available for data management operations. 

## Troubleshoot upgrade script errors

This section provides information that can help you troubleshoot various issues.

### Rerun the runbook after a data upgrade script failure

A data upgrade deployable package enables the runbook to be rerun in a more granular manner than a typical deployable package. The data upgrade scripts begin to be run at Step 5 of the runbook. If you experience a failure during Step 5, view the output in the command window to learn which substep you reached. For example, if you reached substep 5.3, use the following command to rerun from that substep.

```Console
AXUpdateInstaller.exe execute -runbookid=upgrade -rerunstep=5.3
```

When you're debugging, you don't have to rerun the whole data upgrade piece and database synchronization. You can keep rerunning just the script that fails.

### View more details about a script error

Upgrade scripts run in X++ by using a batch process that the runbook installer starts. In Application Explorer in Visual Studio, some classes that you can view are prefixed with **ReleaseUpdate**. If an upgrade script fails during the runbook process, you can learn more about the reason for the error by opening Microsoft SQL Server Management Studio and running the following code to query ReleaseUpdateScriptsErrorLog.

```sql
select \* from RELEASEUPDATESCRIPTSERRORLOG
```

You can add this code to a new runnable class in Visual Studio, and directly observe, debug, and rework its behavior.

### Skip failed scripts

> [!IMPORTANT]
> This process is intended to be used only in a development scenario.

You can skip all scripts that have failed a specific number of times, and move to the next viable scripts. This functionality helps with the troubleshooting process. By design, the process is very manual, so that you're less likely to unintentionally skip scripts.

In the ReleaseUpdateConfiguration table, there is a new field that is named **ScriptRetryCount**. The value in this field controls how many times the runbook process will rerun scripts before it ignores them. When the runbook is run, the system updates the **ReleaseUpdateScriptsErrorLog.ErrorCount** field every time that a specific script fails. A new row is created for each script.

In the DataUpgrade package folder, under ..\\AosServices\\Scripts\\, there is a script that is named IgnoreBlockingScripts.ps1. Run this script from an Administrator Windows PowerShell window to skip all scripts where **ScriptRetryCount**=**ErrorCount**. Then rerun the runbook step that failed, so that scripts will be ignored. The **ReleaseUpdateScriptsErrorLog.Ignored** field will also be set for each script that is skipped. Therefore, you can easily identify skipped scripts later.

### Monitor the duration of scripts that are run

Every script that is successfully run records the number of minutes that it took in the **ReleaseUpdateScriptsLog.DurationMins** column. Therefore, you can easily identify the longest-running scripts when you're trying to tune the performance of the data upgrade process. Note that the duration is the amount of time that each script takes to run. However, because multiple scripts run in parallel, the sum of values in the **DurationMins** column will exceed the overall duration of the upgrade process.

## Known issues
### A duplicate key was found for the object that is named dbo.RESOURCESETUP

When you upgrade a database, you might receive the following error message during the database synchronization phase of the runbook process:

> Database execution failed: The CREATE UNIQUE INDEX statement terminated because a duplicate key was found for the object name 'dbo.RESOURCESETUP' and the index name 'I\_6716AK'

This issue is a known issue that will be resolved in a future hotfix. The workaround is to delete the duplicate rows from the table by running the following SQL script against the database from Management Studio.

```sql
delete RS from ResourceSetup as RS
join ResResourceIdentifier as RRI on RRI.RecId = RS.Resource_
join WrkCtrTable as WCT on WCT.RecId = RRI.RefRecId
join DirPartyTable as DPT on DPT.DataArea = WCT.DataAreaId
where DPT.DataArea != '' and RS.LegalEntity != DPT.RecId
```

### A record can't be selected in Dimension hierarchy nodes (CAMDataDimensionHierarchyNode)

When you upgrade a database, you might receive the following error message during the database synchronization phase of the runbook process:

> Cannot select a record in Dimension hierarchy nodes (CAMDataDimensionHierarchyNode). Dimension hierarchy: 0. The SQL database has issued an error. Object Server DynamicsAXBatchManagement:  \[Microsoft\]\[ODBC Driver 13 for SQL Server\]\[SQL Server\]Invalid column name 'RELATIONTYPE'. 

This issue is a known issue that will be resolved in a future release. The workaround is to create a missing field in several tables by running the following SQL script against the database from Management Studio.

```sql
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

This issue is a known issue that will be resolved in a future release. The workaround is to delete all records in the InventDistinctProduct table and then resume the runbook from the current step. The records in the InventDistinctProduct table are disposable. They will be regenerated the first time that finance and operations is started, when an item is created, or when MRP is run. To delete all records in InventDistinctProduct, run the following query against the current database from Management Studio.

```sql
truncate table InventDistinctProduct
```

To resume the runbook from the current step, run the following command.

```Console
axupdateinstaller execute -runbookid=<your runbook name> -rerunstep=<the last step number>
```

For example, you can use this command.

```Console
axupdateinstaller execute -runbookid=dataupgrade -rerunstep=5.4
```

### An exchange rate can't be found when demo data is upgraded

When you upgrade a demo database, you might receive the following error message when you deploy the data upgrade package:

> An exchange rate cannot be found for exchange rate type Default between currencies INR and BRL on exchange date 12/1/2014.

Because you're upgrading demo data, look in the TrvUnreconciledExpenseTransaction table, which is where the expense line is. Change the currency to **USD**. (Because the data is demo data, you don't have to be careful to preserve this expense line.)

```sql
update TrvUnreconciledExpenseTransaction
set transactioncurrencycode = 'USD'
where transactioncurrencycode = 'INR'
```

Alternatively, go to the original environment that the data came from (such as the old version), and add the missing exchange rate at **General Ledger** &gt; **Currencies** &gt; **Currency exchange rates**. You must add records for Indian rupee (INR) and Brazilian real (BRL) that cover 2014. Then bring that database into your new environment, and start the upgrade against that database.

### The interpreter evaluation stack has grown during a call to the kernel

If you've enabled database logging on a kernel table such as UserInfom, you might receive the following error message:

> Executing step: 5.1  
> prereq for data upgrade  
> prereq for data upgrade  
> Unhandled exception More Information: The interpreter evaluation stack has grown during a call to the kernel method xRecord::Delete (), height before call: 0, height after call: 3. Unhandled exception More Information: KernelInstance: Kernel is accessing deleted memory  
> The step failed

To resolve this issue, review the database log setup at **System administration** &gt; **Setup** &gt; **Database log setup**. Remove records for kernel tables as you require.

### The batch process fails to start

The batch process can fail if the environment was left in [maintenance mode](../sysadmin/maintenance-mode.md) after the configuration keys were changed. To resolve this issue, turn maintenance mode off, and then resume the runbook process.

### The system fails to locate or generate a user GUID

You might receive the following error message:

> …Unhandled exception More Information: System failed to locate or generate a user GUID…

To resolve this issue, rerun the runbook step that failed. You will then be able to continue.

### Pre-sync or post-sync errors on ReleaseUpdateDB71\_LedgerPeriodClose

You might receive one of the following error messages on the **preSyncLedgerPeriodCloseTemplateTask**, **updateMenuItemTypeForCurrencyReval**, or **updateLedgerPeriodCloseTemplateTask** method in the **ReleaseUpdateDB71\_LedgerPeriodClose** class:

> Cannot execute the required database operation. The SQL database has issued an error. Object Server DynamicsAXBatchManagement: \[Microsoft\]\[SQL Server Native Client 11.0\]\[SQL Server\]Invalid column name 'TEMPLATE'. INSERT INTO LedgerPeriodCloseTemplateTaskTmp ( TEMPLATE, AREA, NAME, MENUITEM, MENUITEMTYPE, TARGETDAYSFROMPROJECTCOMPLETE, DUETIME, LEGALENTITYSELECTION, RECVERSION, PARTITION, RECID, CLOSINGROLE, LINENUM) SELECT T1.TEMPLATE, T1.AREA, T1.NAME, T1.MENUITEM, T1.MENUITEMTYPE, T1.TARGETDAYSFROMPROJECTCOMPLETE, T1.DUETIME, T1.LEGALENTITYSELECTION, T1.RECVERSION, T1.PARTITION, T1.RECID, T1.CLOSINGROLE, 0 FROM LedgerPeriodCloseTemplateTask T1 session 1013 (Admin) Microsoft.Dynamics.Ax.Xpp.ErrorException: Cannot execute the required database operation. The SQL database has issued an error.
> 
> Cannot execute the required database operation. The SQL database has issued an error. Object Server DynamicsAXBatchManagement: \[Microsoft\]\[SQL Server Native Client 11.0\]\[SQL Server\]Invalid column name 'MENUITEMTYPE'. UPDATE LedgerPeriodCloseTemplateTaskTmp SET MENUITEMTYPE = 0 WHERE MENUITEMTYPE = 2 AND MENUITEM = 'LedgerExchAdj' AND PARTITION = 5637144576 session 1013 (Admin) Microsoft.Dynamics.Ax.Xpp.ErrorException: Cannot execute the required database operation. The SQL database has issued an error.
> 
> Cannot execute the required database operation. The SQL database has issued an error. Object Server DynamicsAXBatchManagement: \[Microsoft\]\[SQL Server Native Client 11.0\]\[SQL Server\]Invalid column name 'TEMPLATE'. INSERT INTO LedgerPeriodCloseTemplateTask ( TEMPLATE, AREA, NAME, MENUITEM, MENUITEMTYPE, TARGETDAYSFROMPROJECTCOMPLETE, DUETIME, LEGALENTITYSELECTION, RECVERSION, PARTITION, RECID, CLOSINGROLE, LINENUM) SELECT T1.TEMPLATE, T1.AREA, T1.NAME, T1.MENUITEM, T1.MENUITEMTYPE, T1.TARGETDAYSFROMPROJECTCOMPLETE, T1.DUETIME, T1.LEGALENTITYSELECTION, T1.RECVERSION, T1.PARTITION, T1.RECID, T1.CLOSINGROLE, T1.LINENUM FROM LedgerPeriodCloseTemplateTaskTmp T1 session 1013 (Admin)

To resolve this issue, use Management Studio to manually drop the LedgerPeriodCloseTemplateTaskTmp table from the database. Then rerun the runbook step. This issue will be fixed in a future hotfix.

### Table Sync Failed for Table: WarrantyGroupConfigurationItem

If you're upgrading to Dynamics 365 Finance version 10.0.9 or 10.0.10, you might receive the following error message during data upgrade:

> Table Sync Failed for Table: WarrantyGroupConfigurationItem

To resolve the issue, roll back the database upgrade, install the quality updates in the destination environment, and then rerun the data upgrade. 

### KB number 3170386

If KB number 3170386 isn't installed, you will receive the following error message:

> GlobalUpdate script for service model: AOSService on machine …. Etc …. UpgradeServiceHelper::WaitForDataUpgradeToComplete(Object\[\]… The step failed

This error is caused by a failure in the pre-sync or the post-sync substep of the data upgrade. Follow these steps to determine which substep failed and the details of the failure.

> [!NOTE]
> You can't rerun the failed runbook step until the pre-sync or post-sync substep has been manually completed, and the AutoDataUpgrade.config file has been updated to skip the substeps that have already been run.

1. In File Explorer, in the **DataUpgradeAosServiceScripts** folder, sort by descending order of the date when files were last modified, and then look at the file at the top of the list to determine which substep failed.

    - If the top file is named **dbUpgrade*PreSync*Monitor.error.log**, the pre-sync substep failed.
    - If the top file is named **dbUpgrade*PostSync*Monitor.error.log**, the post-sync substep failed.

2. In Management Studio, run the following **SELECT** statement.

    ```sql
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

## Additional resources

[Process for moving to the latest update of finance and operations](/dynamics365/unified-operations/dev-itpro/migration-upgrade/upgrade-latest-update)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]

