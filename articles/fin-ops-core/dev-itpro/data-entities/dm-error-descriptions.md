---
# required metadata

title: Data management error descriptions
description: This article describes the error messages that you might encounter in data management.
author: peakerbl
ms.date: 01/08/2024
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: peakerbl
ms.search.validFrom: 2018-09-15
ms.dyn365.ops.version: Platform update 20

---

# Data management error descriptions

[!include [banner](../includes/banner.md)]


[!INCLUDE [PEAP](../../../includes/peap-3.md)]

This article documents the scenarios when a specific error will be seen. These scenarios aren't a complete list of errors and scenarios, however this list will be continuously updated so keep checking back for updates. Any feedback on this page with regards to specific errors that should be covered are welcome.

This article describes the error messages that you might encounter in data management.

## Import to target failed due to an update conflict as more than one process is trying to update the same record at the same time

When you use recurring imports (enqueue API), if the files are sent to the end point at high frequency and the sequential processing of messages isn't enabled, data management will try to process the files in parallel. When files are processed in parallel, and multiple files have the same record, multiple threads will try to update the same record at the same time. If this is a data issue, you must update the data so that the same records don’t repeat across files. If this is not a data issue and the entity is expected to handle such cases, this might be a bug. For bugs, to mitigate the issue, you can choose to sequentially process the files. If this is not a data issue and the entity is not expected to process in parallel, then this entity must not be subjected to parallel processing. You should enable sequential processing of messages in the recurring job.

## There are field(s) which are not mapped to Entity \<EntityName\>

It is a common practice to use the export functionality to generate the entity template file that can be later used for imports. However, while exporting the template, in fixed width format with 'First row header' set to 'No' (in source data formats set up), the exported template will not have the column names. When this file is imported, it will result in this error. 

## Data package download - Error downloading data package for job ''. Record for ID - {GUID} not found

One of the scenarios where this error can happen is when the environment, such as the dev environment, points to the database in another environment, such as UAT, and the export job is run from the source environment. which is dev in this example. The exported file gets uploaded to the blob storage that is associated with the source environment (dev, in this example). However, this job will also show up in the target environment (UAT) since the database is shared. If you try to download the exported file using the **Download file** option, this error will display because the file does not exist in the blob storage of the target environment (UAT) from where you are trying to download.

## XML is not in correct format-Exception from HRESULT: 0xC0010009

This message covers all XML formatting issues in the file. For example, the data project has mappings for columns that do not exist in the file that is being used for the operation. This error can happen if certain columns were removed from the file and this file is now used. Either fix the mapping in the data project or fix the file to have all the columns as expected.

## Error while uploading a file during export

When running an export on a development environment, an error could occur relating to not being able to upload the export file. This could occur if Azure Storage Emulator is not available or an older version of the emulator is installed. To resolve this issue, install the latest emulator, restart the virtual machine (VM), and rerun the export job. The storage emulator can be installed from [Azure Storage Emulator](/azure/storage/common/storage-use-emulator).

## Error codes 

