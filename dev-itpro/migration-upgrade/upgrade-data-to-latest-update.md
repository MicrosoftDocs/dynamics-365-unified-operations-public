---
# required metadata

title: Upgrade data in development, demo, or sandbox environments
description: This topic provides instructions for upgrading your Microsoft Dynamics 365 for Finance and Operations database to the latest update.
author: tariqbell
manager: AnnBe
ms.date: 07/10/2017
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
ms.search.scope: Operations, Platform, UnifiedOperations, AX Platform
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


This topic provides instructions for upgrading your Microsoft Dynamics 365 for Finance and Operations database to the latest update. 
Note that the Microsoft Service Engineering (DSE) Team will execute this process for you if:

- You must be live in production or have already deployed your production environment
- DSE will perform the data upgrade in one Tier 2 or higher sandbox environment
- DSE will perform the data upgrade in the production environment
- DSE will not perform the data upgrade in any additional Tier 2 or higher sandbox environments. You do not need to upgrade these - simply delete them, redeploy, and then make a database refresh request to copy a database from a Tier 2 or higher environment which was already upgraded. Alternatively you can upgrade them manually by following [Process for Upgrading a Sandbox Environment](../upgrade-sandbox-environment.md)
- DSE will not perform the data upgrade in any Tier 1 environments. You can upgrade these yourself, follow the rest of this article below.

. You can contact them using an **Upgrade** request in Microsoft Dynamics Lifecycle Services (LCS), which you submit using the **Maintain** button on the **Environment details** page for the environment that you want to update.

This topic describes how to upgrade an older source database to the latest Finance and Operations update. To copy a database from a production environment back to a one-box demo or development environment, follow the steps in [Copy a Microsoft Dynamics 365 for Finance and Operations database from Azure SQL Database to a Microsoft SQL Server Environment](..\database\copy-database-from-azure-sql-to-sql-server.md). 

> [!IMPORTANT]
> This process does not apply to the upgrade of data in Management Reporter or the Retail channel database. It also does not apply to the upgrade of document attachments that are stored in Microsoft Azure blob storage.

## Before you begin
1.  You must have a functional one-box demo or development environment that is already successfully running with the latest Finance and Operations update.
2.  If you are upgrading from the Dynamics AX February 2016 release (also known as RTW) and upgrading to the May 2016 release, then the following hotfixes must be installed. These fixes must be installed in the destination environment. If you are upgrading to a newer version than the May 2016 release, you **do not** need these fixes, they are already included.
    -   Hotfix KB number 3170386, "Upgrade script error: ReleaseUpdateDB70\_DMF. updateIntegrationActivityExecutionMessageIdPreSync".
    -   Hotfix KB number 3180871, "Data upgrade from RTW to Update 1 causes errors when synchronizing views involving disabled configuration keys". This is a binary hotfix which will cause the database synchronize process to fail.

3.  In your source environment you must be install the appropriate fix below for your version. These fixes will correct a bug in the SysSetupLog logic so that the upgrade understands correctly which version you are upgrading from:
    - If upgrading from the February 2016 release (also known as RTW or 7.0) 7.0.1265.3015: Hotfix KB number 4023685 "Could not find source system version information" error when you upgrade to the latest Application Release 
    - If upgrading from the November 2016 release (also known as 1611 or 7.1) 7.1.1541.3036: Hotfix KB number 4023686 "Could not find source system version information" error when you upgrade to the latest Application Release 
    - If upgrading from the July 2017 release (also known as 7.2) 7.2.11792.56024: No additional fix is needed for this issue.

4.  If you're upgrading a database that began as a standard demo data database, you must also run the following script. This step is required because the demo data contains bad records for some kernel X++ classes.

> *delete from classidtable where id >= 0xf000 and id <= 0xffff*

## Download the MinorVersionDataUpgrade.zip script
To obtain the latest MinorVersionDataUpgrade.zip package from your target environment that is running the latest Finance and Operations update, download the latest binary updates from Lifecycle Services (LCS).
> [!NOTE]
> In earlier versions (prior to Platform update 4), the package was named DataUpgrade.zip. 

1.  In LCS, in the **Environments** section, click your target Finance and Operations environment, scroll to the bottom of the page, and then click the **All binary updates** tile. 

