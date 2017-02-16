---
# required metadata

title: Run the Test Data Transfer Tool (beta) for Dynamics AX (AX 2012)
description: 
author: kfend
manager: AnnBe
ms.date: 2015-12-04 19 - 13 - 31
ms.topic: article
ms.prod: 
ms.service: Lifecycle Services
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
# ms.reviewer: 51
ms.search.scope: AX 2012
# ms.tgt_pltfrm: 
ms.custom: 17571
ms.assetid: 2ad74cd3-3286-48da-9ac1-e248d8f44c9b
ms.search.region: Global
# ms.search.industry: 
ms.author: kfend
ms.dyn365.ops.intro: 
ms.dyn365.ops.version: 2012

---

# Run the Test Data Transfer Tool (beta) for Dynamics AX (AX 2012)



Security and permissions
------------------------

The Test Data Transfer Tool (beta) requires only Microsoft SQL Server permissions.

| **Caution**                                                                                                                         |
|-------------------------------------------------------------------------------------------------------------------------------------|
| The Test Data Transfer Tool (beta) does not in any way recognize the security mechanisms that are built into Microsoft Dynamics AX. |

If you have permission to execute **SELECT** statements in SQL Server Management Studio or to use the SQL Server bulk copy tool (bcp) to export data, you have the permissions that are required to export data by using the Test Data Transfer Tool (beta). The following SQL Server permissions are required during export:

-   Read permission to the sys schema to read tables, indexes, and sysdatabases
-   Read permission to the ModelElements view
-   Read permission to the SQLDictionary table
-   Read permission to the ElementType table
-   Read permission to the ModelElement table
-   Read permission to the table that you are exporting

If you have permission to execute **SELECT** statements and **BULK INSERT** statements in SQL Server Management Studio, you have the permissions that are required to import data by using the tool. The following SQL Server permissions are required during import:

-   Read permission to the sys schema to read tables, indexes, and sysdatabases
-   Read permission to the ModelElements view
-   Read permission to the SQLDictionary table
-   Read permission to the ElementType table
-   Read permission to the ModelElement table
-   Read/write permission to the SYSTEMSEQUENCES table
-   Write permission to the table that you are importing
-   Permission to execute **ALTER INDEX** on the table that you are importing, if the data violates unique index constraints and you want the index to be disabled automatically
-   Appropriate permissions for any SQL commands that are found in the \[Import\] directory

## Run the tool
You must run the Test Data Transfer Tool (beta) from a system that has the SQL Server client tools installed, so that the bcp utility is in the command-prompt path. You must run the tool directly from the computer that is hosting the database during import. To run the Test Data Transfer Tool (beta), follow these steps.
1.  Stop the instance of Microsoft Dynamics AX Application Object Server (AOS).
2.  Run the Test Data Transfer Tool (beta) (DP.exe). Include arguments that describe the action to take.

As the tool runs, the following information is displayed:
-   The tool’s progress
-   The number of tables that must still be processed
-   The number of errors that have occurred

After processing is completed, the tool writes the DPLog.xml log file to the current directory. To find errors, search for ‘failed’ in the log file.
### Syntax

    DP.exe direction directory database server

All arguments are optional.
| Parameter   | Default value         | Description                                                                                                                                                                                                                                                                                                           |
|-------------|-----------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| *direction* | EXPORT                | Specify EXPORT to export data or IMPORT to import data.                                                                                                                                                                                                                                                               |
| *directory* | The current directory | Specify the directory from which the data should be exported or to which the data should be imported.                                                                                                                                                                                                                 |
| *database*  | AXDB                  | The name of the database.                                                                                                                                                                                                                                                                                             |
| *server*    | The current computer  | Specify the computer name or instance name of the SQL Server computer that is hosting the Microsoft Dynamics AX database. To specify an instance name, enter it in the format ServerNameInstanceName. If you have a named instance on a local computer, you can use the format localhostInstanceName or InstanceName. |

  You can view a summary of the command-line options by using the following command.

    DP.exe -?

### Stop the tool

To stop the tool, press Ctrl+C. The tool finishes the tables that it is currently working on and then closes.