|Error code	|Possible cause	|Possible resolution|
|DMF021|	AddColumnsToFullDataDerivedComponent failure raised when the enum value mappings are missing. The possible values for the enum can't be determined.|Remove enum columns from the mapping. If the error continues, contact support to determine which column is involved. Remove the affected enumeration column from mapping.|
|DMF023|	Error adding database connection. Your bring your own database is unreachable or the source database is unreachable due to patching/deployment.|	Verify bring your own database connection string and retry later.|
|DMF030|	Error adding or updating OLEDB source properties. This could be due to incorrect field mapping.|	Sometimes, the problematic fields can be identified by removing all fields from the mapping except key columns and doing an export job. If export was successful, add back other fields a few at a time and repeat until you find the problematic field. Don't map any virtual fields if you selected skip staging. Entities with duplicate labels may cause this error. Only one entity can be assigned a particular label as the entity name, if you have more than one entity using the same label it will cause an error.|
|DMF040|	Excel query failed. The system can't retrieve the column names or the worksheet name. The system should automatically restart any Data management instances that raises this error frequently.|	Consider changing the file type for the import project to something other than Excel. |
|DMF042	|The Data management service is unreachable. This is can be due to patching or deployment in progress.	|This is usually a transient failure. Try the import/export job again. If the error occurs consistently, contact support.|
|DMF043	|Package execution has failed. This is a general error when the error pattern doesn't match a known error code.	|Check the execution details for the particular execution ID for the specific error message. Depending on the problem, you may need to contact support.|
|DMF045	|Error executing SSIS package.|	Check the execution details for the execution ID that failed. If the information in the error log is insufficient, contact support.|
|DMF1830	|Xml is not in correct format.|	Verify your import file is of type XML and not empty. For composite entities, ensure that you have all the elements for each of the entities in the composite entity. You can't leave out a child entity.|
|DMF1855	|File type doesn't match project.	|The import file needs to be the type set in the project. Use the type set for the project or change the file type set in the project.|
|DMF1957|	Can't export unicode data as an ascii file type. The entity contains data that's not allowed in ascii files.|	Change the file type on the export project to one of the file types that supports unicode characters. Use XML or any of the file types ending with -Unicode.|
|DMF1959|	PrimaryKeyViolationErrorCode. When importing, there are multiple rows having the same key column values. When exporting, the columns used for the staging table index don't form a key for the entity.|	For import, check the execution details from the failed import to find the key column values involved. Remove the duplicate row and then try the import again. For export, if this is a custom entity, validate the staging table index forms a key for your entity. Modify the entity key and staging index or modify the entity view to not return duplicate rows. To check the key, on the UAT environment query for row counts from your SQL entity view groupedby your staging table index columns(omit the executionid and definition group). If you have a set of key column values with row count > 1 then the key is not unique.|
|DMF1961	|Invalid composite entity relation.|For custom entity, ensure the entity relationships are correctly modeled and the data for the relation fields in the import file is the correct data type.|
|DMF1963	|Composite entity import file isn't in XML format. Only XML files can be used for composite entity import. Verify the import file isn't empty and is in XML format.|
|DMF1965|	Upload to azure storage failed due to long running queries.|	For entities with slow performance, consider exporting to database.|
|DMF1966	|There's a mismatch in the mapped columns and uploaded file. This error displays when an import file doesn't contain any of the mapped fields for the entity.	|Having more than one entity that has the same value for it's label property will cause this error. After an entity refresh, the label can get assigned to the conflicting entity. This results in a project with mapping for one entity but the entity query is now for a different entity. If the entity is custom, reset the label property for the entity to a new value that isn't already used by an existing entity. Redeploy the custom entity.|
|DMF1968|	Database not found.| Any failed import/export with this error will automatically retry. For this error on export to BYOD, verify the BYOD connection string.|
|DMF1969|	SSIS package execution threw an exception.|	Check the execution log of the job for more information and resolution. If there's no information, contact support.|
|DMF1970|	Truncate entity command timed out. |	Full export to database error took more than 10 minutes to remove existing data for the company. Confirm that there no processes are running on the destination table during the export. Increase the command timeout on the BYOD tab of the framework parameters page.|
|DMF1973|	Publish entity failed.|	Check details in the error/execution log. If there's insufficient information, contact support.|
|DMF1987	|This can be caused by: 
1: Failure due to a table mapping problem. 2: Adding a new field/column without republishing the entity. |1: The problematic field can be identified by removing all fields from the mapping except key columns and doing an export. If this is successful, incrementally add a few columns at a time and re-export until you find the problematic column. 2: After deploying changes, refresh the entity list and republish the entity.|
|DMF1995|	Sql login timed out. Imports or exports with this error automatically retry.	|For database export, consider specifying a longer than default connection timeout on the connection string. Default timeout is 30 seconds. The value can be set in the connection string to be longer.|
|DMF1996	|Deadlock. This means there are concurrent imports for the same project interfering with each other. |	If using auto generated numbers for import, keep the file size low to avoid locking the staging table. If seeing this consistently for a data project, adjust the scheduling of the project to avoid concurrent execution.|
|DMF1997|	AcquireConnectionsError. SSIS was unable to connect to the database. Imports or exports with this error automatically retry.	|For database export, confirm the BYOD(Bring your own database) connection string still works and try again. If seeing this error frequently, contact support.|
|DMF1999	|Column delimiter not found.|	Don't change the delimiter character for the built in file types. Specifically, don't change the CSV-Unicode as integration with Dataverse depends on that file type. If using a new delimiter, add a new file type record in the source name list, and set the delimiter on the new record.|
|DMF2003|	Sql command timed out.|	Adjust the command timeout on the **Framework parameters** page, on the **BYOD** tab. It's applied to all service commands and not just for BYOD (Bring your own database).|
|DMF2006	|BYODMappingErrorCode. One or more fields in the export command don't exist in the BYOD(Bring your own database) table. The data entity could have been modified since the last time it was published.	|Republish the entity to your BYOD(Bring your own database).|
|DMF2008	|AcquireConnectionFailed. Failed to connect to the destination database. |	Any export or import with this error automatically retries. For an export to database, verify the BYOD(Bring your own database) connection string is still valid and that the SQL user for the connection string still has rights to log into the database. If the import or export didn't automatically rerun successfully, run again.|
|DMF2009	|Excel column limit exceeded. Can't export more than 255 columns to an Excel file.	|Known SSIS limitation. Pick a different file type or modify the mapping to reduce the number of columns to export.|
|DMF2010|	Destination database out of space.|	Upgrade to a higher tier for the BYOD(Bring your own database) or remove some data to free up space.|
|DMF2016	|Invalid data time value.|	Correct the invalid value in the import file.|
|DMF2017	|Error reading package executor results.|	View the execution details for logs. If there's not enough informatio, contact support.|
|DMF2018|	Column has invalid data.|	1: Check the execution log for any details of which column had the error. 2: Check the import file data. Tips: Too many or too few values per row. Long strings that might overflow a column length limit. Data values inappropriate for the data type ie. alphabet characters in a numeric field.|
|DMF2022|	ElementNotFoundInCollection. There's a mismatch between the mapped fields list and the columns for the import file or the columns returned by the entity query.|	For import, check all the fields in your import file are in the mapping and vice versa. For export, try removing all fields from the map except key columns and retry export. If successful, add back fields a few at a time and re-export until you find the problematic field. Including a virtual field in mapping and skipping staging can cause this error for an export.|
|DMF2025|	InvalidColumnErrorCode. Import fails due to a column not found in the input file.|	1 - Verify that there's a mapping record for every field in the import file and a column in the import file for every mapped field. 2 - Concurrent ImportFromPackate or ExportToPackage api calls for the same project aren't supported unless the **Enhanced parallel package import** option is selected on the **Framework parameters** page.|
|DMF2028|	DBUnavailabilityErrorCode. The database was unreachable.|	Any import or export with this error should retry. If the retry isn't successfully, run the job again.|
|DMF2033	|Failed to delete duplicate data from the BYOD(Bring your own database) due to missing column(s).	|Remove the corresponding fields from the entity mapping and/or publish the entity again.|
|DMF2035|	Transaction log full.	|If this happens for import or file export, contact support to get the database log size reduced. For export to BYOD(Bring your own database), reduce your database log size.|
|DMF2036|	Bulk copy aborted by a schema change.	| The staging table index was rebuilt while the import job was running. Reschedule/retry the import.|
|DMF2037	|Destination database unreachable.| Transient issue. Try the job again and verify the connection string.|
|DMF2039|	Unable to obtain Excel file lock. |	There can only be one import or export to Excel at any time. Stagger the import/export to not cause contention for the Excel file lock. Or use a different file type other than Excel for your project. Other filetypes can be processed in parallel.|
|DMF2040	|BYODDatabaseIsFullErrorCode. Your BYOD(Bring your own database) has reached it's size quota.	|Increase the db tier for your destination database. Delete/remove data from the database.|
|DMF2042|	Spreadsheet is full. |	Data set has too many rows to be saved as an excel file. Pick a different file type or add a filter on the export project so that it exports fewer rows.|
|DMF2043|	Destination database unreachable.	|Transient issue and retry the operation. If this is a BYOD(Bring your own database), verify the connection string is valid and the user specified in the connection string still has permissions.|
|DMF2044|	System resources exceeded.	|If this is a custom entity, verify that the entity doesn't require large amounts of temp db storage or memory to run. Verify that entity design isn't missing ranges on joins and there are no joins inside computed column formulas. |
|DMF2045|	Call to the Data management service failed.|	Retry the operation. If seeing this consistently, check the execution log for more information or contact support.|
|DMF2048	|Data import and export service unreachable. Any import/export with this failure should automatically retry.	|Retry the operation. If seeing this consistently, check the execution log for more information or contact support.|
|DMF2050	|Error skipping data rows. File format error.	|For files that are not XML, confirm the header row is present and there aren't any unterminated rows or columns in the file. Remove blank lines and verify the same number of column values is present on every row.|
|DMF2051|	Publish entity failed due to CCI index not supported on the database tier.	|CCI index isn't allowed on some smaller azure database sizes. Turn off the use CCI index option where the connection string is entered, or use a higher DB tier. If use CCI is OFF, the staging table index will be used for the destination table key.|
|DMF2052	|Validation exception. 	|Check the execution log for details and verify column mapping.|
|DMF2053	|Import file empty.|	At least one data row is required to do an import.|
|DMF2054|	BYODTableDoesNotExistOrDoNotHavePermissionErrorCode. 	|Destination table isn't present or the login user doesn't have rights to the table. Check if the destination table exists in the BYOD(Bring your own database), if not publish the entity. Confirm if the SQL login account used for BYOD(Bring your own database) connection string has rights to write to the table.|
|DMF2055|	InvalidXMLCharacterErrorCode. |	Control characters other than tab, aren't allowed in xml files. If exporting data contains a control character like backspace, the export will fail.
Remove any control characters from the data or use a different file type for the export. The memo field usually has these values where the data was originally set from email or other automated process. Backspace is the most common character causing these error.|
|DMF2057|	Unique key constraint violation.	|For export jobs, the entity key isn't unique. Update the entity key and staging index and redeploy your changes. For import jobs, there are rows having duplicate key values in the import file. Remove duplicate values.|
|DMF2060	|Mapped field isn't present in the import file or staging table.	|Remove the unused field from the mapping or include it in the import file. When customizing an entity, fields need to be added to both the entity view and it's staging table.|
|DMF2061|	Destination table is missing expected columns.|	Republish the entity.|
|FF004|	Header row is missing.	|File imports not using xml are expected to have a row listing the column names. If that row is missing, or if there's a blank line at start of the file, this error is displayed. The header row determines which values belongs to their respective columns. Add the missing header row to the import file and remove any blank lines.|
|MAP011|	Xml node not found.	|This occurs during composite entity import. You must have an element for every entity in the composite entity. Check your import file. You need xml element for every entity that makes up your composite entity. If there is an missing entity, add an element for it to the import file.  Data rows can be empty, but the element for the entity is required in the file.|



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
