---
title: Data management overview
description: Learn about data management in finance and operations, including overviews of data entities and data migrations. 
author: twheeloc
ms.author: twheeloc
ms.topic: overview
ms.custom: 
  - bap-template
ms.date: 01/14/2026
ms.reviewer: twheeloc
ms.collection: get-started
ms.assetid: e67f5edc-1087-4867-8955-b2a40d94217f
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
---

# Data management overview

[!include [banner](../includes/banner.md)]

This article describes how you can use the data management framework to manage data entities and data entity packages in finance and operations.

The data management framework consists of the following concepts:

- **Data entities** - A data entity is a conceptual abstraction and encapsulation of one or more underlying tables. A data entity represents a common data concept or functionality, such as Customers or Vendors. Users familiar with business concepts can easily understand data entities. After you create data entities, you can reuse them through the Excel Add-in, use them to define import/export packages, or use them for integrations.
- **Data project** - A project that contains configured data entities, which include mapping and default processing options.
- **Data job** - A job that contains an execution instance of the data project, uploaded files, schedule (recurrence), and processing options.
- **Job history** - Histories of source to staging and staging to target jobs.
- **Data package** - A single compressed file that contains a data project manifest and data files. This package is generated from a data job and used for import or export of multiple files with the manifest.

The data management framework supports using data entities in the following core data management scenarios:

- Data migration
- Set up and copy configurations
- Integration

## Data entities

Data entities provide conceptual abstraction and encapsulation of the underlying table schema that represent data concepts and functionalities. In Microsoft Dynamics AX 2012, most tables, like the Customer and Vendor tables, were de-normalized and split into multiple tables. This design was beneficial from a database design point of view, but it made it difficult for implementers and ISVs to use without a thorough understanding of the physical schema. Data management introduces data entities as a layer of abstraction that uses business concepts to make the schema easier to understand. In previous versions, there were multiple ways to manage data, such as Microsoft Excel Add-ins, AIF, and DIXF. The concept of data entities combines those different concepts into one. After you create data entities, you can reuse them for Excel Add-ins, import/export, or integration. The following table shows core data management scenarios.

| Scenario | Description |
|----------|-------------|
| **Data Migration** | <ul><li>Migrate reference, master, and document data from legacy or external systems.</li></ul> |
| **Set up and copy configuration** | <ul><li>Copy configuration between company/environments.</li><li>Configure processes or modules using the Lifecycle Services (LCS) environment.</li></ul> |
| **Integration** | <ul><li>Real-time service based integration.</li><li>Asynchronous integration.</li></ul> |

## Data migration

By using the data management framework, you can quickly migrate reference, master, and document data from legacy or external systems. The framework is designed to help you quickly migrate data by using the following features:

- Select only the entities you need to migrate.
- If an import error occurs, skip selected records and choose to proceed with the import by using only the good data. You can fix and import the bad data later. You can partially continue and use errors to quickly find bad data.
- Move data entities straight from one system to another, without having to go through Excel or XML.
- Easily schedule data imports by using a batch, which offers flexibility when it's required to run. For example, you can migrate customer groups, customers, vendors, and other data entities in the system at any time.

## Set up and copy configuration

Use the data management framework to copy configurations between companies or environments, and configure processes or modules by using Microsoft Dynamics Lifecycle Services (LCS).

Copying configurations makes it easier to start a new implementation, even if your team doesn't deeply understand the structure of data that needs to be entered, data dependencies, or which sequence to add data to an implementation.

The data management framework allows you to:

- Move data between two similar systems.
- Discover entities and dependencies between entities for a given business process or module.
- Maintain a reusable library of data templates and datasets.
- Use data packages to create incremental data entities. Data entities can be sequenced inside the packages. You can name data packages, which can be easily identifiable during import or export. When you build data packages, map data entities to staging tables in grids or by using a visual mapping tool. You can also drag-and-drop columns manually.
- View data during imports, so you can compare data and ensure that it's valid.

## Working with data entities

The following sections provide quick snapshots of the different functionalities of data management by using data entities. The goal is to help you strategize and make effective decisions on how to best utilize the available tools during data migration. You also find tips and tricks on how to effectively use each area during data migration. A list of available data entities for each area can also be found with the suggested data sequences, showing data dependencies. Microsoft provides data packages that can be found on Lifecycle Services (LCS) as an initial guide. The information in this document can be used as a guide for creating your own packages. The description of each data entity shows what the object contains and if it's needed during data migration.

