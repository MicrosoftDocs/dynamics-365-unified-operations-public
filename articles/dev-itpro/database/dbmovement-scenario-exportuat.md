---
# required metadata

title: Exporting a copy of the Standard User Acceptance Test (UAT) database
description: This topic explains a database export scenario for Microsoft Dynamics 365 for Finance and Operations.
author: LaneSwenka
manager: AnnBe
ms.date: 01/28/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: IT Pro, Developer
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.search.region: Global
# ms.search.industry: 
ms.author: laneswenka
ms.search.validFrom: 2019-01-31
ms.dyn365.ops.version: 8.1.3

---

# Exporting a copy of the Standard User Acceptance Test (UAT) database

[!include [banner](../includes/banner.md)]

Database movement operations are a suite of self-service actions that can be used as part of data application lifecycle management (DataALM). This tutorial shows how to export all of the data and transactions from a sandbox Standard User Acceptance Test (UAT) environment.

In this tutorial, you will learn how to:

> [!div class="checklist"]
> * Refresh the user acceptance testing (UAT) environment.
> * Run the export to the Asset Library in Microsoft Dynamics Lifecycle Services (LCS).
> * Download the database backup.
> * Import the database and prepare it so that it can be used in a developer environment.

As an example of this scenario, a customer who has already gone live with Microsoft Dynamics 365 for Finance and Operations wants to load a recent copy of production transactions into his or her development environment. In this way, the customer will be able to debug specific transactions or develop new features and reports by using realistic datasets.

