---
# required metadata

title: Retain a copy of a Dynamics 365 for Operations database to restore later
description: This topic provides instructions for exporting a Microsoft Dynamics 365 for Operations database to a file and then reimporting that file to the same instance or another instance of the application. This procedure can only be used in non-production environments. 
author: MargoC
manager: AnnBe
ms.date: 2017-02-03 19 - 56 - 01
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
# ms.reviewer: 11
ms.search.scope: Operations, Platform
# ms.tgt_pltfrm: 
ms.custom: 269254
ms.assetid: 7464b180-8ace-4b65-8b53-ba608d0611e1
ms.search.region: Global
# ms.search.industry: 
ms.author: tabell
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Platform update 3

---

# Retain a copy of a Dynamics 365 for Operations database to restore later

This topic provides instructions for exporting a Microsoft Dynamics 365 for Operations database to a file and then reimporting that file to the same instance or another instance of the application. This procedure can only be used in non-production environments. 

You might want to retain a copy of a Dynamics 365 for Operations database process in several situations:

-   To take strategic backups to restore to in the future. For example, before or after a major code update you might want copies to use for reference later.
-   To back up a database before destructive testing and then restore it afterward.
-   When upgrading to a new major release of Microsoft Dynamics 365 for Operations, this process can be used to export your old test database and bring it forward to the new version.

Be aware that Microsoft also provides a standard feature which provides the ability to restore an Azure SQL database environment to a point-in-time within the last 35 days via a service request. For more information, see [Request a point-in-time database restore on a non-production environment](request-point-in-time-restore.md).

## Prerequisites
To export a database from a sandbox environment you must install the latest SQL Server 2016 Management Studio to the AOS machine in that environment and perform the export on that AOS machine. This is for two reasons. First, there is an IP access restriction on the sandbox SQL Server instance, which only allows a connection from a machine within that environment. Second, the version of SQL Server Management Studio installed by default is for a previous version of SQL Server and can’t complete the tasks required.

## Export the Dynamics 365 for Operations database
### Stop services

Use Remote Desktop to connect to all the computers in the environment and stop the following Windows services by using services.msc. These services will have open connections to the Dynamics 365 for Operations database.

-   World wide web publishing service (on all AOS computers)
-   Microsoft Dynamics AX Batch Management Service (on non-private AOS computers only)
-   Management Reporter 2012 Process Service (on BI computers only)

### Execute sqlpackage to export the Dynamics 365 for Operations database

Open a command prompt as an Administrator, and then execute the following commands.

    cd C:\Program Files (x86)\Microsoft SQL Server\130\DAC\bin

    SqlPackage.exe /a:export /ssn:<server>.database.windows.net /sdn:<database to export> /tf:D:\Exportedbacpac\my.bacpac /p:CommandTimeout=1200 /p:VerifyFullTextDocumentTypesSupported=false /sp:<sql password> /su:<sql user>

The parameters include:

-   **ssn** (source server name) - The name of the SQL Azure server from which you will export.
-   **sdn** (source database name) - The name of the database that you will export.
-   **tf** (target file) - The path and file name that you will export to.
-   **sp** (source password) - The SQL password for the source SQL Server.
-   **su** (source user) - The SQL user name for the source SQL Server. We recommend that you use the **sqladmin** user, which the deployment will have created on every Dynamics SQL instance. You can retrieve the password for this user from your Lifecycle Services (LCS) project.