### Sequencing

When you work with data entities, consider two types of sequencing:

- Sequencing data entities within a data package
- Sequencing the order of data package imports

#### Sequence data entities within a data package

1. When you add data entities to a data project, you set a sequence for the order in which the entities load. The first entity you add to the project is the first entity to load, the next entity is second, the next entity is third, and so on.

    For example, if you add two entities in this order, **Sales tax codes** and **Sales Tax groups**, then **Sales tax codes** gets an entity sequence of **1.1.1**, and **Sales tax groups** gets an entity sequence of **1.1.2**. The sequence level indicates that the second entity doesn't start the import process until the first level finishes.

1. To view or edit a sequence, select the **Entity sequence** button on the Action Pane of the data project.

    :::image type="content" source="./media/dataentitiesdatapackages01.png" alt-text="Screenshot of entity sequence.":::

1. In the Definition group entity sequence, you can see the execution units and the sequence. You can change sequence by selecting the data entity in the list, setting a different Execution unit or Sequence in level, and then selecting **Update selected**. After selecting **Update selected**, the entity moves up or down in the entity list.

**Example**

The following screenshot shows the entity sequence that is set for the Sales Tax CodeGroups data package.

:::image type="content" source="./media/dataentitiesdatapackages02.png" alt-text="Screenshot of Sales Tax CodeGroups data package sequence.":::

To successfully import sales tax codes and groups, the process loads the sales tax codes and details first, before it imports sales tax groups. Sales tax codes and groups are all in Execution unit = 1, but the sequences are in the order that they import. The package includes other related sales tax entities that aren't dependent upon other data entities being loaded. For example, sales tax exempt numbers are set in its own Execution unit = 2. This data entity starts loading immediately because there are no dependencies on other entities loading before it.

#### Sequence data package imports

To successfully load data, set the correct order for importing data packages. Dependencies exist within and across modules. The numbering format that the system uses for the data packages within LCS are as follows:

- First segment: Module
- Second segment: Data type (setup, master, transaction)
- Third segment: Sequence number

The following tables provide more information about the default numbering format.

**Module numbers**

:::image type="content" source="./media/dataentitiesdatapackages03.png" alt-text="Screenshot of module area numbers." lightbox="./media/dataentitiesdatapackages03.png":::

**Data type numbers**

:::image type="content" source="./media/dataentitiesdatapackages04.png" alt-text="Screenshot of data type numbers." lightbox="./media/dataentitiesdatapackages04.png":::

**Sequence number**

:::image type="content" source="./media/dataentitiesdatapackages05.png" alt-text="Screenshot of sequence number." lightbox="./media/dataentitiesdatapackages05.png":::

Data packages follow the sequence number, followed by the module abbreviation, and then a description. The following example shows General ledger data packages.

:::image type="content" source="./media/dataentitiesdatapackages06.png" alt-text="Screenshot of numbering example." lightbox="./media/dataentitiesdatapackages06.png":::

## Mapping

When you work with data entities, the system automatically maps an entity to a source. You can override the automatic mapping of fields if needed.

### View mapping

To view how an entity is mapped, find the tile for the entity in the project, and then select **View map**.

The system provides two views: mapping visualization view (default) and mapping details view. A red asterisk (\*) identifies any required fields in an entity. You must map these fields to work with the entity. You can leave other fields unmapped as required when you work with the entity.

- To unmap a field, highlight the field in either column (**Entity** or **Source**), select **Delete selection**, and then select **Save**. After saving, close the form to return to the project.

You can also edit the field mapping from source to staging after import by using the same process.

:::image type="content" source="./media/dataentitiesdatapackages07.png" alt-text="Screenshot of mapping visualization." lightbox="./media/dataentitiesdatapackages07.png":::

### Regenerate a map

If you extend an entity (add fields) or if the automatic mapping appears to be incorrect, you can regenerate the mapping of the entity in the **Mapping** form.

1. Select **Generate source mapping**.

    A message asks, "Do you want to generate the mapping from scratch?"

1. Select **Yes** to regenerate the mapping.

### Generate data

