---
# required metadata

title: Change the database collation for development environments
description: This article describes how to change the database collation for development environments.
author: ttreen 
ms.date: 08/03/2023
ms.topic: article
audience: Developer, IT Pro
ms.reviewer: twheeloc
ms.search.region: Global
ms.author: ttreen
ms.search.validFrom: 
ms.search.form: 2022-04-08

---

# Change the database collation for development environments

[!include[banner](../includes/banner.md)]

**SQL\_Latin1\_General\_CP1\_CI\_AS** is the only supported database collation in finance and operations apps. For self-service environments, the Data migration toolkit handles collation conversion as part of the SQL replication process. However, for development environments (Tier 1 cloud-hosted environments), the database collation must be changed before the data upgrade is run. This article describes how to change the collation.

For more information about SQL database collations, see [Collation and Unicode support](/sql/relational-databases/collations/collation-and-unicode-support).

## Change the database collation

To change the database collation, you must reconstruct the whole database. Use the [SQLPackage](/sql/tools/sqlpackage/sqlpackage) tool.

1. Download and install SQLPackage. For more information, see [Download and install SqlPackage](/sql/tools/sqlpackage/sqlpackage-download).
1. Export the Microsoft Dynamics AX 2012 database that you're upgrading to a **\*.bacpac** file. Open a Command Prompt window as an administrator, and run the following command. Edit the source server name, source database name, and target file as required.

    ```
    SqlPackage.exe /Action:Export /SourceServerName:localhost /SourceDatabaseName:MicrosoftDynamicsAX /TargetFile:"C:\Temp\MicrosoftDynamicsAX.bacpac" /Properties:CommandTimeout=1200 /Properties:VerifyFullTextDocumentTypesSupported=False
    ```

1. Use archiving software such as 7 Zip or WinZip to open the exported **\*.bacpac** file.
1. Extract the **model.xml** file from the **\*.bacpac** archive, and copy it to the same folder.
1. In your preferred editing tool, open the extracted **model.xml** file for editing.
1. In the **model.xml** file, find the following property (collation stated maybe different).

    ```XML
    <Property Value="Danish_Norwegian_CI_AS" Name="Collation"/>
    ```

1.  Edit the value to **SQL\_Latin1\_General\_CP1\_CI_AS**.

    ```XML
    <Property Value="SQL_Latin1_General_CP1_CI_AS" Name="Collation"/>
    ```

1. Import the **\*.bacpac** file back into the database server to create a new database. SQLPackage is used, and the modified **model.xml** file is referenced. Open a Command Prompt window as an administrator, and run the following command. Edit the source file, target server name, target database name, and model file path as required.

    ```
    SqlPackage.exe /Action:Import /SourceFile:"C:\Temp\MicrosoftDynamicsAX.bacpac" /TargetServerName:localhost /TargetDatabaseName:MicrosoftDynamicsAX_NewCollation /Properties:CommandTimeout=1200 /ModelFilePath:"C:\Temp\model.xml"
    ```

## Next steps

For next steps, see [Upgrade from AX 2012 - Data upgrade in development environments](data-upgrade-2012.md).