## Overview of data export and import
The Test Data Transfer Tool (beta) exports and imports three files for each Microsoft Dynamics AX table. If tables have dependencies in Microsoft Dynamics AX, these files support the capability of the tool to export and import the tables independently of related tables. The following diagram shows the export and import process. ![Process of exporting and importing data](./media/dataportprocess.jpg)
### Export and import process

The following table describes the three types of files.
| File type | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
|-----------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| .out      | A bcp data file that contains table data. Columns are separated by \#|EOC|\#. Rows are separated by \#|EOR|\#n.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| .xml      | A bcp data file that contains the table metadata (column descriptions).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| .outmodel | A file that contains metadata that is specific to Microsoft Dynamics AX. This metadata includes all names and IDs of the table and its fields. This file also includes the **elementType** attribute, which stores the names and IDs of any Microsoft Dynamics AX tables, classes, or extended data types that are referenced by the table.This information is used during import to match up fields that have been renamed. The information is also used to update the table IDs, class IDs, or data type IDs so that those IDs match the IDs in the target database.Data in the .outmodel file is constructed from the Metadata.xml file. This file is generated by an X++ job that you run from Microsoft Dynamics AX on the source database. |

When the Test Data Transfer Tool (beta) exports data, the Metadata.xml file is used to identify table relationships and EDT references that require additional information during import. This additional information is included in the .outmodel file that the tool exports. It is important that you maintain an updated .outmodel file in some scenarios, such as scenarios that involve table inheritance. Each row in the **SuperType** table includes an **InstanceRelationType** column that contains the Microsoft Dynamics AX ID of the **SubType** table for that row. Because the Microsoft Dynamics AX IDs can change over time, the data in the .out file can become inaccurate. The Test Data Transfer Tool (beta) uses information from the Metadata.xml file to avoid this situation and to make sure that the data is imported correctly. When you import files, make sure that the Metadata.xml file is current. During the import process, the tool uses the .outmodel file to recognize the relationships. The tool then queries Microsoft Dynamics AX to make sure that the data is imported correctly. For example, the .outmodel file indicates that the value to insert into the **InstanceRelationType** column is **1234**. However, the tool recognizes that new tables have been added to the new Microsoft Dynamics AX ID for which the subtype table is **1235**. When you use a Metadata.xml file that is out of date, the data is usually imported and exported without any errors. This lack of errors can make it difficult to diagnose issues. The Microsoft Dynamics AX IDs that are included in the .out file are typically correct. However, when a table’s Microsoft Dynamics AX ID changes, the data import is completed successfully, but incorrect values are added in the Microsoft Dynamics AX ID field. For example, payroll data contains some inheritance tables that are related to the setup of an employee’s payroll tax. If you load data that was exported by using an outdated Metadata.xml file, several issues occur that involve the inheritance relationships in the tables. When you are running Microsoft Dynamics AX as an administrator, the inheritance relationships can be correctly resolved, and the payroll payments are then generated correctly. However, if you are running Microsoft Dynamics AX as a non-administrator, the X++ code does not read the records from the database. Therefore, the payroll payments that are generated do not include any taxes.

## Exporting data
The procedure for exporting data consists of the following general steps:
1.  Generate a Metadata.xml file.
2.  Determine which data to export.
3.  Run the tool.

### Generate the Metadata.xml file

Before you use the Test Data Transfer Tool (beta) to export data, you must generate the Metadata.xml file on the source system. The Metadata.xml file is used only during export.
| **Note**                                                                                                                                                                                                                                                                                             |
|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| The Metadata.xml file can become out of date if you do not update it periodically. If the file is out of date, the exported data might not contain the **elementType** attribute, and the import might not update the IDs to match the IDs in the target database.You must update the file manually. |

To update the Metadata.xml file, follow these steps.
1.  Import the MetadataXMLGenerator.xpo from the same folder that DP.exe is stored in, and then run the MetadataXMLGenerator job.A new Metadata.xml file is created in a temporary folder on your computer.
2.  Locate the new Metadata.xml file in one of the following ways:
    -   When the MetadataXMLGenerator job is completed, the path of the new Metadata.xml file is provided in the Infolog.
    -   Open a Command Prompt window, and enter **echo %temp%** to view the path of the temporary folder where the Metadata.xml file is stored.