> [!NOTE]
> If the All binary updates tile shows zero updates available then use the MinorVersionDataUpgrade.zip from the latest platform update package available in the **Shared Asset Library** in LCS within the **Software deployable package** section. For example, if upgrading to Dynamics 365 for Operations version 1611 with platform update 3 and the **All binary updates** tile shows zero updates, then use the "D365 for Operations Platform Update 3" package from the shared asset library. When using this package from the shared asset library, the path required in step 3 below changes to ..\\AOSService\\Packages\\files\\dynamicsax-framework-bin.7.0.4307.16141.zip\\CustomDeployablePackage

2.  On the **Add hotfixes** page, click **Select all**, click **Add**, and then click **Download package**.
3.  On the next page, click **Download**.
4.  After the package is downloaded, extract the contents, and go to the following directory to find the MinorVersionDataUpgrade.zip file (note that the version number in the path will vary): ..\\AOSServiceDSC\\Packages\\files\\dynamicsax-framework-bin.7.0.4127.24083.zip\\CustomDeployablePackage

> [!NOTE]
> Computers that are deployed from LCS will already have a MinorVersionDataUpgrade.zip file. However, that file is out of date and includes issues that have been resolved in later fixes. Always download the latest version of the file from LCS.

## Remove encryption certification rotation
1.  Extract the MinorVersionDataUpgrade.zip deployable package to C:\\Temp or a location of your choice.
2.  Open the following file in a text editor: C:\\Temp\\DataUpgrade\\RotateConfigData\\ServicingRotations.json file. Modify the file as shown here, and save it. This step is required only for one-box environments. Because you're removing the need for encryption certificate rotations, old data in encrypted fields in your database will no longer be readable. This is a technical limitation for a one-box data upgrade. New data that goes into those fields after the upgrade is completed is unaffected. For details about the affected fields, see the ["Encrypted fields in demo data"](#encrypted-fields-in-demo-data) section later in this topic.

>       {
>             "AosService": {
>                              "EncryptionThumbprint": null,
>                              "SigningThumbprint": null,
>                              "Certificates": [
>                                               ],
>                               "CertificateThumbprints": [
>                                              ],
>                               "KeyValues": [
>                                              ]
>                           }
>        }

3.  Run the Windows PowerShell Integrated Scripting Environment (ISE) as an administrator.
4.  Open C:\\Temp\\DataUpgrade\\RotateConfigData\\Scripts\\EncryptRotationConfigData.ps1.
5.  Press F5 to run the script.

### Fix the duplicate key issue (February 2016 release only)

This step is required if you're upgrading a database from the February 2016 release (also known as RTW).

1.  Open the following file in a text editor: C:\\Temp\\DataUpgrade\\AOSService\\Scripts\\AutoDataUpgradePreReqs.ps1.
2.  Comment out or remove the following line.

>        Invoke-SQL -sqlCommand:$adjustsqlseq

3.  Save the file.

