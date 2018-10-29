---
# required metadata

title: Copy Finance and Operations databases from Azure SQL Database to SQL Server environments
description: This topic explains how to move a Microsoft Dynamics 365 for Finance and Operations database from an Azure-based environment to a SQL Server–based environment.
author: laneswenka
manager: AnnBe
ms.date: 10/29/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.custom: 203764
ms.assetid: 45efdabf-1714-4ba4-9a9d-217143a6c6e0
ms.search.region: Global
# ms.search.industry: 
ms.author: laswenka
ms.search.validFrom: 2016-05-31
ms.dyn365.ops.version: AX 7.0.1

---

# Copy Finance and Operations databases from Azure SQL Database to SQL Server environments

[!include [banner](../includes/banner.md)]

This topic explains how to export a Microsoft Dynamics 365 for Finance and Operations database from an environment that is based on Microsoft Azure and import it into an environment that is based on Microsoft SQL Server.

## Overview

To move a database, you use the sqlpackage.exe command-line tool to export the database from Azure SQL Database and then import it into Microsoft SQL Server 2016. Because the file name extension for the exported data is .bacpac, this process is often referred to as the *bacpac process*.

The high-level process for a database move includes the following phases:

1. Create a duplicate of the source database.
2. Run a SQL script to prepare the database.
3. Export the database from the Azure SQL database.
4. Import the database into SQL Server 2016.
5. Run a SQL script to update the database.

## Prerequisites

The following prerequisites must be met before you can move a database:

- The source environment (that is, the environment that is connected to the source database) must run a version of the Finance and Operations platform that is earlier than or the same as the version of the platform that the destination environment runs.
- Only a database that the customer has SQL access to can be copied. If you must copy the production environment, you must first copy that environment to the sandbox environment. Then work from the sandbox environment.

    > [!NOTE]
    > In this article, we use the term *sandbox* to refer to a Standard or Premier Acceptance Testing (Tier 2/3) or higher environment connected to a SQL Azure database.