3.  Navigate to the temporary folder, and then copy the Metadata.xml file to the subfolder where the Test Data Transfer Tool (beta) is installed. If there is an existing Metadata.xml file in the \[Lists\] subfolder, overwrite the existing Metadata.xml file by using the Metadata.xml file that you just generated.

### Choose data to export

The Test Data Transfer Tool (beta) is designed to export all data from all tables in the database, unless tables, columns, or rows are filtered out of the exported data. The tool is preconfigured to include a set of filters that filter out many tables. The preconfigured filters are based on the following guidelines:
-   Do not export tables that contain code or models.
-   Do not export security settings.
-   Do not export computer-specific data.
-   Do not export user-specific data.
-   Do not export temp tables.

These filters might not be complete or appropriate for your requirements. For example, you might want to export some of the data that is filtered out by default, or you might have additional tables that should not be exported.
| **Important**                                                                                                                                                                                                                                                                                                                                                                                                                    |
|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| If a table contains a **RecVersion** column, the Test Data Transfer Tool (beta) ignores the current value in the table and always exports the table by using the value 1. This feature makes it much easier to compare .out files and see only meaningful differences. This feature is especially useful when you keep your data in a version control system. Most Microsoft Dynamics AX tables contain a **RecVersion** column. |

The following table describes the export strategies that are used in the standard exclude files and the Filters.xml file.
| Content of the table                                                       | Export strategy                 | Reason                                                                                                                                                                                                                                                                                |
|----------------------------------------------------------------------------|---------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Code, system data, or user data that is not connected to the business data | Exclude this table from export. | This strategy prevents data from being unintentionally changed when business data is imported.                                                                                                                                                                                        |
| Cached values that are calculated from business data                       | Export an empty .out file.      | This strategy helps control the content of the table when the table is imported, because the content depends on business data. An .out file is required, but we do not want to store values that can be recalculated from the source data. Therefore, an empty .out file is exported. |

### 

### Export data

After you have generated the Metadata.xml file and chosen the data to export, you can export the file. The Test Data Transfer Tool (beta) does not create any temporary files during export. The Test Data Transfer Tool (beta) generates SQL statements from the content of the \[Lists\]Filters.xml file. In particular, the content of the &lt;filter&gt; element can contain arbitrary SQL statements that are executed in your user context during export. Make sure that you thoroughly test all changes to the Filters.xml file before you modify it.

### Export filtering

When you export data by using the Microsoft Dynamics AX 2012 Test Data Transfer Tool (beta), you can prevent the tool from exporting data in three ways:
-   Exclude  or include tables
-   Exclude columns
-   Exclude rows

#### Create an exclude file to exclude tables from the export

To exclude a table or a set of tables from the exported data, follow these steps.
1.  Add a text file in the \[Lists\] directory. The file name must start with **Exclude –** (the space and hyphen are part of the name), and the file name extension must be **.txt**. You can also modify an existing file.
2.  In the text file, add a line that contains a regular expression that matches the name of the table or tables to exclude from the export.