## Upgrade the database
1.  Install the deployable package from the C:\\Temp\\DataUpgrade folder (the location that you extracted to earlier). Use the instructions in [Install a deployable package](../deployment/install-deployable-package.md).
2.  Restore a backup of the source database to your one-box demo or development environment that is already running the latest Finance and Operations update that you want to upgrade to. **Note:** For better upload/download speed between Azure virtual machines (VMs), we recommend that you use AzCopy. For details about how to download and use AzCopy to copy to or from an Azure blob store, see [Transfer data with the AzCopy Command-Line Utility](https://azure.microsoft.com/en-us/documentation/articles/storage-use-azcopy/).
3.  Run the runbook file until Step 4: GlobalBackup.
4.  Rename the existing Update 1 database, and replace it with the source database that you want to upgrade.

        ALTER DATABASE <Update1_AX_DATABASENAME> MODIFY NAME = <Update1_AX_DATABASENAME>_ORIG
        ALTER DATABASE <Source_AX_DATABASENAME> MODIFY NAME = <Update1_AX_DATABASENAME>

5.  Create a backup of the source database, in case you need to revert to it, because the following steps will modify the source database.
6.  Mark step 4 of the runbook as completed, and continue to run the runbook until it's completed. 

**Notes:**
    -   The steps after step 4 of the runbook run the upgrade scripts.
    -   If there is data in any staging tables that is used by data management, this step fails, and you receive the following error message.

        > Staging tables should be empty in order to proceed with the data upgrade. Please run the DeleteScriptForStagingTables.sql by carefully reviewing the script in order to remove the data from the staging tables.

        In this case, run DeleteScriptForStagingTables.sql to clean up the staging tables. You can find this script under AOSServiceScripts in your data upgrade folder. After the script has finished running, re-run this step.

## Troubleshoot upgrade script errors
### How to re-run the runbook after a data upgrade script failure

A data upgrade deployable package allows more granular re-running than a typical deployable package. The step at which the data upgrade scripts begin executing is Step 5. If you experience a failure during Step 5, check the output in the command window to identify which sub-step you reached. For example it may be 5.3, the issue the command follows to re-run from that sub-step. This is to allow you to keep re-running a particular failing script during debugging, without having to re-run the entire data upgrade piece (including database synchronization).

    AXUpdateInstaller.exe execute -runbookid=upgrade -rerunstep=5.3

### How to view more detail about a script error

Upgrade scripts are running in X++ using a batch process that the runbook installer is starting. There are classes you can view in the Application Explorer in Visual Studio, they are prefixed with *ReleaseUpdate*. If an upgrade script fails during the runbook process you can discover more detail about the reason for the error by opening SQL Management Studio and querying the ReleaseUpdateScriptsErrorLog as follows.

    select \* from RELEASEUPDATESCRIPTSERRORLOG

It is possible to take that code, add it to a new runnable class in Visual Studio, and directly observe, debug, and rework it’s behavior.

### How to skip failed scripts

> [!IMPORTANT]
> This process is only designed to be used in a development scenario. 

Skipping failed scripts is an aid to the troubleshooting process and lets you skip all scripts that have failed a certain number of times and move to the next viable scripts. The process is intentionally very manual, to reduce the likelihood that you skip scripts without realizing that they were skipped. 

In the table **ReleaseUpdateConfiguration** there is a new field called **ScriptRetryCount**. The value in this field controls how many times the runbook process will re-run a script before it ignores it. When the runbook executes, the system updates the field ReleaseUpdateScriptsErrorLog.ErrorCount each time a specific script fails (creating a new row for each distinct script). 
In the DataUpgrade package folder, under ..\\AosServices\\Scripts\\ is a script named IgnoreBlockingScripts.ps1. Execute this from an Administrator PowerShell window to skip all scripts where the ScriptRetryCount=ErrorCount. 
Then re-run the failed runbook step so that scripts will be ignored. The field **ReleaseUpdateScriptsErrorLog.Ignored** will also be set for each skipped script so that they can be identified later.

### How to monitor duration of executed scripts

Each successfully executed script records the amount of time that it took to process (in minutes) in the **ReleaseUpdateScriptsLog.DurationMins** column. This is intended as a simple way to identify the longest running scripts when working on performance tuning the data upgrade process. It is important to understand that the timing is the duration each script takes to run, however multiple scripts will run in parallel, so the sum of the **DurationMins** column is greater than the overall duration of the upgrade process.

## Known issues
### Duplicate key was found for the object name 'dbo.RESOURCESETUP' 
When upgrading a database, you may experience the following error during the database synchronize phase of the runbook process.

> Database execution failed: The CREATE UNIQUE INDEX statement terminated because a duplicate key was found for the object name 'dbo.RESOURCESETUP' and the index name 'I_6716AK'


This is a known issue that will be resolved in a future hotfix. The workaround is to delete the duplicate rows from this table by executing the following SQL script against the database from SQL Server Management Studio.

    delete RS from ResourceSetup as RS
    join ResResourceIdentifier as RRI on RRI.RecId = RS.Resource_
    join WrkCtrTable as WCT on WCT.RecId = RRI.RefRecId
    join DirPartyTable as DPT on DPT.DataArea = WCT.DataAreaId
    where DPT.DataArea != '' and RS.LegalEntity != DPT.RecId


### Cannot select a record in Dimension hierarchy nodes (CAMDataDimensionHierarchyNode). 
When upgrading a database, you may experience the following error during the database synchronize phase of the runbook process.

>  Cannot select a record in Dimension hierarchy nodes (CAMDataDimensionHierarchyNode). Dimension hierarchy: 0. The SQL database has issued an error. Object Server DynamicsAXBatchManagement:  [Microsoft][ODBC Driver 13 for SQL Server][SQL Server]Invalid column name 'RELATIONTYPE'. 


This is a known issue that will be resolved in a future release. The workaround is to create a missing field in several tables by executing the following SQL script against the database from SQL Server Management Studio.

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
                PRINT @TABLENAME + ' table does not exists. Please provide a base table';
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

### Cannot create index on InventDistinctProduct

When upgrading a database, you may experience the following error during the database synchronize phase of the runbook process.

> Cannot create index on InventDistinctProduct a duplicate key exists on column Product.


This is a known issue that will be resolved in a future release. The workaround is to delete all records in the **InventDistinctProduct** table and then resume the runbook from the current step. The records contained in this table are disposable and will be regenerated either the first time Microsoft Dynamics 365 for Finance and Operations is launched, when an item is created, or when MRP is run. To drop all records in **InventDistinctProduct**, execute the following query against the current database from SQL Management Studio.

    truncate table InventDistinctProduct

To resume the runbook from the current operation, use the following command.

    axupdateinstaller execute -runbookid=<your runbook name> -rerunstep=<the last step number>

For example, you can use this command.

    axupdateinstaller execute -runbookid=dataupgrade -rerunstep=5.4

### An exchange rate cannot be found when upgrading demo data

When upgrading a demo database, you may receive the following error when deploying the DataUpgrade package.

> An exchange rate cannot be found for exchange rate type Default between currencies INR and BRL on exchange date 12/1/2014.

As you're upgrading demo data, look in table **TrvUnreconciledExpenseTransaction**, which is where the offending expense line is, and change the currency to USD (because it's demo data, we don't need to be careful to preserve this expense line).

    update TrvUnreconciledExpenseTransaction
    set transactioncurrencycode = 'USD'
    where transactioncurrencycode = 'INR'

Alternatively, you can go to the original environment the data came from (such as the old version) and add the missing exchange rate in **General Ledger** &gt; **Currencies** &gt; **Currency exchange rates**. You need to add a record for INR and BRL that covers 2014, then take that database and bring it into your new environment and start the upgrade against that database.

### Error: The interpreter evaluation stack has grown during a call to the kernel

This error can occur if you have enabled database logging on a kernel table such as UserInfo. The solution is to review the database log setup in **System administration** &gt; **Setup** &gt; **Database log setup** and remove records for kernel tables as necessary. The full error is as follows.

    Executing step: 5.1
    prereq for data upgrade
    prereq for data upgrade
    Unhandled exception More Information: The interpreter evaluation stack has grown during a call to the kernel method xRecord::Delete(), height before call: 0, height after call: 3. Unhandled exception More Information: KernelInstance: Kernel is accessing deleted memory
    The step failed

### The batch process fails to start

The batch process can fail if the environment has been left in [maintenance mode](../sysadmin/maintenance-mode.md) following a change to configuration keys. To resolve, turn maintenance mode off and resume the runbook process.

### The system fails to locate or generate a user GUID

You might receive the following error message.

> …Unhandled exception More Information: System failed to locate or generate a user GUID…

In this case, rerun the runbook step that failed. You will then be able to continue.

### Pre-sync or post-sync errors on ReleaseUpdateDB71\_LedgerPeriodClose

You might receive one of the following error messages on either preSyncLedgerPeriodCloseTemplateTask, updateMenuItemTypeForCurrencyReval, updateLedgerPeriodCloseTemplateTask methods in the ReleaseUpdateDB71\_LedgerPeriodClose class.

> Cannot execute the required database operation. The SQL database has issued an error. Object Server DynamicsAXBatchManagement: \[Microsoft\]\[SQL Server Native Client 11.0\]\[SQL Server\]Invalid column name 'TEMPLATE'. INSERT INTO LedgerPeriodCloseTemplateTaskTmp ( TEMPLATE, AREA, NAME, MENUITEM, MENUITEMTYPE, TARGETDAYSFROMPROJECTCOMPLETE, DUETIME, LEGALENTITYSELECTION, RECVERSION, PARTITION, RECID, CLOSINGROLE, LINENUM) SELECT T1.TEMPLATE, T1.AREA, T1.NAME, T1.MENUITEM, T1.MENUITEMTYPE, T1.TARGETDAYSFROMPROJECTCOMPLETE, T1.DUETIME, T1.LEGALENTITYSELECTION, T1.RECVERSION, T1.PARTITION, T1.RECID, T1.CLOSINGROLE, 0 FROM LedgerPeriodCloseTemplateTask T1 session 1013 (Admin) Microsoft.Dynamics.Ax.Xpp.ErrorException: Cannot execute the required database operation. The SQL database has issued an error.

> Cannot execute the required database operation. The SQL database has issued an error. Object Server DynamicsAXBatchManagement: \[Microsoft\]\[SQL Server Native Client 11.0\]\[SQL Server\]Invalid column name 'MENUITEMTYPE'. UPDATE LedgerPeriodCloseTemplateTaskTmp SET MENUITEMTYPE = 0 WHERE MENUITEMTYPE = 2 AND MENUITEM = 'LedgerExchAdj' AND PARTITION = 5637144576 session 1013 (Admin) Microsoft.Dynamics.Ax.Xpp.ErrorException: Cannot execute the required database operation. The SQL database has issued an error.

> Cannot execute the required database operation. The SQL database has issued an error. Object Server DynamicsAXBatchManagement: \[Microsoft\]\[SQL Server Native Client 11.0\]\[SQL Server\]Invalid column name 'TEMPLATE'. INSERT INTO LedgerPeriodCloseTemplateTask ( TEMPLATE, AREA, NAME, MENUITEM, MENUITEMTYPE, TARGETDAYSFROMPROJECTCOMPLETE, DUETIME, LEGALENTITYSELECTION, RECVERSION, PARTITION, RECID, CLOSINGROLE, LINENUM) SELECT T1.TEMPLATE, T1.AREA, T1.NAME, T1.MENUITEM, T1.MENUITEMTYPE, T1.TARGETDAYSFROMPROJECTCOMPLETE, T1.DUETIME, T1.LEGALENTITYSELECTION, T1.RECVERSION, T1.PARTITION, T1.RECID, T1.CLOSINGROLE, T1.LINENUM FROM LedgerPeriodCloseTemplateTaskTmp T1 session 1013 (Admin)

In this case, manually drop the table **LedgerPeriodCloseTemplateTaskTmp** from the database via SQL Management Studio, and then re-run the runbook step. This issue will be fixed in a future hotfix.

### KB number 3170386

If KB number 3170386 isn't installed, you will receive the following error message.

> *GlobalUpdate script for service model: AOSService on machine …. Etc …. UpgradeServiceHelper::WaitForDataUpgradeToComplete(Object\[\]… The step failed*

This error is caused by a failure in the pre-sync or the post-sync substep of the data upgrade. You can use the following steps to determine which substep failed and the details of the failure. **Note:** You can't rerun the failed runbook step until the pre-sync or post-sync substep has been manually completed and the AutoDataUpgrade.config file has been updated to skip the substeps that have already been run.

1.  In File Explorer, in the …DataUpgradeAosServiceScripts folder, sort by descending order of date modified, and then look at the file at the top of the list to determine which substep failed.
    -   If the top file is named dbUpgrade*PreSync*Monitor.error.log, the pre-sync substep failed.
    -   If the top file is named dbUpgrade*PostSync*Monitor.error.log, the post-sync substep failed.

2.  In Management Studio, run the following **SELECT** statement.

        SELECT * FROM RELEASEUPDATELOG

    The second-to-last record in the result set will have the errors and call stacks for all the failures.

### DMF errors

If you receive either of the following Data Migration Framework (DMF) errors, download Hotfix KB number 3170386, and restart the upgrade process.

#### DMF pre-sync

> Batch error: initial.DAT.ReleaseUpdateDB70\_DMF.updateIntegrationActivityExecutionMessageIdPreSync (Batch:AOS-F01B9F0CCC8, 9, Info, Error, ):\[\[1\]\[3,Cannot execute the required database operation. The SQL database has issued an error.\]\[3,Object Server DynamicsAXBatchManagement: \]\[3,\[Microsoft\]\[SQL Server Native Client 11.0\]\[SQL Server\]Incorrect syntax near 'GO'.\]\[3,

#### DMF post-sync

> Batch error: initial.DAT.ReleaseUpdateDB70\_DMF.updateIntegrationActivityExecutionMessageIdPostSync (Batch:AOS-F01B9F0CCC8, 9, Info, Error, ):\[\[1\]\[3,Cannot execute the required database operation.The SQL database has issued an error.\]\[3,Object Server DynamicsAXBatchManagement: \]\[3,\[Microsoft\]\[SQL Server Native Client 11.0\]\[SQL Server\]Incorrect syntax near 'GO'.\]\[3,

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



See also
--------

[Overview of moving to the latest update of Microsoft Dynamics 365 for Finance and Operations](upgrade-latest-update.md)



