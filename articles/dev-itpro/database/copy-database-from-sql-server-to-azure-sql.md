---
# required metadata

title: Copy a Finance and Operations database – SQL Server to production Azure SQL
description: This topic describes how to move a Finance and Operations database from an environment that runs on SQL Server (Tier 1 or one-box) to an environment that runs on an Azure SQL database (Tier 2 or higher). 
author: tariqbell
manager: AnnBe
ms.date: 08/21/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
ms.reviewer: margoc
ms.search.scope: Operations, UnifiedOperations
# ms.tgt_pltfrm: 
ms.custom: 256464
ms.assetid: 4cc5f2aa-dd4e-4981-9607-e75fd1d57941
ms.search.region: Global
# ms.search.industry: 
ms.author: tabell
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611

---

# Copy a Finance and Operations database from SQL Server to a production Azure SQL Database environment

[!include[banner](../includes/banner.md)]

This topic describes how to move a Microsoft Dynamics 365 for Finance and Operations, Enterprise edition, database from an environment that runs on Microsoft SQL Server (that is, a Tier 1 or one-box environment) to an environment that runs on a Microsoft Azure SQL database (a Tier 2 or higher environment). 

This process is typically performed before go-live to bring a golden (or seed) database that contains only system configuration data into a production environment. This process isn't suitable for all situations. For example, you should not use this process to import data for a new legal entity for an existing live deployment. In those situations, we recommend that you use [process data packages](../lcs-solutions/process-data-packages-lcs-solutions.md) or [data entity data packages](../data-entities/data-entities-data-packages.md). Here is the supported procedure for bringing a golden database into the production environment.

1. A customer or partner exports the database from SQL Server.
2. The customer or partner imports the database into a sandbox environment that runs on an Azure SQL database. 
3. The customer or partner raises a service request of the **Other request** type in Microsoft Dynamics Lifecycle Services (LCS) to ask the Microsoft Dynamics Support Engineering (DSE) team to move the sandbox database to the production environment.
4. The DSE team copies the database from the sandbox environment to the production environment. 

> [!NOTE]
> Microsoft accepts requests to copy a database into a production environment only before go-live. 

During the process for moving a database, the sqlpackage.exe command-line tool is used to export the database from SQL Server and import it into an Azure SQL database. Because the file name extension for the exported data file is .bacpac, the process is often referred to as the *bacpac process*. Here are the high-level steps.

1. Create a copy of the source database.
2. Run a script to prepare the database.
3. Export the database from SQL Server.
4. Import the database into an Azure SQL database.
5. Run a script to update the database.

If you encounter issues, see the "Known issues and limitations" section at the end of this topic. It explains how to troubleshoot, gives performance tips, and explains limitations of the copy process.

## Prerequisites

