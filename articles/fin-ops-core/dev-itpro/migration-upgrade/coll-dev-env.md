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

**SQL_Latin1_General_CP1_CI_AS** is the only supported database collation in Dynamics 365 finance and operations. For self-service environments, the **Data migration toolkit** handles this collation conversion as part of the SQL replication process. However, for development environments (Tier 1 cloud hosted environments), the database collation must be changed prior to running the data upgrade. This article describes the steps to change the collation.

For details on SQL database collations, see: [Collation and Unicode support](/sql/relational-databases/collations/collation-and-unicode-support).

## Database collation change 
Database collation can only be changed by reconstructing the entire database. The [SQLPackage tool](/sql/tools/sqlpackage/sqlpackage) is used.
1. Download and install **SQLPackage**, see: [Download and install SqlPackage](/sql/tools/sqlpackage/sqlpackage-download).
2. Export the AX 2012 database you're upgrading to a **\*.bacpac** file. Open a Command prompt window as an administrator. Run the following (edit source server name, source database name and target file as needed).
   ```
   SqlPackage.exe /Action:Export /SourceServerName:localhost /SourceDatabaseName:MicrosoftDynamicsAX /TargetFile:"C:\Temp\MicrosoftDynamicsAX.bacpac" /Properties:CommandTimeout=1200 /Properties:VerifyFullTextDocumentTypesSupported=False
   ```
3. Open the exported **\*.bacpac** file with archiving software, e.g 7 Zip or WinZip.
4. Extract and copy the **model.xml** file from the **\*.bacpac** archive to the same folder.
5. Open and edit the **model.xml** that was extracted in the previous step with your preferred editing tool.
6. In the **model.xml** file, find the following property **Name=\"Collation"**. Edit the current collation value to **SQL_Latin1_General_CP1_CI_AS**:
    - From:
   ```XML
   <Property Value="Danish_Norwegian_CI_AS" Name="Collation"/>
   ```
    - To:
   ```XML
   <Property Value="SQL_Latin1_General_CP1_CI_AS" Name="Collation"/>
   ```
7. Import the **\*.bacpac** file back into the database server to create a new database. The **SQLPackage** is used and the modified **model.xml** file is referenced. Open a Command prompt window as an administrator. Run the following (edit the source file, target server name, target database name and model file path as needed).
   ```
   SqlPackage.exe /Action:Import /SourceFile:"C:\Temp\MicrosoftDynamicsAX.bacpac" /TargetServerName:localhost /TargetDatabaseName:MicrosoftDynamicsAX_NewCollation /Properties:CommandTimeout=1200 /ModelFilePath:"C:\Temp\model.xml"
   ```

## Next steps
For next steps, see [Upgrade from AX 2012 - Data upgrade in development environments](data-upgrade-2012.md).