## Known limitations
Due to recent restrictions by the Azure SQL platform, it is not recommended to export your database if it is larger than 200GB.  If you must do this, the recommended option is to use the [legacy documentation](https://github.com/MicrosoftDocs/dynamics-365-unified-operations-public/blob/b86878500e79f0fe0488c9aedf3fd38b30749fd4/articles/dev-itpro/database/copy-database-from-azure-sql-to-sql-server.md) until Azure SQL can support larger exports.  Note that this recommendation is for Export, and not for Refresh which can support databases up to 4TB in size.

## Prerequisites

To do a refresh operation, you must have your production environment deployed, or you must have a minimum of two standard UAT environments. To complete this tutorial, you must have a developer environment deployed.

## Refresh the UAT environment

This refresh operation will overwrite the UAT environment with the latest copy of the production database. To complete this step, follow the instructions in [Refresh for training purposes](dbmovement-scenario-general-refresh.md).

## Back up to the Asset Library

[!include [dbmovement-export](../includes/dbmovement-export.md)]

## Import the database

After you've downloaded a database backup (.bacpac) file, you can begin the manual import operation on your Tier 1 environment. When you import the database, we recommend that you follow these guidelines:

- Keep a copy of the existing AxDB database, so that you can revert to it later if required.
- Import the new database under a new name, such as **AxDB\_fromProd**.

To help guarantee the best performance, copy the \*.bacpac file to the local computer that you're importing from. Open a **Command Prompt** window, and run the following commands.

```
cd C:\Program Files (x86)\Microsoft SQL Server\140\DAC\bin

SqlPackage.exe /a:import /sf:D:\Exportedbacpac\my.bacpac /tsn:localhost /tdn:<target database name> /p:CommandTimeout=1200
```

Here is an explanation of the parameters:

- **tsn (target server name)** – The name of the Microsoft SQL Server instance to import into.
- **tdn (target database name)** – The name of the database to import into. The database should **not** already exist.
- **sf (source file)** – The path and name of the file to import from.

> [!NOTE]
> During import, the user name and password aren't required. By default, SQL Server uses Microsoft Windows authentication for the user who is currently signed in.

## Update the database

Run the following SQL script against the imported database. This script adds back the users that you deleted from the source database and correctly links them to the SQL logins for this SQL instance. The script also turns change tracking back on. Remember to edit the final **ALTER DATABASE** statement so that it uses the name of your database.

```
CREATE USER axdeployuser FROM LOGIN axdeployuser
EXEC sp_addrolemember 'db_owner', 'axdeployuser'

CREATE USER axdbadmin FROM LOGIN axdbadmin
EXEC sp_addrolemember 'db_owner', 'axdbadmin'

CREATE USER axmrruntimeuser FROM LOGIN axmrruntimeuser
EXEC sp_addrolemember 'db_datareader', 'axmrruntimeuser'
EXEC sp_addrolemember 'db_datawriter', 'axmrruntimeuser'

CREATE USER axretaildatasyncuser FROM LOGIN axretaildatasyncuser
EXEC sp_addrolemember 'DataSyncUsersRole', 'axretaildatasyncuser'

CREATE USER axretailruntimeuser FROM LOGIN axretailruntimeuser
EXEC sp_addrolemember 'UsersRole', 'axretailruntimeuser'
EXEC sp_addrolemember 'ReportUsersRole', 'axretailruntimeuser'

CREATE USER axdeployextuser FROM LOGIN axdeployextuser
EXEC sp_addrolemember 'DeployExtensibilityRole', 'axdeployextuser'

CREATE USER [NT AUTHORITY\NETWORK SERVICE] FROM LOGIN [NT AUTHORITY\NETWORK SERVICE]
EXEC sp_addrolemember 'db_owner', 'NT AUTHORITY\NETWORK SERVICE'

UPDATE T1
SET T1.storageproviderid = 0
    , T1.accessinformation = ''
    , T1.modifiedby = 'Admin'
    , T1.modifieddatetime = getdate()
FROM docuvalue T1
WHERE T1.storageproviderid = 1 --Azure storage

DROP PROCEDURE IF EXISTS SP_ConfigureTablesForChangeTracking
DROP PROCEDURE IF EXISTS SP_ConfigureTablesForChangeTracking_V2
GO
-- Begin Refresh Retail FullText Catalogs
DECLARE @RFTXNAME NVARCHAR(MAX);
DECLARE @RFTXSQL NVARCHAR(MAX);
DECLARE retail_ftx CURSOR FOR
SELECT OBJECT_SCHEMA_NAME(object_id) + '.' + OBJECT_NAME(object_id) fullname FROM SYS.FULLTEXT_INDEXES
    WHERE FULLTEXT_CATALOG_ID = (SELECT TOP 1 FULLTEXT_CATALOG_ID FROM SYS.FULLTEXT_CATALOGS WHERE NAME = 'COMMERCEFULLTEXTCATALOG');
OPEN retail_ftx;
FETCH NEXT FROM retail_ftx INTO @RFTXNAME;

BEGIN TRY
    WHILE @@FETCH_STATUS = 0 
    BEGIN 
        PRINT 'Refreshing Full Text Index ' + @RFTXNAME;
        EXEC SP_FULLTEXT_TABLE @RFTXNAME, 'activate';
        SET @RFTXSQL = 'ALTER FULLTEXT INDEX ON ' + @RFTXNAME + ' START FULL POPULATION';
        EXEC SP_EXECUTESQL @RFTXSQL;
        FETCH NEXT FROM retail_ftx INTO @RFTXNAME;
    END
END TRY
BEGIN CATCH
    PRINT error_message()
END CATCH

CLOSE retail_ftx; 
DEALLOCATE retail_ftx; 
-- End Refresh Retail FullText Catalogs
```

### Turn on change tracking

If change tracking was turned on in the source database, be sure to turn it on in the newly provisioned database in the target environment by using the **ALTER DATABASE** command.

```
ALTER DATABASE [your database name] SET CHANGE_TRACKING = ON (CHANGE_RETENTION = 6 DAYS, AUTO_CLEANUP = ON);
```

To help guarantee that the current version of the store procedure that is related to change tracking is used in the new database, you must turn change tracking on or off for a data entity in data management. You can choose any entity. This step is required to trigger the refresh of the store procedure.

## Start to use the new database

To switch environments and use the new database, first stop the following services:

- World Wide Web Publishing Service
- Microsoft Dynamics 365 Unified Operations: Batch Management Service
- Management Reporter 2012 Process Service

After these services have been stopped, rename the AxDB database **AxDB\_orig**, rename your newly imported database **AxDB**, and then restart the three services.

To switch back to the original database, reverse this process. In other words, stop the services, rename the databases, and then restart the services.

### Reprovision the target environment

[!include [environment-reprovision](../includes/environment-reprovision.md)]

### Reset the Financial Reporting database

If you're using Financial Reporting, you must reset the Financial Reporting database by following the steps in [Resetting the financial reporting data mart after restoring a database](../analytics/reset-financial-reporting-datamart-after-restore.md). (Financial Reporting was previously named Management Reporter.)

## Reenter data from encrypted and environment-specific fields in the target database

In the Finance and Operations client, enter the values that you documented for the encrypted and environment-specific fields. The following fields are affected. The field names are given in *Table.Field* format.

| Field name                                               | Where to set the value |
|----------------------------------------------------------|------------------------|
| CreditCardAccountSetup.SecureMerchantProperties          | Select **Accounts receivable** &gt; **Payments setup** &gt; **Payment services**. |
| ExchangeRateProviderConfigurationDetails.Value           | Select **General ledger** &gt; **Currencies** &gt; **Configure exchange rate providers**. |
| FiscalEstablishment\_BR.ConsumerEFDocCsc                 | Select **Organization administration** &gt; **Fiscal establishments** &gt; **Fiscal establishments**. |
| FiscalEstablishmentStaging.CSC                           | This field is used by the Data Import/Export Framework (DIXF). |
| HcmPersonIdentificationNumber.PersonIdentificationNumber | Select **Human resources** &gt; **Workers** &gt; **Workers**. On the **Worker** tab, in the **Personal information** group, select **Identification numbers**. |
| HcmWorkerActionHire.PersonIdentificationNumber           | This field has been obsolete since Microsoft Dynamics AX 7.0 (February 2016). It was previously in the **All worker actions** form (**Human resources** &gt; **Workers** &gt; **Actions** &gt; **All worker actions**). |
| SysEmailSMTPPassword.Password                            | Select **System administration** &gt; **Email** &gt; **Email parameters**. |
| SysOAuthUserTokens.EncryptedAccessToken                  | This field is used internally by Application Object Server (AOS). It can be ignored. |
| SysOAuthUserTokens.EncryptedRefreshToken                 | This field is used internally by AOS. It can be ignored. |

## Community tools

Are you looking for more tools to help with importing backup files to your developer environments? Here are some other sources of information:

* [D365fo.Tools](https://github.com/d365collaborative/d365fo.tools/blob/development/docs/Import-D365Bacpac.md) provides many valuable tools that have been created by the community.
* [Community provided open source projects on GitHub](https://github.com/search?q=dynamics+365+finance+operations&s=stars).

## Known issues

### Export database is in 'Preparation failed' state.
This happens when the automation from Lifecycle Services hits a timeout.  The export operation is still executing in Azure SQL to the Asset Library.  You can use the **Resume** button to reconnect the process with Azure SQL and it will complete successfully.

### Export database is taking a very long time.
Azure SQL has recently announced that the Import/Export API used by Lifecycle Services has variable execution times for any database that is over 200GB in size.  If you face this problem, you can either decide to [connect your DevTest environment directly to the UAT database](dbmovement-scenario-debugdiag.md) or you can follow the [legacy documentation](https://github.com/MicrosoftDocs/dynamics-365-unified-operations-public/blob/b86878500e79f0fe0488c9aedf3fd38b30749fd4/articles/dev-itpro/database/copy-database-from-azure-sql-to-sql-server.md).  Exporting databases for backup purposes is not recommended as Point-in-time restore functionality is available and included with your environment.

The Lifecycle Services team is working directly with the Azure SQL team to increase the performance of this Export API, and will make improvements in upcoming releases of LCS.

### I can't download Management Studio installation files

When you try to download the Microsoft SQL Server Management Studio installer, you might receive the following error message:

> Your current security settings do not allow this file to be downloaded.

To work around this issue, follow these steps to enable file downloads.

1. In your web browser, open **Internet options**.
2. On the **Security** tab, select the **Internet** zone, and then select **Custom level**.
3. Scroll to **Downloads**, and then, under **File download**, select the **Enable** option.

### Database synchronization fails

When you sync the database against the newly imported database from Microsoft Visual Studio, the synchronization might fail, and you might receive the following error message:

> Failed to open SQL connection syncengine.exe exited with code -1.

In this case, the following message is also logged under event ID 140 in the Windows application log:

> Object Server Database Synchronizer: The internal system table version number stored in the database is higher than the version supported by the kernel (141/138). Use a newer Microsoft Dynamics kernel, or start Microsoft Dynamics using the -REPAIR command line parameter to enforce synchronization.

This issue can occur when the platform build number of the current environment is lower than the platform build number of the source environment. Depending on your circumstances, either use the **Updates** tiles on the environment page in LCS to upgrade the platform in the current environment so that it matches the platform in the source environment, or run the following query to adjust the expected version in the database.

```
UPDATE SQLSYSTEMVARIABLES

SET VALUE = 138

WHERE PARM = 'SYSTABVERSION'
```

> [!NOTE]
> The value **138** in the preceding query is taken from the event log message, where version 138 was expected in this particular environment.

### Performance

The following guidelines can help you achieve optimal performance:

- Always import the .bacpac file locally on the computer that runs the SQL Server instance. Don't import it from Management Studio on a remote machine.
- In a Finance and Operations one-box environment that is hosted in Microsoft Azure, put the .bacpac file on drive D when you import it. (A one-box environment is also known as a Tier 1 environment.) For more information about the temporary drive on Azure virtual machines (VMs), see the [Understanding the temporary drive on Windows Azure Virtual Machines](https://blogs.msdn.microsoft.com/mast/2013/12/06/understanding-the-temporary-drive-on-windows-azure-virtual-machines/) blog post.
- Grant the account that runs the SQL Server Windows service [Instance File Initialization](https://msdn.microsoft.com/library/ms175935.aspx) rights. In this way, you can help improve the speed of the import process and the speed of a restore from a \*.bak file. For a developer environment, you can easily make sure that the account that runs the SQL Server service has these rights by setting SQL Server to run as the axlocaladmin account.
