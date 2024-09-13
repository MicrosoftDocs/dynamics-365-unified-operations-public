---
title: Data management error descriptions and known limitations
description: Learn about the error messages that you might encounter in data management, including a table that outlines possible causes of various errors.
author: pnghub
ms.author: gned
ms.topic: conceptual
ms.custom: 
  - bap-template
ms.date: 05/14/2024
ms.reviewer: twheeloc
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2018-09-15
ms.search.form: 
ms.dyn365.ops.version: Platform update 20
---

# Data management error descriptions and known limitations

[!include [banner](../includes/banner.md)]

This article documents the scenarios where specific errors are seen. It doesn't provide a complete list of errors and scenarios. However, keep checking back, because the list is continuously updated.

## Import to target failed due to an update conflict as more than one process is trying to update the same record at the same time

When you use recurring imports (enqueue API), the files are sent to the endpoint at a high frequency. If sequential processing of messages isn't enabled, data management tries to process the files in parallel. When files are processed in parallel, if multiple files have the same record, multiple threads try to update the same record at the same time. You must update the data so that the same records aren't repeated across multiple files. The entity is expected to handle cases where each record occurs in only one file. To mitigate the issue, sequentially process the files. If this issue isn't a data issue, and the entity isn't expected to process in parallel, the entity isn't subject to parallel processing. Enable sequential processing of messages in the recurring job.

## There are fields, which are not mapped to Entity \<EntityName\>

It's a common practice to use the export functionality to generate the entity template file that can be used later for imports. If you export the template in fixed-width format where the **First row header** option is set to **No** in the source data format setup, the exported template doesn't have the column names. Then, when the file is imported, this error occurs. 

## Data package download - Error downloading data package for job ''. Record for ID - \{GUID\} not found

In one scenario, the dev environment points to the database in another environment (for example, the UAT environment), and the export job is run from the source environment (dev). The exported file is uploaded to the blob storage that's associated with the source environment (dev). This job shows up in the target environment (UAT) because the database is shared. If you try to download the exported file by using the **Download file** option, you receive this error because the file doesn't exist in the blob storage of the target environment (UAT) that you're trying to download from.

## XML is not in correct format-Exception from HRESULT: 0xC0010009

This message covers all XML formatting issues in the file. For example, the data project has mappings for columns that don't exist in the file that's used for the operation. This error occurs if some columns were previously removed from the file, and the file is now used. Either fix the mapping in the data project, or fix the file so that it has all the expected columns.

## Error while uploading a file during export

When you run an export in a development environment, an error occurs if the export file can't be uploaded. To fix this issue, install the latest Microsoft Azure Storage emulator, restart the virtual machine (VM), and rerun the export job. You can install the storage emulator from [Azure Storage Emulator](/azure/storage/common/storage-use-emulator). We currently support an export file size of up to 256 MB. To increase this limit to 5,000 MB, update the 'AzureStorageServiceVersion' field to '2019-12-12' in the DMFPARAMETERS table. To ensure the file size stays within the 5,000 MB limit, apply filters directly from the export project form to reduce the number of records being exported.

## Error codes