- The destination SQL Server environment must run SQL Server 2016 Release to Manufacturing (RTM) (13.00.1601.5) or later. The Community Technology Preview (CTP) versions of SQL Server 2016 might cause errors during the import process.

    > [!IMPORTANT] 
    > To export a database from a sandbox environment, you must be running the same version of SQL Server Management Studio (SSMS) that is in the environment you will be importing the database to. This may require you to install the [latest version of SQL Server Management Studio](https://msdn.microsoft.com/en-us/library/mt238290.aspx) on the VM that runs Application Object Server (AOS) in the sandbox environment. Do the bacpac export on that AOS computer. There are two reasons for this requirement:
    > 
    > - Because of an Internet Protocol (IP) access restriction on the sandbox instance of SQL Server, only computers in that environment can connect to the instance.
    > - The exported \*.bacpac file may be dependent on version specific features of Management Studio. Make sure the SSMS version that you use to export the database **is not newer** than the SSMS version (on the target environment) that you will be using to import the bacpac.

## Before you begin

Encrypted and environment-specific values can't be imported into a new environment. After you've completed the import, you must re-enter some data from your source environment in your target environment.

### Document the values of encrypted fields

Because of a technical limitation that is related to the certificate that is used for data encryption, values that are stored in encrypted fields in a database will be unreadable after that database is imported into a new environment. Therefore, after an import, you must manually delete and re-enter values that are stored in encrypted fields. New values that are entered in encrypted fields after an import will be readable. The following fields are affected. The field names are given in Table.Field format.

| Field name                                               | Where to set the value |
|----------------------------------------------------------|------------------------|
| CreditCardAccountSetup.SecureMerchantProperties          | Select **Accounts receivable** &gt; **Payments setup** &gt; **Payment services**. |
| ExchangeRateProviderConfigurationDetails.Value           | Select **General ledger** &gt; **Currencies** &gt; **Configure exchange rate providers**. |
| FiscalEstablishment\_BR.ConsumerEFDocCsc                 | Select **Organization administration** &gt; **Fiscal establishments** &gt; **Fiscal establishments**. |
| FiscalEstablishmentStaging.CSC                           | This field is used by the Data Import/Export Framework (DIXF). |
| HcmPersonIdentificationNumber.PersonIdentificationNumber | Select **Human resources** &gt; **Workers** &gt; **Workers**. On the **Worker** tab, in the **Personal information** group, select **Identification numbers**. |
| HcmWorkerActionHire.PersonIdentificationNumber           | This field has been obsolete since Microsoft Dynamics AX 7.0 (February 2016). It was previously in the **All worker actions** form (**Human resources** &gt; **Workers** &gt; **Actions** &gt; **All worker actions**). |
| SysEmailSMTPPassword.Password                            | Select **System administration** &gt; **Email** &gt; **Email parameters**. |
| SysOAuthUserTokens.EncryptedAccessToken                  | This field is used internally by AOS. It can be ignored. |
| SysOAuthUserTokens.EncryptedRefreshToken                 | This field is used internally by AOS. It can be ignored. |

### If you're running Retail components, document encrypted and environment-specific values

The values on the following pages are either environment-specific or encrypted in the database. Therefore, all the imported values will be incorrect.

- Payments services (**Accounts receivable** &gt; **Payments setup** &gt; **Payments services**)
- Hardware profiles (**Retail and commerce** &gt; **Channel setup** &gt; **POS setup** &gt; **POS profiles** &gt; **Hardware profiles**)

## Create a copy of the source database

Because you must turn off change tracking and delete database users before you can export the source Azure SQL database, you should create a copy of that database. You can then work with the copy instead of deleting information from the original database. The following SQL statement creates a copy of the axdb\_mySourceDatabaseToCopy database and names it **MyNewCopy**. Edit this script so that it uses the names of your databases.

```
CREATE DATABASE MyNewCopy AS COPY OF axdb_mySourceDatabaseToCopy
```

This SQL statement runs asynchronously. In other words, although it appears to be completed after one minute, it actually continues to run in the background. For more information, see [CREATE DATABASE (Azure SQL Database)](https://msdn.microsoft.com/en-us/library/dn268335.aspx). To monitor the progress of the copy operation, run the following query against the MASTER database in the same instance.

```
SELECT * FROM sys.dm_database_copies
```

> [!WARNING] 
> Retaining copies of the database for an extended period is not allowed in any Finance and Operations environment. Microsoft reserves the right to delete any copies of the database older than 7 days without any prior notice.

## Prepare the database

Run the following script against the copy of the database to turn off change tracking, and to remove SQL Database users and a system view. The script also corrects system flags, removes references to the previous environment, withholds batches, and removes email configuration. All these changes are required for a successful export and import of the database. These changes also help guarantee that, when the AOS computer is started in the target environment, nothing automatically starts to run.

> [!NOTE]
> You must edit the following **ALTER DATABASE** command so that it uses the name of your database copy.

```
--Prepare a database in Azure SQL ddatabase for export to SQL Server.

--Remove certificates in database from Electronic Signature usage
DECLARE @SQL nvarchar(512)
DECLARE certCursor CURSOR for
select 'DROP CERTIFICATE ' + QUOTENAME(c.name) + ';'
from sys.certificates c;
OPEN certCursor;
FETCH certCursor into @SQL;
WHILE @@Fetch_Status = 0
BEGIN
print @SQL;
exec(@SQL);
FETCH certCursor into @SQL;
END;
CLOSE certCursor;
DEALLOCATE certCursor;


-- Re-assign full rext catalogs to [dbo]
BEGIN
    DECLARE @catalogName nvarchar(256);
    DECLARE @sqlStmtTable nvarchar(512)

    DECLARE reassignFullTextCatalogCursor CURSOR
       FOR SELECT DISTINCT name
       FROM sys.fulltext_catalogs 
       
       -- Open cursor and disable on all tables returned
       OPEN reassignFullTextCatalogCursor
       FETCH NEXT FROM reassignFullTextCatalogCursor INTO @catalogName

       WHILE @@FETCH_STATUS = 0
       BEGIN
              SET @sqlStmtTable = 'ALTER AUTHORIZATION ON Fulltext Catalog::[' + @catalogName + '] TO [dbo]'
              EXEC sp_executesql @sqlStmtTable
              FETCH NEXT FROM reassignFullTextCatalogCursor INTO @catalogName
       END
       CLOSE reassignFullTextCatalogCursor
       DEALLOCATE reassignFullTextCatalogCursor
END

--Disable change tracking on tables where it is enabled.
declare
@SQL varchar(1000)
set quoted_identifier off
declare changeTrackingCursor CURSOR for
select 'ALTER TABLE [' + t.name + '] DISABLE CHANGE_TRACKING'
from sys.change_tracking_tables c, sys.tables t
where t.object_id = c.object_id
OPEN changeTrackingCursor
FETCH changeTrackingCursor into @SQL
WHILE @@Fetch_Status = 0
BEGIN
exec(@SQL)
FETCH changeTrackingCursor into @SQL
END
CLOSE changeTrackingCursor
DEALLOCATE changeTrackingCursor

--Disable change tracking on the database itself.
ALTER DATABASE
-- SET THE NAME OF YOUR DATABASE BELOW
MyNewCopy
set CHANGE_TRACKING = OFF
--Remove the database level users from the database
--these will be recreated after importing in SQL Server.
declare
@userSQL varchar(1000)
set quoted_identifier off
declare userCursor CURSOR for
select 'DROP USER [' + name + ']'
from sys.sysusers
where issqlrole = 0 and hasdbaccess = 1 and name <> 'dbo'
OPEN userCursor
FETCH userCursor into @userSQL
WHILE @@Fetch_Status = 0
BEGIN
exec(@userSQL)
FETCH userCursor into @userSQL
END
CLOSE userCursor
DEALLOCATE userCursor
--Delete the SYSSQLRESOURCESTATSVIEW view as it has an Azure-specific definition in it.
--We will run db synch later to recreate the correct view for SQL Server.
if(1=(select 1 from sys.views where name = 'SYSSQLRESOURCESTATSVIEW'))
DROP VIEW SYSSQLRESOURCESTATSVIEW
--Next, set system parameters ready for being a SQL Server Database.
update sysglobalconfiguration
set value = 'SQLSERVER'
where name = 'BACKENDDB'
update sysglobalconfiguration
set value = 0
where name = 'TEMPTABLEINAXDB'
--Clean up the batch server configuration, server sessions, and printers from the previous environment.
TRUNCATE TABLE SYSSERVERCONFIG
TRUNCATE TABLE SYSSERVERSESSIONS
TRUNCATE TABLE SYSCORPNETPRINTERS
TRUNCATE TABLE SYSCLIENTSESSIONS
TRUNCATE TABLE BATCHSERVERCONFIG
TRUNCATE TABLE BATCHSERVERGROUP
--Remove records which could lead to accidentally sending an email externally.
UPDATE SysEmailParameters
SET SMTPRELAYSERVERNAME = '', MAILERNONINTERACTIVE = 'SMTP' --LANE.SWENKA 9/12/18 Forcing SMTP as Exchange provider can still email on refresh
--Remove encrypted SMTP Password record(s)
TRUNCATE TABLE SYSEMAILSMTPPASSWORD
GO
UPDATE LogisticsElectronicAddress
SET LOCATOR = ''
WHERE Locator LIKE '%@%'
GO
TRUNCATE TABLE PrintMgmtSettings
TRUNCATE TABLE PrintMgmtDocInstance
--Set any waiting, executing, ready, or canceling batches to withhold.
UPDATE BatchJob
SET STATUS = 0
WHERE STATUS IN (1,2,5,7)
GO
-- Clear encrypted hardware profile merchand properties
update dbo.RETAILHARDWAREPROFILE set SECUREMERCHANTPROPERTIES = null where SECUREMERCHANTPROPERTIES is not null
```

## Export the database

Open a **Command Prompt** window and run the following commands.

```
cd C:\Program Files (x86)\Microsoft SQL Server\140\DAC\bin

SqlPackage.exe /a:export /ssn:<server>.database.windows.net /sdn:<database to export> /tf:D:\Exportedbacpac\my.bacpac /p:CommandTimeout=1200 /p:VerifyFullTextDocumentTypesSupported=false /sp:<SQL password> /su:<sql user>
```

Here is an explanation of the parameters:

- **ssn (source server name)** – The name of the Azure SQL Database server to export from.
- **sdn (source database name)** – The name of the database to export.
- **tf (target file)** – The path and name of the file to export to.
- **sp (source password)** – The SQL password for the source SQL Server.
- **su (source user)** – The SQL user name for the source SQL Server. We recommend that you use the **sqladmin** user. This user is created on every Finance and Operations SQL instance during deployment. You can retrieve the password for this user from your project in Microsoft Dynamics Lifecycle Services (LCS).

After the export is completed, run the following command to delete the database copy.

```
DROP DATABASE [MyNewCopy]
```

## Import the database

When you import the database, we recommend that you follow these guidelines:

- Retain a copy of the existing AxDB database, so that you can revert to it later if you must.
- Import the new database under a new name, such as **AxDB\_fromProd**.

To help guarantee the best performance, copy the \*.bacpac file to the local computer that you're importing from. Open a **Command Prompt** window and run the following commands.

```
cd C:\Program Files (x86)\Microsoft SQL Server\140\DAC\bin

SqlPackage.exe /a:import /sf:D:\Exportedbacpac\my.bacpac /tsn:localhost /tdn:<target database name> /p:CommandTimeout=1200
```

Here is an explanation of the parameters:

- **tsn (target server name)** – The name of the SQL Server to import into.
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

ALTER DATABASE [<your AX database name>] SET CHANGE_TRACKING = ON (CHANGE_RETENTION = 6 DAYS, AUTO_CLEANUP = ON)
GO
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

### Enable change tracking
If change tracking was enabled in the source database, ensure to enable change tracking again in the newly provisioned database in the target environment using the ALTER DATABASE command.

To ensure current version of the store procedure (related to change tracking) is used in the new database, you must enable/disable change tracking for a data entity in data management. This can be done on any entity as this is needed to trigger the refresh of store procedure.

### Re-provision the target environment

[!include [environment-reprovision](../includes/environment-reprovision.md)]

### Reset the Financial Reporting database

If you're using Financial Reporting, which was previously named Management Reporter, you must reset the Financial Reporting database by following the steps in [Resetting the financial reporting data mart after restoring a database](../analytics/reset-financial-reporting-datamart-after-restore.md).

## Start to use the new database

To switch the environment and use the new database, first stop the following services:

- World Wide Web Publishing Service
- Microsoft Dynamics 365 Unified Operations: Batch Management Service
- Management Reporter 2012 Process Service

After the services have been stopped, rename the AxDB database **AxDB\_orig**, rename your newly imported database **AxDB**, and then restart the three services.

To switch back to the original database, reverse this process. In other words, stop the services, rename the databases, and then restart the services.

## Re-enter data from encrypted and environment-specific fields in the target database

In the Finance and Operations client, enter the values that you documented for the encrypted and environment-specific fields. The following fields are affected. The field names are given in Table.Field format.

| Field name                                               | Where to set the value |
|----------------------------------------------------------|------------------------|
| CreditCardAccountSetup.SecureMerchantProperties          | Select **Accounts receivable** &gt; **Payments setup** &gt; **Payment services**. |
| ExchangeRateProviderConfigurationDetails.Value           | Select **General ledger** &gt; **Currencies** &gt; **Configure exchange rate providers**. |
| FiscalEstablishment\_BR.ConsumerEFDocCsc                 | Select **Organization administration** &gt; **Fiscal establishments** &gt; **Fiscal establishments**. |
| FiscalEstablishmentStaging.CSC                           | This field is used by DIXF. |
| HcmPersonIdentificationNumber.PersonIdentificationNumber | Select **Human resources** &gt; **Workers** &gt; **Workers**. On the **Worker** tab, in the **Personal information** group, select **Identification numbers**. |
| HcmWorkerActionHire.PersonIdentificationNumber           | This field has been obsolete since AX 7.0 (February 2016). It was previously in the **All worker actions** form (**Human resources** &gt; **Workers** &gt; **Actions** &gt; **All worker actions**). |
| SysEmailSMTPPassword.Password                            | Select **System administration** &gt; **Email** &gt; **Email parameters**. |
| SysOAuthUserTokens.EncryptedAccessToken                  | This field is used internally by AOS. It can be ignored. |
| SysOAuthUserTokens.EncryptedRefreshToken                 | This field is used internally by AOS. It can be ignored. |

## Known issues

### I can't download Management Studio installation files

When you try to download the Management Studio installer, you might receive the following error message:

> Your current security settings do not allow this file to be downloaded.

To work around this issue, follow these steps to enable file downloads.

1. In your web browser, open **Internet options**.
2. On the **Security** tab, select the **Internet** zone, and then select **Custom level**.
3. Scroll to **Downloads**, and then, under **File download**, select the **Enable** option.

### Database synchronization fails

When you synchronize the database against the newly imported database from Microsoft Visual Studio, the synchronization might fail, and you might receive the following error message:

> Failed to open SQL connection syncengine.exe exited with code -1.

In this case, the following message is also logged under event ID 140 in the Windows application log:

> Object Server Database Synchronizer: The internal system table version number stored in the database is higher than the version supported by the kernel (141/138). Use a newer Microsoft Dynamics kernel, or start Microsoft Dynamics using the -REPAIR command line parameter to enforce synchronization.

This issue can occur when the platform build number of the current environment is lower than the platform build number of the source environment. Depending on your circumstances, either use the **Updates** tiles on the LCS **Environment** page to upgrade the platform in the current environment so that it matches the platform in the source environment, or run the following query to adjust the expected version in the database.

```
UPDATE SQLSYSTEMVARIABLES

SET VALUE = 138

WHERE PARM = 'SYSTABVERSION'
```

> [!NOTE]
> The value **138** in the preceding query is taken from the event log message, where version 138 was expected in this particular environment.

### Performance

The following guidelines can help you achieve optimal performance:

- Always export a database from a virtual machine (VM) that is in the same Azure datacenter as the Azure SQL database. If you're exporting a copy of your sandbox database, export it from the sandbox AOS computer.
- Always import the .bacpac file locally on the computer that runs the SQL Server instance. Don't import it from Management Studio on a remote machine.
- In a Finance and Operations one-box environment that is hosted in Azure, put the .bacpac file on drive D when you import it. (A one-box environment is also known as a Tier 1 environment.) For more information about the temporary drive on Azure VMs, see the [Understanding the temporary drive on Windows Azure Virtual Machines](https://blogs.msdn.microsoft.com/mast/2013/12/06/understanding-the-temporary-drive-on-windows-azure-virtual-machines/) blog post.
- Grant the account that runs the SQL Server Windows service [Instance File Initialization](https://msdn.microsoft.com/en-us/library/ms175935.aspx) rights. In this way, you can help improve the speed of the import process and the speed of a restore from a \*.bak file. For a developer environment, you can easily make sure that the account that runs the SQL Server service has these rights by setting SQL Server to run as the axlocaladmin account.
- From Azure SQL Database, don't select **Export data tier application in Management Studio**, because there can be a memory limitation for larger databases.
