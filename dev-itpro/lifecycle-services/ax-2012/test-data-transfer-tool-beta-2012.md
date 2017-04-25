---
# required metadata

title: Test Data Transfer Tool (beta) 
description: The Microsoft Dynamics AX 2012 Test Data Transfer Tool (beta) (DP.exe) is a command-line tool that exports data from a Microsoft Dynamics AX 2012 business database in a production or non-production environment. The tool also imports data into a Microsoft Dynamics AX 2012 business database in a non-production environment. The non-production environment can be either a development or test environment.
author: kfend
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
# ms.reviewer: 51
ms.search.scope: AX 2012
# ms.tgt_pltfrm: 
ms.custom: 18651
ms.assetid: de54d768-d7a3-45d4-93bf-e95356b797aa
ms.search.region: Global
# ms.search.industry: 
ms.author: kfend
ms.search.validFrom: 
ms.dyn365.ops.version: 2012

---

# Test Data Transfer Tool (beta) (AX 2012)

[!include[banner](../includes/banner.md)]


The Microsoft Dynamics AX 2012 Test Data Transfer Tool (beta) (DP.exe) is a command-line tool that exports data from a Microsoft Dynamics AX 2012 business database in a production or non-production environment. The tool also imports data into a Microsoft Dynamics AX 2012 business database in a non-production environment. The non-production environment can be either a development or test environment.

The Test Data Transfer Tool (beta) has been moved. It is now available from the **Downloadable tools** section of Microsoft Dynamics Lifecycle Services. [Go to Lifecycle Services](https://lcs.dynamics.com). **Note:** Microsoft does not support using the Test Data Transfer Tool (beta) to import data into a production environment. The tool can be used only to export data from a production environment, and to import data into a test or development environment. The Test Data Transfer Tool (beta) is especially useful in the following circumstances:

-   You want to export or import a large, multicompany dataset.
-   You have to move data between different Microsoft Dynamics AX environments that have slightly different customizations.
-   You have to store data in a version control system.
-   You have to export or import data without running Microsoft Dynamics AX Application Object Server (AOS).

## Benefits
The Test Data Transfer Tool (beta) uses the Microsoft SQL Server bulk copy tool (bcp). The Test Data Transfer Tool (beta) provides the following key benefits that other methods for importing and exporting Microsoft Dynamics AX data do not provide:

-   You can export or import data when an AOS instance is not running.
-   You can export or import Microsoft Dynamics AX data more quickly compared to other methods.
-   Only minimal changes are made to the data that you import. This feature helps guarantee that the data is stable over time. For example, the tool never renumbers RecIDs.
-   The data file format is text-based. Therefore, the data can be compared with earlier versions and stored in a version control system.
-   The data file format is a standard format that is produced by bcp.

The Test Data Transfer Tool (beta) adds the following features that work with bcp. These features make bcp an appropriate tool for managing data for Microsoft Dynamics AX.

-   Exported data can be filtered. Therefore, specified tables, columns, or rows can be easily excluded from the export.
-   Differences between builds of Microsoft Dynamics AX 2012 are found and corrected. These differences often occur during development. Because of this feature, data can often be imported without user intervention, even when the table definitions have changed. For example, tables or fields that have been renamed do not prevent import.
-   Entity IDs, such as table IDs, class IDs, and extended data type IDs, are updated to match the IDs of the target system.
-   The tool reads and correctly updates the **SYSTEMSEQUENCES** table.

## Limitations
-   The Test Data Transfer Tool (beta) does not make sure that data that you export is complete or coherent. However, the tool does export any data that you ask it to export.
-   The tool does not make sure that data that you import produces a complete or coherent database. However, the tool does import any data that you ask it to import.
-   The Test Data Transfer Tool (beta) can only be used to move data between environments that are running on the same version of AX 2012, for example, from an AX 2012 R2 production environment to a AX 2012 R2 test environment. You can move data between different builds of the same version. To move data between environments that are running on different versions, you must first upgrade the database through the standard upgrade process.

The Test Data Transfer Tool (beta) imports and exports the data as-is. In some cases, you might exclude tables or records from either import or export. Nevertheless, the tool does not make sure that the data is complete or coherent when other tables contain references to excluded tables or records. Therefore, after import and export, you must make sure that the data that you are importing or exporting is coherent.

## Who should use this tool
Only advanced users should use the Test Data Transfer Tool (beta). You should be a database administrator or a developer who has experience using SQL Server. You should also have permission to read from or write directly to the Microsoft Dynamics AX database that you are working with, and to execute applications directly on the computer that is hosting the database. Before you use the tool, you should read this topic and understand how the tool works. The Test Data Transfer Tool (beta) is a powerful tool for importing and exporting data, but every operation that works with data has risks. You are responsible for creating regular backups of your data before you perform operations by using the tool. You are also responsible for testing your particular uses of the tool to determine whether the tool meets your requirements. You should also make sure that you understand which conditions are logged as errors during import. For example, you might try to import data for a table or column that does not exist in the target database. This attempt is not treated as an error by the tool, because the tool is designed to work seamlessly when the source and target databases have a different set of tables. If you are not sure whether the Test Data Transfer Tool (beta) is the tool that you should use, see [Plan for data](http://technet.microsoft.com/library/8b061683-1c1c-40a0-af49-c2cda7c86f9c(AX.60).aspx).

## Personally identifiable information
The Microsoft Dynamics AX 2012 Test Data Transfer Tool (beta) runs in the security context of the user who starts the tool. Therefore, the tool has the same permissions and restrictions that the user has when he or she accesses SQL Server directly. You must run the tool directly from the computer that is hosting the database during import.

See also
--------

[Plan data import, export, and migration](http://technet.microsoft.com/library/a05289fb-0f8f-4563-be3c-7c840bfea7e1(AX.60).aspx)

[Install the Test Data Transfer Tool (beta) for Microsoft Dynamics AX](install-test-data-transfer-tool-beta.md)

[Run the Test Data Transfer Tool (beta) for Microsoft Dynamics AX](run-test-data-transfer-tool-beta.md)