| Error code | Possible cause | Possible resolution |
|---|---|---|
| DMF021 | An `AddColumnsToFullDataDerivedComponent` failure is raised if the enumeration (enum) value mappings are missing. The possible values for the enum can't be determined. | Remove the affected enum column from the mapping. If the error continues, contact Support to determine which column is involved. |
| DMF023 | An error occurred when the database connection was added. Your bring your own database (BYOD) is unreachable, or the source database is unreachable because of patching/deployment. | Verify the BYOD connection string, and retry later. |
| DMF030 | An error occurred when OLEDB source properties were added or updated, because of incorrect field mapping. | To identify the problematic fields, remove all fields from the mapping, except key columns, and then do an export. If the export is successful, add back a few fields at a time until you find the problematic field. Don't map any virtual fields if you chose to skip staging. Entities that have duplicate labels might cause this error. Only one entity can be assigned a particular label as the entity name. If more than one entity uses the same label, an error occurs. |
| DMF040 | The Excel query failed. The system can't retrieve the column names or the worksheet name. The system automatically restarts any Data management instances that frequently raise this error. | Consider changing the file type of the import project to something other than Excel. |
| DMF042 | The Data management service is unreachable. This issue can occur because patching or deployment is in progress. | This issue is usually a transient failure. Try the import/export job again. If the error consistently occurs, contact Support. |
| DMF043 | Package execution failed, and the error pattern doesn't match a known error code. | Review the execution details for the execution ID for the specific error message. Depending on the issue, you might have to contact Support. |
| DMF045 | An error occurred when the SQL Server Integration Services (SSIS) package was run. | Review the execution details for the execution ID that failed. If the information in the error log is insufficient, contact Support. |
| DMF1830 | The XML isn't in the correct format. | Confirm that your import file is of the XML type, and that it isn't empty. For composite entities, ensure that you have all the elements for each entity in the composite entity. You can't leave out a child entity. |
| DMF1855 | The file type doesn't match the project. | The import file must be of the type that's set in the project. Use the file type that's set in the project, or change the file type that's set in the project. |
| DMF1957 | Unicode data can't be exported as an ASCII file type. The entity contains data that isn't allowed in ASCII files. | Change the file type of the export project to one of the file types that support Unicode characters. Use XML or any file type that ends with **-Unicode**. |
| DMF1959 | A `PrimaryKeyViolationErrorCode` error occurred. For an import, this error indicates that multiple rows have the same key column values. For an export, it indicates that the columns that are used for the staging table index don't form a key for the entity. | For an import, review the execution details of the failed import to find the key column values that are involved. Remove the duplicate row, and then try the import again. For an export, if the entity is a custom entity, validate that the staging table index forms a key for that entity. Modify either the entity key and staging index or the entity view so that there aren't duplicate rows. To check the key, in the UAT environment, query for row counts from your SQL entity view grouped by your staging table index columns. (Omit the execution ID and definition group.) If you have a set of key column values where the row count is more than 1, the key isn't unique. |
| DMF1961 | The composite entity relation isn't valid. | For a custom entity, ensure that the entity relationships are correctly modeled, and that the data for the relation fields in the import file is of the correct data type. |
| DMF1963 | The composite entity import file isn't in XML format. Only XML files are used for composite entity import. | Confirm that the import file isn't empty, and that it's in XML format. |
| DMF1965 | Upload to Azure Storage failed because of long-running queries. | For entities that have slow performance, consider exporting to the database. |
| DMF1966 | There's a mismatch in the mapped columns and the uploaded file. This error is shown when an import file doesn't contain the mapped fields for the entity. | This error occurs because more than one entity has the same value for the label property. After an entity refresh, the label can be assigned to the conflicting entity. As a result, a project has a mapping for one entity, but the entity query is now for a different entity. If the entity is a custom entity, reset the label property for it to a new value that isn't already used by an existing entity. Redeploy the custom entity. |
| DMF1968 | The database wasn't found. | Any failed import/export that has this error is automatically retried. If this error occurs during an export to the BYOD, verify the BYOD connection string. |
| DMF1969 | SSIS package execution threw an exception. | Review the execution log of the job for more information and a resolution. If there's no information, contact Support. |
| DMF1970 | The **Truncate entity** command timed out. | The full export to database error took more than 10 minutes to remove existing data for the company. Confirm that no processes are running on the destination table during the export. Increase the command time-out on the **BYOD** tab of the **Framework parameters** page. |
| DMF1973 | Publishing of the entity failed. | Review the details in the error/execution log. If there's insufficient information in the log, contact Support. |
| DMF1987 | <p>This error can have two causes:</p><ol><li>A failure occurred because of a table mapping issue.</li><li>A new field/column was added without republishing the entity.</li></ol> | <ol><li>To identify the problematic field, remove all fields from the mapping, except key columns, and then do an export. If the export is successful, incrementally add a few columns at a time and re-export until you find the problematic column.</li><li>After you deploy changes, refresh the entity list, and republish the entity.</li></ol> |
| DMF1995 | SQL login timed out. Imports or exports that have this error are automatically retried. | For a database export, set the connection time-out on the connection string so that it's longer than default time-out (30 seconds). |
| DMF1996 | A deadlock occurred. Concurrent imports for the same project are interfering with each other. | If you're using automatically generated numbers for the import, keep the file size low to prevent the staging table from being locked. If the error consistently occurs for a data project, adjust the scheduling of the project to prevent concurrent execution. |
| DMF1997 | An `AcquireConnectionsError` error occurred. SSIS was unable to connect to the database. Imports or exports that have this error are automatically retried. | For a database export, confirm that the BYOD connection string still works, and try again. If this error frequently occurs, contact Support. |
| DMF1999 | The column delimiter wasn't found. | Don't change the delimiter character for the built-in file types. Specifically, don't change it for **CSV-Unicode**, because integration with Dataverse depends on that file type. If you're using a new delimiter, add a new file type record in the source name list, and set the delimiter on the new record. |
| DMF2003 | The SQL command timed out. | Adjust the command time-out on the **BYOD** tab of the **Framework parameters** page. This time-out applies to all service commands, not just commands for the BYOD. |
| DMF2006 | A `BYODMappingErrorCode` error occurred. One or more fields in the export command don't exist in the BYOD table. The data entity might have been modified since the last time that it was published. | Republish the entity to your BYOD. |
| DMF2008 | An `AcquireConnectionFailed` error occurred because of a failure to connect to the destination database. | Any export or import that has this error is automatically retried. For an export to database, confirm that the BYOD connection string is still valid, and that the SQL user for the connection string still has rights to sign in to the database. If the import or export didn't automatically rerun successfully, run it again. |
| DMF2009 | The Excel column limit was exceeded. You can't export more than 255 columns to an Excel file. | This issue is a known SSIS limitation. Select a different file type, or modify the mapping to reduce the number of columns that are exported. |
| DMF2010 | The destination database is out of space. | Upgrade to a higher tier for the BYOD, or remove some data to free up space. |
| DMF2016 | A data/time value isn't valid. | Correct the invalid value in the import file. |
| DMF2017 | An error occurred when the package executor results were read. | View the execution details for logs. If the information in the log is insufficient, contact Support. |
| DMF2018 | A column has invalid data. | <ol><li>Review the execution log for details about which column had the error.</li><li><p>Review the import file data.</p><p><strong>Tip:</strong> Here are some specific things to look for:</p><ul><li>Too many or too few values per row</li><li>Long strings that might overflow a column's length limit</li><li>Data values that are inappropriate for the data type (for example, alphabetic characters in a numeric field)</li></ul></li></ol> |
| DMF2022 | An `ElementNotFoundInCollection` error occurred. There's a mismatch between the mapped field list and the columns for the import file or the columns that the entity query returned. | For an import, confirm that all the fields in your import file are present in the mapping, and that all the fields in the mapping are present in your import file. For an export, try to remove all fields from the map, except key columns, and then retry the export. If the export is successful, add back a few fields at a time and re-export until you find the problematic field. For an export, this error can occur if you include a virtual field in the mapping and skip staging. |
| DMF2025 | An `InvalidColumnErrorCode` error occurred. Import failed because a column wasn't found in the input file. | <ol><li>Confirm that there's a mapping record for every field in the import file and a column in the import file for every mapped field.</li><li>Concurrent ImportFromPackage or ExportToPackage API calls for the same project aren't supported unless the **Enhanced parallel package import** option is selected on the **Framework parameters** page.</li></ol> |
| DMF2028 | An `DBUnavailabilityErrorCode` error occurred. The database was unreachable. | Any import or export that has this error should be retried. If the retry isn't successful, run the job again. |
| DMF2033 | Deletion of duplicate data from the BYOD failed because of missing columns. | Remove the corresponding fields from the entity mapping, and/or publish the entity again. |
| DMF2035 | The transaction log is full. | If this issue occurs for an import or file export, contact Support to have the size of the database log reduced. For an export to BYOD, reduce the size of your database log. |
| DMF2036 | Bulk copy was aborted by a schema change. | The staging table index was rebuilt while the import job was running. Reschedule/retry the import. |
| DMF2037 | The destination database was unreachable. | This issue is transient. Try the job again, and verify the connection string. |
| DMF2039 | An Excel file lock couldn't be obtained. | There can be only one import or export to Excel at any time. Stagger the imports/exports to avoid causing contention for the Excel file lock. Alternatively, use a file type other than Excel for your project. Other file types can be processed in parallel. |
| DMF2040 | A `BYODDatabaseIsFullErrorCode` error occurred. Your BYOD has reached its size quota. | Increase the database tier for your destination database. Delete/remove data from the database. |
| DMF2042 | The worksheet is full. | The dataset can't be saved as an Excel file because it has too many rows. Select a different file type, or add a filter on the export project so that it exports fewer rows. |
| DMF2043 | The destination database was unreachable. | This issue is transient. Retry the operation. If the database is a BYOD, confirm that the connection string is valid, and that the user that's specified in the connection string still has permissions. |
| DMF2044 | System resources were exceeded. | If the entity is a custom entity, confirm that it doesn't require large amounts of temporary database storage or memory to run. Confirm that that entity design isn't missing ranges on joins, and that there are no joins inside computed column formulas. |
| DMF2045 | The call to the Data management service failed. | Retry the operation. If you consistently encounter this issue, review the execution log for more information, or contact Support. |
| DMF2048 | The Data import and export service was unreachable. Any import/export that has this failure should automatically be retried. | Retry the operation. If you consistently encounter this issue, review the execution log for more information, or contact Support. |
| DMF2050 | Data rows were skipped. The issue is a file format error. | For files that aren't in XML format, confirm that the header row is present, and that there aren't any unterminated rows or columns in the file. Remove blank lines, and confirm that every row has the same number of column values. |
| DMF2051 | Publishing of the entity failed because a clustered columnstore index (CCI) isn't supported on the database tier. | A CCI index isn't allowed on some smaller Azure database sizes. Turn off the **Use CCI** option where the connection string is entered, or use a higher database tier. When the **Use CCI** option is turned off, the staging table index is used for the destination table key. |
| DMF2052 | A validation exception occurred. | Review the execution log for details, and verify the column mapping. |
| DMF2053 | The import file is empty. | At least one data row is required to do an import. |
| DMF2054 | A `BYODTableDoesNotExistOrDoNotHavePermissionErrorCode` error occurred. | The destination table isn't present, or the signed-in user doesn't have rights to the table. Confirm that the destination table exists in the BYOD. If it doesn't, publish the entity. Confirm that the SQL login account that's used for the BYOD connection string has rights to write to the table. |
| DMF2055 | An `InvalidXMLCharacterErrorCode` error occurred. | No control characters except tabs are allowed in XML files. If the exporting data contains control characters such as backspaces, the export fails. Remove any control characters from the data, or use a different file type for the export. The `memo` field usually has these control characters when the data was originally set from email or another automated process. A backspace is the most common character that causes this error. |
| DMF2057 | A unique key constraint violation occurred. | For export jobs, the entity key isn't unique. Update the entity key and staging index, and redeploy your changes. For import jobs, there are rows that have duplicate key values in the import file. Remove the duplicate values. |
| DMF2060 | A mapped field isn't present in the import file or staging table. | Remove the unused field from the mapping, or include it in the import file. When you customize an entity, you must add fields to both the entity view and its staging table. |
| DMF2061 | The destination table is missing expected columns. | Republish the entity. |
| FF004 | The header row is missing. | File imports that don't use XML are expected to have a row that lists the column names. If that row is missing, or if there's a blank line at start of the file, this error is shown. The header row determines which values belong to each column. Add the missing header row to the import file, and remove any blank lines. |
| MAP011 | An XML node wasn't found. | This issue occurs during import of a composite entity. You must have an element for every entity in the composite entity. Review your import file. You need an XML element for every entity that makes up your composite entity. If an entity is missing, add an element for it in the import file. Data rows can be empty, but the element for the entity is required in the file. |

### Known limitations

Data management (DMF/DIXF) export to Excel has a 255-character limit.

- The Data management (DMF) export job truncates data that has the Excel file type if there are more than 255 characters.
- This limitation is a known SSIS limitation. Data that has more than 255 characters is truncated when you export to the Excel file type. For more information, see [Export long text values](/sql/integration-services/load-data-to-from-excel-with-ssis#export-long-text-values).
- To export data by using the Data management (DMF) export job, use a different file type.


> [!NOTE]
> When doing Data management export to file and downloading to file, an extra period(.) will be appended to the end of file name.
> 
[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