If you have fields in entities that you want the system to generate data for during import, instead of providing the data in the source file, use the auto-generated functionality in the mapping details for the entity. For example, if you want to import customers and customer address information, but the address information wasn't previously imported with the Global Address Book entities, you can have the entity auto-generate the party number upon import and the GAB information is created. To access this functionality, view the map of the entity and select the **Mapping details** tab. Select the fields that you want to auto-generate. This action changes the source field to **Auto**.

:::image type="content" source="./media/dataentitiesdatapackages18.png" alt-text="Screenshot of generate data." lightbox="./media/dataentitiesdatapackages18.png":::

### Turn off automatically generated number sequences

Many entities support automatic generation of identifiers based on number sequence setup. For example, when you create a product, the product number is automatically generated and the form doesn't allow you to edit values manually.

:::image type="content" source="./media/dataentitiesdatapackages15.jpg" alt-text="Screenshot of automatic number sequence." lightbox="./media/dataentitiesdatapackages15.jpg":::

You can enable manual assignment of number sequences for a specific entity.

:::image type="content" source="./media/dataentitiesdatapackages16.png" alt-text="Screenshot of enable manual number sequences." lightbox="./media/dataentitiesdatapackages16.png":::

After you enable manual assignment, you can provide manually assigned numbers instead.

:::image type="content" source="./media/dataentitiesdatapackages17.png" alt-text="Screenshot of provide number sequence." lightbox="./media/dataentitiesdatapackages17.png":::

## Export

Export is the process of retrieving data from a system by using data entities. You perform the export process through a project. When exporting, you have flexibility in how you define the export project. You can choose which data entities to export, but you also choose the number of entities, the file format used (there are 14 different formats to choose from for export), and you can apply a filter to each entity to limit what is exported. After you add the data entities to the project, you can perform the sequencing and mapping described earlier for each export project.

:::image type="content" source="./media/dataentitiesdatapackages08.png" alt-text="Screenshot of export page." lightbox="./media/dataentitiesdatapackages08.png":::

After you create and save the project, you can export the project to create a job. During the export process, you can see a graphical view of the status of the job and the record count. This view shows multiple records, so you can review the status of each record before you download the actual files.

:::image type="content" source="./media/dataentitiesdatapackages10.png" alt-text="Screenshot of execution summary." lightbox="./media/dataentitiesdatapackages10.png":::

:::image type="content" source="./media/dataentitiesdatapackages11.png" alt-text="Screenshot of record counts." lightbox="./media/dataentitiesdatapackages11.png":::

After the job completes, you can choose how to download the files: each data entity can be a separate file, or you can combine the files into a package. If the job contains multiple data entities, choosing the package option speeds up the upload process. The package is a zip file that contains a data file for each entity as well as a package header and manifest. These additional documents are used when importing to add the data files to the correct data entities and sequence the import process.

## Import

Import is the process of pulling data into a system by using data entities. You perform the import process through the **Import** tile in the **Data Management** workspace. You can import data for individual entities or for a group of logically related entities that are sequenced in the correct order. The file formats vary depending on the type of import. For an entity, the file can be an Excel file that is comma-separated, tab-separated, or text. For a data package, the file is a .zip file. In both cases, you export the files by using the previously described export process.

### Import a data package

1. Sign in to the environment by using an account with sufficient privileges (typically the Administrator role).
1. On the dashboard, select the **Data Management** workspace.
1. Select the **Import** tile.
1. On the next page, complete the following steps:

    1. Enter a name.
    1. In the **Source Data Format** field, select **Package**.
    1. Select **Upload** and choose the appropriate package file from the location for the data you're importing. This action imports all the files from the package.

        :::image type="content" source="./media/dataentitiesdatapackages12.png" alt-text="Screenshot of choose package file." lightbox="./media/dataentitiesdatapackages12.png":::

    1. Select **Save**, and then select **Import**.

### Import multiple data packages

Use one of the following methods to import multiple data packages.

- Create a new job for each package, and then repeat steps 4(a) through 4(d) earlier in this procedure, for each package.
- Create one job to import multiple packages in a sequence. Repeat steps 4(a) through 4(c) earlier in this procedure, and then repeat step 4(c) for all packages that need to be imported. After you select the packages, execute step 4(d) to import the data from the selected data packages through a single job.

    :::image type="content" source="./media/dataentitiesdatapackages13.png" alt-text="Screenshot of multiple data packages." lightbox="./media/dataentitiesdatapackages13.png":::