- To import a database into an Azure SQL Database environment, you must install the [latest version of Microsoft SQL Server Management Studio](https://msdn.microsoft.com/en-us/library/mt238290.aspx) on the Application Object Server (AOS) computer in **that** environment. You then do the bacpac import on the AOS computer. There are two reasons for this requirement:

    - Because of an Internet Protocol (IP) access restriction on all instances of Finance and Operations that run on Azure SQL Database, connections are allowed only from a computer in that environment.
    - The version of Management Studio that is installed by default is for a previous version of SQL Server and can't perform the required tasks.

> [!IMPORTANT]
> If your environment includes Microsoft Dynamics 365 for Retail components, you must manually store some environment-specific values before you begin. For more information, see the "Additional steps for Retail environments" section.

## Before you begin

Encrypted and environment-specific values can't be imported into a new environment. After you've completed the import, you must re-enter some data from your source environment in your target environment.

### Document the values of encrypted fields

Because of a technical limitation that is related to the certificate that is used for data encryption, values that are stored in encrypted fields in a database will be unreadable after that database is imported into a new environment. Therefore, after an import, you must manually delete and re-enter values that are stored in encrypted fields. New values that are entered in encrypted fields after an import will be readable. The following fields are affected. (The field names are given in *Table*.*Field* format.)

| Table.field name                                         | Where to set the value |
|----------------------------------------------------------|------------------------|
| CreditCardAccountSetup.SecureMerchantProperties          | Select **Accounts receivable** &gt; **Payments setup** &gt; **Payment services**. |
| ExchangeRateProviderConfigurationDetails.Value           | Select **General ledger** &gt; **Currencies** &gt; **Configure exchange rate providers**. |
| FiscalEstablishment\_BR.ConsumerEFDocCsc                 | Select **Organization administration** &gt; **Fiscal establishments** &gt; **Fiscal establishments**. |
| FiscalEstablishmentStaging.CSC                           | This field is used by the Data Import/Export Framework. |
| HcmPersonIdentificationNumber.PersonIdentificationNumber | Select **Human resources** &gt; **Workers** &gt; **Workers**. On the **Worker** tab, in the **Personal information** group, select **Identification numbers**. |
| HcmWorkerActionHire.PersonIdentificationNumber           | This field has been obsolete since the February 2016 release. It previously appeared on the **All worker actions** page (**Human resources** &gt; **Workers** &gt; **Actions** &gt; **All worker actions**). |
| SysEmailSMPTPassword.Password                            | Select **System administration** &gt; **Email** &gt; **Email parameters**. |
| SysOAuthUserTokens.EncryptedAccessToken                  | This field is used internally by AOS. It can be ignored. |
| SysOAuthUserTokens.EncryptedRefreshToken                | This field is used internally by AOS. It can be ignored. |

### If you're running Retail components, document encrypted and environment-specific values

The values on the following pages are either environment-specific or encrypted in the database. Therefore, all the imported values will be incorrect.

- **Accounts receivable** &gt; **Payments setup** &gt; **Payments services**
- **Retail and commerce** &gt; **Channel setup** &gt; **POS setup** &gt; **POS profiles** &gt; **Hardware profiles**

## Create a copy of the source database

Before you can export the source SQL Server database, the database users must be deleted. Therefore, you don't modify the original database. Instead, you create a copy of the source database to work with. The following script backs up the default AxDB database and then restores it to the same instance under a new name. To use this script, first verify that the path D:\\backups exists.

    BACKUP DATABASE [AxDB] TO DISK = N'D:\Backups\axdb_golden.bak' WITH NOFORMAT, NOINIT,
    NAME = N'AxDB_golden-Full Database Backup', SKIP, NOREWIND, NOUNLOAD, COMPRESSION, STATS = 10
    GO
    RESTORE DATABASE [AxDB_CopyForExport] FROM DISK = N'D:\Backups\axdb_golden.bak' WITH FILE = 1,
    MOVE N'AXDBBuild_Data' TO N'F:\MSSQL_DATA\AxDB_CopyForExport.mdf',
    MOVE N'AXDBBuild_Log' TO N'G:\MSSQL_LOGS\AxDB_CopyForExport_Log.ldf',
    NOUNLOAD, STATS = 5

## Run a script to prepare the database

Run the following script against the AxDB\_CopyForExport database that you created in the previous step. This script makes the following changes:

- Set the **SysGlobalConfiguration** flag to inform Finance and Operations that the database is Azure-based.
- Remove a reference to tempDB in the XU\_DisableEnableNonClusteredIndexes procedure. References to tempDB aren't allowed in an Azure SQL database. The reference will be re-created later by the database synchronization process.
- Drop users, because Microsoft Windows users are forbidden in Azure SQL databases. Other users must be re-created later, so that they're correctly linked to the appropriate sign-in on the target server.

A successful export and import of the database requires all these changes.

    update sysglobalconfiguration
    set value = 'SQLAZURE'
    where name = 'BACKENDDB'

    update sysglobalconfiguration
    set value = 1
    where name = 'TEMPTABLEINAXDB'

    drop procedure XU_DisableEnableNonClusteredIndexes
    drop schema [NT AUTHORITY\NETWORK SERVICE]
    drop user [NT AUTHORITY\NETWORK SERVICE]
    drop user axdbadmin
    drop user axdeployuser
    drop user axmrruntimeuser
    drop user axretaildatasyncuser
    drop user axretailruntimeuser

## Export the database from SQL Server

Next, open a **Command Prompt** window as an administrator, and run the following commands.

> [!IMPORTANT]
> If the **140** folder doesn't exist, you need to install the [latest version of Microsoft SQL Server Management Studio](https://msdn.microsoft.com/en-us/library/mt238290.aspx)).

    cd C:\Program Files (x86)\Microsoft SQL Server\140\DAC\bin\
    SqlPackage.exe /a:export /ssn:localhost /sdn:<database to export> /tf:D:\Exportedbacpac\my.bacpac /p:CommandTimeout=1200 /p:VerifyFullTextDocumentTypesSupported=false

Here is an explanation of the parameters:

- **ssn** (source server name) – The name of the SQL Server to export from. For our purposes, the name should always be **localhost**.
- **sdn** (source database name) – The name of the database to export.
- **tf** (target file) – The path and name of the file to export to. The folder should already exist, but the export process will create the file.

## Import the database into an Azure SQL database

Copy the .bacpac file that was generated in the previous step to the AOS computer in the target environment. A typical golden database .bacpac file will be smaller than 100 MB. Therefore, you can copy and paste the file through a Remote Desktop (RDP) window. If the .bacpac file is much larger than 100 MB, [upload the file to an Azure storage account,](https://azure.microsoft.com/en-gb/documentation/articles/storage-use-azcopy/), and then download it to the target AOS computer.

> [!NOTE]
> Microsoft doesn't provide a storage account as part of your Finance and Operations agreement. You must either purchase a storage account or use a storage account from a separate Azure subscription. For performance reasons, we recommend that you put the .bacpac file on drive D on the AOS computer. (For more details, see the "Known issues and limitations" section.)

Open a **Command Prompt** window as an administrator, and run the following commands
> [!IMPORTANT]
> If the **140** folder doesn't exist, you need to install the [latest version of Microsoft SQL Server Management Studio](https://msdn.microsoft.com/en-us/library/mt238290.aspx)).

    cd C:\Program Files (x86)\Microsoft SQL Server\140\DAC\bin\

    SqlPackage.exe /a:import /sf:D:\Exportedbacpac\my.bacpac /tsn:<azure sql database server name>.database.windows.net /tu:sqladmin /tp:<password from LCS> /tdn:<New database name> /p:CommandTimeout=1200 /p:DatabaseEdition=Premium /p:DatabaseServiceObjective=P2

Here is an explanation of the parameters:

- **tsn** (target server name) – The name of the SQL Azure server to import into. The name can be found in LCS. Add the suffix **database.windows.net**.
- **tdn** (target database name) – The name of the database to import into. The database should **not** already exist. The import process will create it.
- **sf** (source file) – The path and file name to import from.
- **tu** (target user) – The SQL user name for the target Azure SQL database instance. We recommend that you use the standard **sqladmin** user. You can retrieve the password for this user from your LCS project.
- **tp** (target password) – The password for the target Azure SQL database user.

You will receive the following warning message. You can safely ignore it.

[![Warning message](./media/sqlpackagewarning.png)](./media/sqlpackagewarning.png)

## Run a script to update the database

Run the following script against the imported database. The script performs the following actions:

- Re-create database users.
- Set the correct performance parameters.
- Enable the SQL Query Store feature.

> [!NOTE]
> You must add the tenant ID to the last three queries. You can find this value by querying the SysServiceConfigurationSetting table in an existing database in the target environment.

    CREATE USER axdeployuser FROM LOGIN axdeployuser
    EXEC sp_addrolemember 'db_owner', 'axdeployuser'
    
    CREATE USER axdeployextuser WITH PASSWORD = '<password from lcs>'
    IF EXISTS (select * from sys.database_principals where type = 'R' and name = 'DeployExtensibilityRole')
    BEGIN
        EXEC sp_addrolemember 'DeployExtensibilityRole', 'axdeployextuser'
    END

    CREATE USER axdbadmin WITH PASSWORD = '<password from lcs>'
    EXEC sp_addrolemember 'db_owner', 'axdbadmin'

    CREATE USER axruntimeuser WITH PASSWORD = '<password from lcs>'
    EXEC sp_addrolemember 'db_datareader', 'axruntimeuser'
    EXEC sp_addrolemember 'db_datawriter', 'axruntimeuser'

    CREATE USER axmrruntimeuser WITH PASSWORD = '<password from lcs>'
    EXEC sp_addrolemember 'ReportingIntegrationUser', 'axmrruntimeuser'
    EXEC sp_addrolemember 'db_datareader', 'axmrruntimeuser'
    EXEC sp_addrolemember 'db_datawriter', 'axmrruntimeuser'

    CREATE USER axretailruntimeuser WITH PASSWORD = '<password from lcs>'
    EXEC sp_addrolemember 'UsersRole', 'axretailruntimeuser'
    EXEC sp_addrolemember 'ReportUsersRole', 'axretailruntimeuser'

    CREATE USER axretaildatasyncuser WITH PASSWORD = '<password from lcs>'
    EXEC sp_addrolemember 'DataSyncUsersRole', 'axretaildatasyncuser'

    ALTER DATABASE SCOPED CONFIGURATION  SET MAXDOP=2
    ALTER DATABASE SCOPED CONFIGURATION  SET LEGACY_CARDINALITY_ESTIMATION=ON
    ALTER DATABASE SCOPED CONFIGURATION  SET PARAMETER_SNIFFING= ON
    ALTER DATABASE SCOPED CONFIGURATION  SET QUERY_OPTIMIZER_HOTFIXES=OFF
    ALTER DATABASE <imported database name> SET COMPATIBILITY_LEVEL = 130;
    ALTER DATABASE <imported database name> SET QUERY_STORE = ON;

    update [dbo].[SYSSERVICECONFIGURATIONSETTING]
    set value ='<tenant ID from existing database>'
    where name = 'TENANTID'

    update dbo.POWERBICONFIG
    set TENANTID = '<tenant ID from existing database>'

    update dbo.PROVISIONINGMESSAGETABLE
    set TENANTID = '<tenant ID from existing database>'

## Synchronize the database

1. Use Remote Desktop to connect to all the computers in the target environment, and stop the following Windows services by using services.msc. These services will have open connections to the Finance and Operations database. After you stop the services, you can replace the existing Finance and Operations database with the newly imported database:

    - World wide web publishing service (on all AOS computers)
    - Microsoft Dynamics 365 for Finance and Operations Batch Management Service (on non-private AOS computers only)
    - Management Reporter 2012 Process Service (on business intelligence [BI] computers only)

2. On the AOS computer where the bacpac import was performed, in Management Studio, run the following script. This script will rename the original database and then rename the newly imported database so that it uses the original database name. In this example, the original database was named axdb\_123456789, and the newly imported database was named importeddb.

    > [!NOTE]
    > Make sure that the you're using the SQL Server 2016 version of Management Studio.

        ALTER DATABASE [axdb_123456789] MODIFY NAME = [axdb_123456789_original]
        ALTER DATABASE [importeddb] MODIFY NAME = [axdb_123456789]

3. Synchronize the database. Open a **Command Prompt** window as an administrator, and run the following commands.

        cd F:\AosService\WebRoot\bin

        Microsoft.Dynamics.AX.Deployment.Setup.exe -bindir "F:\AosService\PackagesLocalDirectory" -metadatadir F:\AosService\PackagesLocalDirectory -sqluser axdbadmin -sqlserver <azure sql database server name>.database.windows.net -sqldatabase <database name> -setupmode sync -syncmode fullall -isazuresql true -sqlpwd <sql password> >log.txt 2>&1

4. Use services.msc to restart the services that you stopped earlier:

    - World wide web publishing service (on all AOS computers)
    - Microsoft Dynamics 365 for Finance and Operations Batch Management Service (on non-private AOS computers only)
    - Management Reporter 2012 Process Service (on BI computers only)

5. At this point, you can open the Finance and Operations application URL and sign in. Verify that the program works as you expect, and then drop the original database by running the following script in Management Studio on the AOS computer where the bacpac import was performed.

        DROP DATABASE [axdb_123456789_original]

### Re-provision the target environment
[!include[environment-reprovision](../includes/environment-reprovision.md)]

### Reset the Financial Reporting database

If you're using Financial Reporting, which was previously named Management Reporter, you must reset the financial reporting database. Follow the steps in [Resetting the financial reporting data mart after restoring a database](../analytics/reset-financial-reporting-datamart-after-restore.md).


## Raise a service request to copy database

To copy the golden database to a production environment, you must submit a service request of the **Other request** type through LCS to ask Microsoft to run the copy action.

> [!NOTE]
> You can't use a request of the **Database refresh request** type, because the request involves copying to a production environment.

1. In LCS, select the hamburger icon, and then select **Work items**.

    [![Work items](./media/lcsworkitemsmenu.png)](./media/lcsworkitemsmenu.png)

2. On the **Work items** page, select **Add**, and then select **Other request**.

    [![Other request](./media/lcsotherrequest.png)](./media/lcsotherrequest.png)

3. In the **Other requests** dialog box, follow these steps:

    1. In the **Environment name** field, select the production environment.
    2. Set the **Preferred downtime start date** and **Preferred downtime end date** fields. The end date must be at least one hour after the start date. To help guarantee that resources are available to run the request, submit your request at least 24 hours before your preferred downtime window.
    3. In the **Request** field, enter the following details: **This is a request for a golden database copy from the sandbox environment &lt;source sandbox environment name&gt; to production. I acknowledge that this will overwrite the database currently in production.**

    [![Other requests dialog box](./media/lcsotherrequestform.png)](./media/lcsotherrequestform.png)

## Additional steps for Retail environments

If your environment includes Retail components, you must perform additional steps to help guarantee that the environment will work after the database import.

### Re-enter encrypted and environment-specific values in the target database

The values on the following page are encrypted in the database. Therefore, all the imported values will be incorrect.

- **Accounts receivable** &gt; **Payments setup** &gt; **Payments services**
- **Retail and commerce** &gt; **Channel setup** &gt; **POS setup** &gt; **POS profiles** &gt; **Hardware profiles**

In the target system, open these pages, and enter the values that you documented earlier.

## Re-enter data from encrypted and environment-specific fields in the target database

In the Finance and Operations client, enter the values that you documented for the encrypted and environment-specific fields. The following fields are affected. (The field names are given in *Table*.*Field* format.)

| Table.field name                                         | Where to set the value |
|----------------------------------------------------------|------------------------|
| CreditCardAccountSetup.SecureMerchantProperties          | Select **Accounts receivable** &gt; **Payments setup** &gt; **Payment services**. |
| ExchangeRateProviderConfigurationDetails.Value           | Select **General ledger** &gt; **Currencies** &gt; **Configure exchange rate providers**. |
| FiscalEstablishment\_BR.ConsumerEFDocCsc                 | Select **Organization administration** &gt; **Fiscal establishments** &gt; **Fiscal establishments**. |
| FiscalEstablishmentStaging.CSC                           | This field is used by the Data Import/Export Framework. |
| HcmPersonIdentificationNumber.PersonIdentificationNumber | Select **Human resources** &gt; **Workers** &gt; **Workers**. On the **Worker** tab, in the **Personal information** group, select **Identification numbers**. |
| HcmWorkerActionHire.PersonIdentificationNumber           | This field has been obsolete since the February 2016 release. It previously appeared on the **All worker actions** page (**Human resources** &gt; **Workers** &gt; **Actions** &gt; **All worker actions**). |
| SysEmailSMPTPassword.Password                            | Select **System administration** &gt; **Email** &gt; **Email parameters**. |
| SysOAuthUserTokens.EncryptedAccessToken                  | This field is used internally by AOS. It can be ignored. |
| SysOAuthUserTokens.EncryptedRefreshToken                | This field is used internally by AOS. It can be ignored. |

## Known issues and limitations
### I can't download the Management Studio installer

When you try to download the Management Studio installer, you might receive the following message: "Your current security settings do not allow this file to be downloaded." 

[![Error message](./media/securitysettingscannotdownload.png)](./media/securitysettingscannotdownload.png) 

To work around this issue, in your web browser, in **Internet Options**, on the **Security** tab, enable file downloads for the **Internet** zone, as shown in the following illustration. 

[![Enable file downloads](./media/securitysettingsfix.png)](./media/securitysettingsfix.png)

### Performance

The following guidelines can help you achieve optimal performance:

- Always export from a computer that is located in the same Azure datacenter as the Azure SQL database instance. In practice, this guideline means that, when you export a copy of your sandbox database, you should export it from the sandbox AOS computer.
- Always import the .bacpac file locally on the computer that is running the SQL Server instance. Don't import it from Management Studio on a remote computer.
- In a one-box environment (Tier 1 environment) that is hosted in Azure, put the .bacpac file on drive D when you export it. For more information about the temporary drive on Azure computers, see the [Understanding the temporary drive on Windows Azure Virtual Machines](https://blogs.msdn.microsoft.com/mast/2013/12/06/understanding-the-temporary-drive-on-windows-azure-virtual-machines/) post on the Azure Support Team blog.
- To help make the import process faster, and to help improve the speed of a restore from a .bak file, grant the account that is running the SQL Server Windows service the [Instance File Initialization](https://msdn.microsoft.com/en-us/library/ms175935.aspx) right. To easily implement this guideline for a developer environment, set SQL Server to run as the axlocaladmin account.
- We recommend that you not use the option to export and import from SQL Azure in Management Studio. (This option is also known as **Export data tier application**.) We recommend that you not use this approach, because there can be memory limitations for larger databases.