When a table is excluded, no files are created for that table during the export. The regular expression that you provide is matched against the name of the table as that name appears in the SQL Server database. Differences in capitalization are disregarded. Additionally, the Test Data Transfer Tool (beta) adds anchors to the regular expression from the exclude file to make sure that tables are excluded only if the whole name matches the regular expression. The tool uses Microsoft .NET regular expression syntax. The exclude file format lets you enter blank lines, so that you can create separate groups for expressions in a single file. The file format also lets you enter single-line comments (where the line starts with //), so that you can provide comments that describe why the tables have been excluded.
#### Examples of excluding tables from the export

To exclude only the table that is named SysVersionControlParameters, use the following regular expression.
    // Exclude 1 table
    SYSVERSIONCONTROLPARAMETERS

To exclude all tables that have names that start with SysVersionControl, use the following regular expression.
    // Exclude multiple tables
    SYSVERSIONCONTROL.*

#### Including tables in the export

Typically, you specify the data that is exported by describing the tables that you do not want to export. However, if you want to describe the tables that you do want to export, you can use a regular expression in an exclude list. Just create a regular expression that matches all tables except the tables that you want to export. The following table describes the syntax that you can include in your regular expression.
| Regular expression syntax | Description                                                                                                                                                     |
|---------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------|
| .                         | Match any single character.                                                                                                                                     |
| \*                        | Match the previous expression zero or more times.                                                                                                               |
| (?&lt;! subexpression)    | Prevent a match if the end of the previously matched content matches the subexpression. This expression is known as a zero-width negative lookbehind assertion. |
| ^                         | Match the start of the string.                                                                                                                                  |

To specify tables, first define a regular expression that starts with .\* to match all tables. Then append a zero-width negative lookbehind assertion for each table that you want to export. The subexpression in each assertion is the name of the table that is anchored to the start of the string. For example, to export only the InventTable and DocuRef tables, use the following regular expression.
    // Match all tables except InventTable and DocuRef
    .*(?<!^InventTable)(?<!^DocuRef)

For each additional table that you want to export, append (?&lt;!^NameOfTable) to the same regular expression.
#### Exclude columns from the export

To exclude a column or columns from the exported data, follow these steps.
1.  Open **\[Lists\]Filters.xml**.
2.  Add a &lt;table&gt; element that has a **name** attribute. The value of the **name** attribute is the name of the table that contains the columns to exclude.
3.  Add an &lt;exclude&gt; element in the &lt;table&gt; element.
4.  For each column that you want to exclude from the export for this table, add a &lt;field&gt; element. The content of the &lt;field&gt; element is the name of the column to exclude.

| **Note**                                                 |
|----------------------------------------------------------|
| There can be only one &lt;exclude&gt; element per table. |

#### 

#### Example of excluding columns from the export

To exclude the **BackingEntityTableId**, **BackingEntityKeyFieldId**, and **BackingEntityValueFieldId** columns when you export the **DimensionAttribute** table, include an entry such as this in Filters.xml.
      <table name="DimensionAttribute">
        <exclude>
          <field>BackingEntityTableId</field>
          <field>BackingEntityKeyFieldId</field>
          <field>BackingEntityValueFieldId</field>
        </exclude>
      </table>

#### Exclude rows from the export

To exclude rows from the exported data, follow these steps.
1.  Open \[Lists\]Filters.xml.
2.  Add a &lt;table&gt; element that has a **name** attribute. The value of the **name** attribute is the name of the table that contains the columns to exclude.
3.  Add a &lt;filter&gt; element in the &lt;table&gt; element. The content of the &lt;filter&gt; element should be an SQL statement that describes the rows to export. The &lt;filter&gt; element is like an SQL WHERE clause, but each column name should be wrapped in a &lt;field&gt; element.

There can be only one &lt;filter&gt; element per table. You can filter based on multiple columns in the table. You cannot filter based on data in other tables. Users often want to exclude all rows from the export. You can easily exclude all rows by using a filter that always evaluates to false. In the standard filters that we supply, a filter of 0 = 1 is the idiom for tables that we want to export as empty. However, when this technique is used, the Test Data Transfer Tool (beta) still creates files for the table during export, even if the .out file does not contain any data. This behavior is unlike the behavior when you exclude the whole table by using an entry in an exclude file.
#### Examples of excluding rows from the export

To export only those rows in **SysLastValue** where the **UserID** is blank, include the following entry in Filters.xml.
      <table name="SysLastValue">
        <filter><field>UserID</field> = ''</filter>
      </table>

In this case, you can imagine that the SQL query that defines the rows to export is SELECT \* FROM SysLastValue WHERE UserID = ''. To prevent all rows in SysPersonalization from being exported, include the following entry in Filters.xml.
      <table name="SysPersonalization">
        <filter>0 = 1</filter>
      </table>

In this case, you can imagine that the SQL query that defines the rows to export is SELECT \* FROM SysPersonalization WHERE 0 = 1.
Importing data
--------------

The Test Data Transfer Tool (beta) is designed to try to import all the data in the directory that you specify. The tool does not perform any filtering during import. The only exception to this rule is the **SystemSequences** table. The tool exports the **SystemSequences** table just like any other table. However, during import, the tool ignores any data that you supply for this table. Instead, the tool updates the **SystemSequences** table in the database for each table that is imported if the next **RecID** value for that table in the **SystemSequences** table is less than the maximum **RecID** in the table that is being imported. As each table is imported, the tool also makes any adjustments that are required to the other ID values that are stored in the **SystemSequences** table. You can import a table that has no rows in the .out file. You can also not import a table at all. These two operations are not the same. When you import a table that has no rows, the existing data in that table is deleted. However, if you do not import a table at all, the existing data in that table is untouched. For each table that must be imported, the tool performs the following actions:
1.  The tool searches for a table in the target database that has the same origin GUID.
    -   If such a table exists, the tool uses that table as the target of the import.
    -   If no such table exists, the tool tries to find a table in the target database that has the same name. If such a table exists, the tool uses that table as the target of the import.
    -   If no target table can be found, the table is not imported, and no error is produced.

2.  When a target table has been identified, the tool creates a new temporary version of the .out file that matches the columns in the target table.
3.  For each column in the source table, the tool first searches for the matching column in the target table by using the origin GUID of the field. If no origin-based match is found, columns are matched by using the field names.
    -   If there are columns in the source table that do not have matching columns in the target table, the data for those columns is ignored, and no error is produced.
    -   If there are columns in the target table that do not have matching columns in the source table, default values are used. In most cases, the default values are 0 (zero) or empty values that match the data type of the target column. However, if the target column is named **InstanceRelationType**, the default value is the table ID of the target table.

4.  For any column that is known to refer to a Microsoft Dynamics AX entity by the entity’s table ID, class ID, or extended data type ID, the tool updates the ID to match the ID of the same entity in the target database. The tool first maps the ID in the source data to the origin of the entity at the time of export. The tool then uses the origin of the entity to obtain the ID in the target database. If the entity cannot be found in the target system, the original ID is used, and no error is produced.
5.  During import, if data is not imported because of an index violation in a non-clustered index, the tool tries to disable the index and then retries the import. In this case, an error is reported in the log file, even if the data is successfully imported after the index was disabled.

### Import example

The following example shows how to import all files in the **Import\_March2013** directory.
    DP.exe IMPORT Import_March2013 AXTestDB

### Files used during import

This section describes the files that are used by the Test Data Transfer Tool (beta) during the import process.
#### Temporary files

The Test Data Transfer Tool (beta) can import data into tables that have many kinds of changes, such as columns that have been added, removed, or renamed. To enable this functionality, the tool writes a modified version of the .out file to a temporary location on disk and passes this file to bcp to import. Then, when the import is completed, the tool deletes the temporary file. The name of the temporary file is generated by calling **Path.GetTempPath()** and **Path.GetRandomFileName()**. Typically, the temporary files are deleted even when run-time errors occur. However, in very rare situations, such as when a power outage occurs during import, the temporary files can be written and not deleted. Because the files are written to the current user’s temporary path, this issue should not cause unexpected information disclosure. However, depending on the importance of the information that you are importing and on your organization’s data handling policies, you might have to know about this risk.

### .sql files

The Test Data Transfer Tool (beta) lets you execute arbitrary SQL statements in your user context by adding .sql files to the \[Import\] folder. Add only .sql files that come from a trusted source.

### .out files, .outmodel files, and .xml files

The Test Data Transfer Tool (beta) generates SQL statements from the names of the .out files and from the content of the other files in the directory that contains the data to import. The content that is pulled from those files and used to generate SQL statements is expected to represent table names. To prevent SQL injection attacks, the tool validates and escapes the data before that data is used to create the SQL queries. However, we still recommend that you accept data only from trusted sources.

## Run SQL scripts after import
The Test Data Transfer Tool (beta) lets you run SQL scripts after you complete the import. Any modifications that you have to make to imported data can be completed by using the SQL scripts. Before you complete your data import, write the SQL script, and then save the file as an .sql file in the \[Import\] subfolder in the same location as the tool. When the import is completed, the tool automatically runs the SQL script file that you have stored in the \[Import\] folder.



