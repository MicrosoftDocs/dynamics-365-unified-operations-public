---
# required metadata

title: Change database collation for development environments
description: This article describes how to change the database collation for development environments
author: ttreen 
ms.date: 07/26/2023
ms.topic: article
audience: Developer, IT Pro
ms.reviewer: twheeloc
ms.search.region: Global
ms.author: ttreen
ms.search.validFrom: 
ms.search.form: 2022-04-08

---

# Change database collation for development environments

[!include[banner](../includes/banner.md)]

**SQL_Latin1_General_CP1_CI_AS** is the only supported database collation in D365 Finance and Operations. For Self-Service environments the **Data Migration Toolkit** handles this collation conversion as part of the SQL replication process. However, for development environments (Tier 1 Cloud Hosted Environments), the database collation must be changed prior to running the data upgrade. This article details the steps you must complete to change the collation.

For details on SQL database collations see: [Collation and Unicode support](https://learn.microsoft.com/en-us/sql/relational-databases/collations/collation-and-unicode-support?view=sql-server-ver16)

## Database collation change procedure
Database collation can only be changed by reconstructing the entire database. The [SQLPackage Tool](https://learn.microsoft.com/en-us/sql/tools/sqlpackage/sqlpackage?view=sql-server-ver16) is used for this process.
1. Download and install **SQLPackage**, see: [Download and install SqlPackage](https://learn.microsoft.com/en-us/sql/tools/sqlpackage/sqlpackage-download?view=sql-server-ver16)
2. Export the AX 2012 database you are upgrading to a **\*.bacpac** file. Open an **Command Prompt** as **Admin**, and run the following (edit source server name, source database name and target file as needed)
   ```
   SqlPackage.exe /Action:Export /SourceServerName:localhost /SourceDatabaseName:MicrosoftDynamicsAX /TargetFile:"C:\Temp\MicrosoftDynamicsAX.bacpac" /Properties:CommandTimeout=1200 /Properties:VerifyFullTextDocumentTypesSupported=False
   ```
3. Open the exported **\*.bacpac** file with archiving software, e.g 7Zip or WinZip.
4. Extract\Copy the **model.xml** file from the **\*.bacpac** archive to the same folder.
5. Open and edit the **model.xml** you just extracted in the step above with Notepad or your preferred editing tool.
6. Find in the **model.xml** file the following property **Name=\"Collation"**, and edit the current collation value to **SQL_Latin1_General_CP1_CI_AS**, see example below:
    - From:
   ```XML
   <Property Value="Danish_Norwegian_CI_AS" Name="Collation"/>
   ```
    - To:
   ```XML
   <Property Value="SQL_Latin1_General_CP1_CI_AS" Name="Collation"/>
   ```
7. Import the **\*.bacpac** file back into the database server to create a new database.  Again, **SQLPackage** will be used, and the modified **model.xml** file will be referenced. Open an **Command Prompt** as **Admin**, and run the following (edit source file, target server name, target database name and model file path as needed)
   ```
   SqlPackage.exe /Action:Import /SourceFile:"C:\Temp\MicrosoftDynamicsAX.bacpac" /TargetServerName:localhost /TargetDatabaseName:MicrosoftDynamicsAX_NewCollation /Properties:CommandTimeout=1200 /ModelFilePath:"C:\Temp\model.xml"
   ```

## Next Steps
Follow the notes in [Upgrade from AX 2012 - Data upgrade in development environments](data-upgrade-2012.md)