When you select **Import**, the system imports the data through staging tables. You can track the progress of the import by using the **Refresh** button in the upper-right corner of the screen.

## Troubleshoot data package processing

This section provides troubleshooting information for the different stages of data package processing.

- You can find the status and error details of a scheduled job under the **Job history** section in the **Data management** form.
- You can display the status and error details of previous runs for data entities by selecting a data project and clicking **Job history**. In **the Execution history** form, select a job, and click **View staging data** and **View execution log**. The previous runs include data project runs that were executed as batch jobs or manually.

### Export process troubleshooting

- If you get an error during the export process, select **View execution log** and review the log text, staging log details, and Infolog for more information.
- If you get an error during the export process with a note directing you to not skip staging, turn off the **Skip staging** option, and then add the entity. If you export multiple data entities, use the **Skip staging** button for individual data entities.

### Import process troubleshooting

When uploading data entity files:

- If data entities don't display in **Selected files and entities** after you select **Upload** during the import process, wait a few minutes, and then check whether the OLEDB driver is still installed. If not, reinstall the OLEDB driver. The driver is Microsoft Access Database Engine 2010 Redistributable – AccessDatabaseEngine\_x64.exe.
- If data entities display in **Selected Files and Entities** with a warning after you select **Upload** during the import process, verify and fix the mapping of individual data entities by selecting **View map**. Update the mapping and select **Save** for each data entity.

During data entity import:

- If data entities fail (shown with a red X or yellow triangle icon on the data entity tile) after you select **Import**, select **View staging data** on each tile under the **Execution summary** page to review the errors. Sort and scroll through the records with Transfer status = Error to display the errors in the Message section. Download the staging table. Fix a record (or all records) directly in staging by selecting **Edit, Validate all, and Copy data to target**, or fix the import file (not staging file) and reimport the data.
- If data entities fail (shown with a red x or yellow triangle icon on the data entity tile) after you select **Import**, and **View staging data** shows no data, go back to the **Execution summary** page. Go to **View execution log**, select the data entity, and review the **Log text, Staging log details, and Infolog** for more information. **Staging log details** displays **Error column** (field) details and **Log description** describes errors in detail.
- If data entities fail, check the import file to see if there's an extra line in the file with text which displays, "This is a string that is inserted into Excel as a dummy cell to make the column to support more than 255 characters. By default, an Excel destination component doesn't support more than 255 characters. The default type of Excel will be set based on the first few rows". This line is added during data export. If this line exists, delete this line, re-package the data entity, and try to import.

## Features flighted in data management and enabling flighted features

The following features are enabled through flighting. *Flighting* is a concept that allows a feature to be ON or OFF by default.