Running this command creates a .bacpac file on the D:\\Exportedbacpac folder. You can take this file and copy or upload it to secure location so that it can be imported into a different environment at another time. You can use the AzCopy command line utility to upload the file to an Azure storage account[,](https://azure.microsoft.com/en-gb/documentation/articles/storage-use-azcopy/) and then download it to the target AOS computer. For more information, see [Copy or upload the file to an Azure storage account](https://docs.microsoft.com/en-gb/azure/storage/storage-use-azcopy). **Note:** Microsoft doesn’t provide a storage account as part of your Dynamics 365 for Operations agreement. You must either purchase a storage account or use a storage account from a separate Azure subscription. **Important:** Be aware of the behavior of the D drive on Azure Virtual Machines, do not keep your exported database files here permanently unless you are prepared to lose them. For details, see [Understanding the temporary drive on Windows Azure virtual machines (blog post)](https://blogs.msdn.microsoft.com/mast/2013/12/06/understanding-the-temporary-drive-on-windows-azure-virtual-machines/).

### Start services

Use services.msc to restart the services that you stopped earlier:

-   World wide web publishing service (on all AOS computers)
-   Microsoft Dynamics AX Batch Management Service (on non-private AOS computers only)
-   Management Reporter 2012 Process Service (on BI computers only)

## Import the Dynamics 365 for Operations database
### Stop services

Use Remote Desktop to connect to all the computers in the environment and stop the following Windows services by using services.msc. These services will have open connections to the Dynamics 365 for Operations database.

-   World wide web publishing service (on all AOS computers)
-   Microsoft Dynamics AX Batch Management Service (on non-private AOS computers only)
-   Management Reporter 2012 Process Service (on BI computers only)

### Import the bacpac file

Copy the .bacpac file that was generated in the export step to the AOS computer in the target environment. For performance reasons, we recommend that you place the .bacpac file on the drive D on the AOS computer. Open a **Command Prompt** window as an administrator, and run the following commands.

    cd C:\Program Files (x86)\Microsoft SQL Server\130\DAC\bin\

    SqlPackage.exe /a:import /sf:D:\Exportedbacpac\my.bacpac /tsn:<azure sql database server name>.database.windows.net /tu:sqladmin /tp:<password from LCS> /tdn:<New database name> /p:CommandTimeout=1200 /p:DatabaseEdition=Premium /p:DatabaseServiceObjective=P2

The parameters include:

-   **tsn** (target server name) – The name of the SQL Azure server to import into. The name can be found in LCS. Add the suffix **database.windows.net**.
-   **tdn** (target database name) – The name of the database to import into. The database should **not** already exist. The import process will create it.
-   **sf** (source file) – The path and file name to import from.
-   **tu** (target user) – The SQL user name for the target Azure SQL database instance. We recommend that you use the standard **sqladmin** user. You can retrieve the password for this user from your LCS project.
-   **tp** (target password) – The password for the target Azure SQL database user.

### Run a script to update the Dynamics 365 for Operations database

If the source and target environments have different SQL user passwords, then you will need to run this script. If you are not sure if the passwords are different, you need to run this script. Run the following script against the imported database. The script will drop the database users and recreate them with the correct passwords for the target environment.

    ALTER AUTHORIZATION ON Fulltext Catalog::[<enter the name of the full text catalog in your database] TO [dbo];

    declare @userSQL varchar(1000)
    set quoted_identifier off

    declare userCursor CURSOR for
    select 'DROP USER ' + name
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

    CREATE USER axdeployuser FROM LOGIN axdeployuser
    EXEC sp_addrolemember 'db_owner', 'axdeployuser'

    CREATE USER axdbadmin WITH PASSWORD = '<password from LCS>'
    EXEC sp_addrolemember 'db_owner', 'axdbadmin'

    CREATE USER axruntimeuser WITH PASSWORD = '<password from LCS>'
    EXEC sp_addrolemember 'db_datareader', 'axruntimeuser'
    EXEC sp_addrolemember 'db_datawriter', 'axruntimeuser'

    CREATE USER axmrruntimeuser WITH PASSWORD = '<password from LCS>'
    EXEC sp_addrolemember 'ReportingIntegrationUser', 'axmrruntimeuser'
    EXEC sp_addrolemember 'db_datareader', 'axmrruntimeuser'
    EXEC sp_addrolemember 'db_datawriter', 'axmrruntimeuser'

    CREATE USER axretailruntimeuser WITH PASSWORD = '<password from LCS>'
    EXEC sp_addrolemember 'UsersRole', 'axretailruntimeuser'
    EXEC sp_addrolemember 'ReportUsersRole', 'axretailruntimeuser'

## Limitations
The link between the database and document handling documents that are stored in Azure blob storage might be broken after importing a database. If you have custom code that utilizes the X++ class FileUpload to place files in blob storage, the links to these files might also be broken.