| Flight name                           | Description |
|---------------------------------------|---------------|
| DMFEnableAllCompanyExport             | Enables BYOD export from all companies in the same export job (supported for BYOD only and not files). By default, this feature is OFF. This flight is no longer needed after Platform update 27 because this feature can be turned ON by using a parameter in data management framework parameters.|
| DMFExportToPackageForceSync           | Enables synchronous execution of data package API export. By default, it's asynchronous. |
| DMFEnableOdataBatchExporter           | Enables the Data Package Export API to perform asynchronous export in batch mode. By default, this feature is disabled. |
| EntityNamesInPascalCaseInXMLFiles     | Enables behavior where entity names are in Pascal Case in the XML files for entities. By default, the names are in upper case. |
| DMFByodMissingDelete                  | Enables the old behavior where under certain conditions, certain delete operations aren't synced to BYOD using change tracking. |
| DMFDisableExportFieldsMappingCache    | Disables caching logic when building target field mapping. |
| EnableAttachmentForPackageApi         | Enables attachments functionality in the package API. |
| FailErrorOnBatchForExport             | Enables fail on error at execution unit or level for export jobs. |
| IgnorePreventUploadWhenZeroRecord     | Disables 'prevent upload when zero records' functionality. |
| DMFInsertStagingLogToContainer        | By default this is ON. This improves performance and functional issues with error logs in the staging table. |
| ExportWhileDataEntityListIsBeingRefreshed     | When enabled, additional validations are made on mappings when a job is scheduled while entity refresh is in progress. By default, this is OFF.|
| DMFDisableXSLTTransformationForCompositeEntity     | This can disable the application of transformations on composite entities. |
| DMFDisableInputFileCheckInPackageImport     | Additional validations are made to ensure if any entity file is missing from a data package, error message is shown. This is the default behavior. If required, this can be turned OFF by this flight.  |
| FillEmptyXMLFileWhenExportingCompositeEntity     | Prior to Platform update 15, when exporting composite entities that didn't have any records to export, the XML file generated didn't have any schema elements. This behavior can be changed to output empty schema by enabling this flight. By default, the behavior still outputs empty schema.  |
| EnableNewNamingForPackageAPIExport     | A fix was made to ensure unique names are used for the execution ID when ExportToPackage is used for export scenarios. Duplicate execution IDs were being created when ExportToPackage was called in quick succession. To preserve compatibility, this behavior is OFF by default. Turning this flight ON enables this new behavior where new naming convention for execution IDs ensures unique names.|
| DMFDisableDoubleByteCharacterExport     | A fix was made to ensure that data can be exported when the format is configured to use code page 932 setting. If an issue is encountered in relation to double byte exports, this fix can be turned off by disabling this flight to unblock, if applicable. |
| DisablePendingRecordFromJobStatus     | A fix was made to ensure that pending records are taken into consideration while evaluating the final status of an import job. If implementations have a dependency on the status evaluation logic and this change is considered a breaking change for an implementation, this new logic can be disabled by using this flight.  |
| DMFDisableEnumFieldDefaultValueMapping     | A fix was made to ensure that default values set in advanced mapping for enum fields are successfully saved in the data package manifest file when generating the data package. This makes it possible for the data package to be used as a template for integrations when such advanced mappings are used. This fix is protected by this flight and can be disabled if the previous behavior is still needed (which is to always set the value to 0 in the data package manifest).  |
| DMFXsltEnableScript     | This flight only applies to Platform update 34 and non-production environments. A fix was made in Platform update 34 to prevent scripting in XSLT. However, this change resulted in breaking some functionality that was dependent on scripting. As a result, this flight was turned ON by Microsoft in all production environments as a preventive measure. In non-production environments, customers must add this flight if they encounter XSLT failures related to scripting. From Platform update 35 onward, a code change was made to revert the Platform update 34 change so this flight doesn't apply from Platform update 35 onward. Even if you enabled this flight in Platform update 34, upgrading to Platform update 35 doesn't cause any negative impact due to this flight being ON from Platform update 34. |
| DMFExecuteSSISInProc     | This flight is OFF by default. This flight is related to a code fix that was made to run SQL Server Integration Services (SSIS) out of process to optimize memory utilization of SSIS when running DIXF jobs. However, this change caused a regression in a scenario where if the DIXF data project name has an apostrophe (') in it, the job fails with an error. If you encounter this issue, removing the (') in the data project name resolves the failure. However, if for some reason the name can't be changed, then this flight can be enabled to overcome this error. Enabling this flight makes SSIS run in-process as before, which could lead to higher memory consumption when running DIXF jobs.  |

The following steps enable a flight in a Tier-1 environment. Execute the following SQL command.

To enable flights in a production or sandbox environment, log a support case with Microsoft.

- After running the SQL statement, ensure that the following is set in the web.config file on each of the AOSs.
        add key="DataAccess.FlightingServiceCatalogID" value="12719367"
- After making the preceding change, perform an IISReset on all AOSs.

    ```sql
    INSERT INTO SYSFLIGHTING
    ([FLIGHTNAME]
    ,[ENABLED]
    ,[FLIGHTSERVICEID]
    ,[PARTITION]
    ,[RECID]
    ,[RECVERSION]
    )
    VALUES ('name', 1, 12719367, PARTITION, RECID, 1)
    ```

- Partition - Partition ID from the environment, which you can get by querying (select) for any record. Every record has a partition ID that you must copy and use here.
- RecID - Same ID as partition. However, if you enable multiple flights, then this can be partition ID + 'n' to ensure it has a unique value
- RecVersion = 1

## Additional resources

- [Data entities overview](data-entities.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
