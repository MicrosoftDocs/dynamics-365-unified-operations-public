---
# required metadata

title: Data entities and packages framework | Microsoft Docs
description: This topic provides information about using data entities and data entity packages in Microsoft Dynamics 365 for Operations. 
author: kfend
manager: AnnBe
ms.date: 2016-06-29 14:26:04
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# keywords: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: 51
ms.suite: Released- Dynamics AX 7.0.0
# ms.tgt_pltfrm: 
ms.custom: 96283
ms.assetid: a64a9304-115e-4586-a4c3-b08ea2835e74
ms.region: Global
# ms.industry: 
ms.author: kfend

---

# Data entities and packages framework

This topic provides information about using data entities and data entity packages in Microsoft Dynamics 365 for Operations. 

Data entities
-------------

Data entities provide conceptual abstraction and encapsulation of underlying table schema that represent data concepts and functionalities. In Microsoft Dynamics AX 2012, most tables, like the Customer and Vendor tables, were de-normalized and split into multiple tables. This was beneficial from a database design point of view, but made it difficult for implementers and ISV’s to use without a thorough understanding of the physical schema. Data entities were introduced as part of data management to be used as a layer of abstraction to easily understand by using business concepts. In previous versions of Dynamics AX, there were multiple ways to manage data, such as Microsoft Excel Add-ins, AIF, and DIXF. The concept of data entities combines those different concepts into one. After data entities are created, you should be able to reuse them for an Excel Add-ins, import/export, or integration. The following table shows core data management scenarios.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><strong>Data Migration</strong></td>
<td><ul>
<li>Migrate reference, master, and document data from legacy or external systems.</li>
</ul></td>
</tr>
<tr class="even">
<td><strong>Setup and copy configuration</strong></td>
<td><ul>
<li>Copy configuration between company/environments.</li>
<li>Configure processes or modules using the Lifecycle Services (LCS) environment.</li>
</ul></td>
</tr>
<tr class="odd">
<td><strong>Integration</strong></td>
<td><ul>
<li>Real-time service based integration.</li>
<li>Asynchronous integration.</li>
</ul></td>
</tr>
</tbody>
</table>

## Data migration
The following pain points can occur during migration:

-   Inability to quickly do iterative migration and validations.
-   Multiple hops that lead to multiple dependencies and change of errors.
-   Complexity due to repeated manual interventions.
-   Difficulty in tracing and error troubleshooting.
-   Difficulty migrating a large volume of data within a time constraint.
-   During migration, you can strategize and choose data entities. Data entities also save time during implementation because previous activities required data export from a database, data export validation, and data transformation to files such as Excel or XML. In the current version Dynamics 365 for Operations, these hops have been eliminated. If an import error occurs, you can skip selected records and choose to proceed with the import using the good data, opting to then fix and import the bad data later. You will be allowed to partially continue and bad data will be indicated by using errors. Data imports can be easily scheduled using a batch, which offers flexibility when it is required to run. For example, you can migrate customer groups, customers, vendors, and other data entities in the system at any time.

## Set up and copy configuration
Starting a new implementation can be difficult because the knowledge of the data that needs to be entered can sometimes be limited. Data must be entered by module, or it must be configured using business processes. It is even more difficult to determine data dependencies and how the data sequencing should be configured in the implementation. Re-usability is also a factor as to where and how data can be used across environments. These pain points are addressed in the current version of Dynamics 365 for Operations. Movement of data becomes easier as it moves from test to staging to production environments. Movement of data can occur in any order. This is not a movement of the entire database but rather, only the data entities that you have chosen. The migration with the new version of Dynamics 365 for Operations allows:

-   Moving data between two similar Dynamics 365 for Operations systems.
-   Discovering setup entities and any dependency between each entity for a given process or module.
-   Maintaining a reusable library of data templates and datasets.
-   Data packages is a new concept that allows you to build incremental data entities. Data entities can be sequenced inside the packages. You can name data packages, which can be easily identifiable during import or export. When building data packages, data entities can be mapped on staging tables in a tabular format or by using available visual representation in data management. You can also drag-and-drop columns manually, depending on the mapping that you want for an entity. During import, data can easily be viewed using data management enabling data comparison.

## Data management concepts
The following terms are introduced in current version of Dynamics 365 for Operations. Take time to learn these terms, as they will be used in other sections of this document.

|                  |                                                                                                                                                                                        |
|------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Data project** | A project that contains configured data entities, which include mapping and default processing options.                                                                                |
| **Data job**     | A job that contains an execution instance of the data project, uploaded files, schedule (recurrence), and processing options.                                                          |
| **Job history**  | Histories of source to staging and staging to target.                                                                                                                                  |
| **Data package** | A single compressed file that contains a data project manifest and/or data files. This is generated from a data job and used for import or export of multiple files with the manifest. |

## Using data entities
The following sections provide quick snapshots of the different functionalities of data management using data entities. The goal is to help to you strategize and make effective decisions on how to best utilize the available tools during data migration. You will also find tips and tricks on how to effectively use each area during data migration. A list of available data entities for each area can also be found with the suggested data sequences, showing data dependencies within Dynamics 365 for Operations. Microsoft provides data packages that can be found on Lifecycle Services (LCS) as an initial guide. The information in this document can be used as a guide for creating your own packages. The description of each data entity shows what the object contains and if it is needed during data migration.

## Sequencing
There are two types of sequencing that should be considered when working with data entities.

-   Sequencing data entities within the data packages.
-   Sequencing for the order of importing the data packages.

**Sequencing data entities within the Data Packages**

1.  When a user adds data entities to a data project, by default, a sequence is set for the order in which the entities will load. The first entity added to the project will be set as the first entity to load, the next entity added will be second, the next entity will be third, and so on. For example, if a user added two entities in this order, **Sales tax codes** and **Sales Tax groups**, **Sales tax codes** is assigned an entity sequence of **1.1.1**, and **Sales tax groups** is assigned an entity sequence of **1.1.2**. The sequence level indicates that the second entity will not start the import process until the first level has completed.
2.  To view or edit the sequence, click the **Entity sequence** button on the Action Pane of the data project. [![DataEntitiesDataPackages01](./media/dataentitiesdatapackages01.png)](./media/dataentitiesdatapackages01.png)
3.  In the definition group entity sequence, you can see the execution units and the sequence.
4.  The sequence can be changed by selecting the data entity in the list, setting a different Execution unit or Sequence in level, and then clicking **Update selected**. After clicking **Update selected**, the entity will be moved up or down in the entity list.

To further illustrate, the following screenshot shows the entity sequence that is set for the Sales Tax CodeGroups data package. [![DataEntitiesDataPackages02](./media/dataentitiesdatapackages02.png)](./media/dataentitiesdatapackages02.png)In order to successfully import sales tax codes and groups, the sales tax codes and details have to be loaded first, before sales tax groups can be imported. Sales tax codes and groups are all in Execution unit = 1, but the sequences are in the order that they will be imported. Other related sales tax entities that are not dependent upon other data entities being loaded are included in the package. For example, sales tax exempt numbers, is set in its own Execution unit = 2. This data entity will start loading immediately because there are no dependencies on other entities loading before it. **Sequencing of the data packages** In order to successfully load data, the order of loading the data packages is important because of dependencies that exist within and across modules in Dynamics 365 for Operations. The numbering format that has been created for the data packages within LCS are as follows:

-   First segment = Modulearea
-   Second segment = Data type (SetupMasterTransaction)
-   Third sequence = Sequence number

The following tables provide more information about the different kinds of numbering. **ModuleArea numbering**[![DataEntitiesDataPackages03](./media/dataentitiesdatapackages03.png)](./media/dataentitiesdatapackages03.png)**Data type numbering** [![DataEntitiesDataPackages04](./media/dataentitiesdatapackages04.png)](./media/dataentitiesdatapackages04.png)**Numbering format** [![DataEntitiesDataPackages05](./media/dataentitiesdatapackages05.png)](./media/dataentitiesdatapackages05.png) The data packages will have the numbering format, followed by the module abbreviation, and description. The following example shows General ledger data packages. [![DataEntitiesDataPackages06](./media/dataentitiesdatapackages06.png)](./media/dataentitiesdatapackages06.png)

## Mapping
When working with data entities, the mapping of the entity to the source is automatic. This mapping of fields can be overridden if needed. To view the mapping, locate the tile for the entity in the project, and then click **View map**. When viewing the mapping there are two views: mapping visualization (default view) or mapping details. A red asterisk (\*) will identify any required fields in the entity. These fields need to be mapped in order to work with the entity. Other fields can be unmapped as required when working with the entity. To unmap a field, highlight the field in either column (**Entity** or **Source**), and then click **Delete selection**. Click **Save** to save your changes. After saving, close the form to return to the project. The field mapping from source to staging can also be edited after import using the same process. [![DataEntitiesDataPackages07](./media/dataentitiesdatapackages07.png)](./media/dataentitiesdatapackages07.png) If you have extended an entity (added fields) or if the automatic mapping appears to be incorrect, the mapping of the entity can be regenerated in the **Mapping** form. To do this, click **Generate source mapping**. A message will display asking, “Do you want to generate the mapping from scratch ?” Click **Yes** to regenerate the mapping.

## Export
Export is the process of pulling data out of a system utilizing data entities. The export process is done through a project. When creating the process there is a lot of flexibility as to how the export project is defined. There is an option to choose not only which data entities to export, but also the number of entities, the file format used (there are 14 different formats to choose for export), and apply a filter to each entity to limit what is exported. After the data entities have been pulled into the project, the [Sequencing](https://ax.help.dynamics.com/en/?post_type=incsub_wiki&p=1105473&preview=true#Sequencing) and [Mapping](https://ax.help.dynamics.com/en/?post_type=incsub_wiki&p=1105473&preview=true#Mapping) described earlier can be performed for each export project. [![DataEntitiesDataPackages08](./media/dataentitiesdatapackages08-1024x400.png)](./media/dataentitiesdatapackages08.png) [![DataEntitiesDataPackages09](./media/dataentitiesdatapackages09.png)](./media/dataentitiesdatapackages09.png) After the project is created and saved you can export the project to create a job. During the export process, you can see a graphical view of the status of the job and the record count. This view shows multiple records so you can review the status of each record prior to downloading the actual files. [![DataEntitiesDataPackages10](./media/dataentitiesdatapackages10-1024x280.png)](./media/dataentitiesdatapackages10.png) [![DataEntitiesDataPackages11](./media/dataentitiesdatapackages11.png)](./media/dataentitiesdatapackages11.png) After the job is completed you can choose how to download the files, either as each data entity as a separate file or by combining the files as a package. If there are multiple data entities in the job, choosing the package option will expedite the upload process. The package is a zipped file, containing a data file for each entity as well as a package header and manifest. These additional documents are used when importing in order to add the data files to the correct data entities and sequence the import process.

## Import
Import is the process of pulling data into a system utilizing data entities. The import process is done through the **Import** tile in the **Data Management** workspace. Data can be imported either for individual entities or for a group of logically related entities that are sequenced in the correct order. The file formats vary depending on the type of import. For an entity, it can be an Excel file that is comma-separated, tab-separated, text. For a data package, it is a .zip file. In both cases, the files are exported using the above mentioned export process. The detailed steps for importing data using data packages is as follows.

1.  Log into the Dynamics 365 for Operations environment using a login with sufficient privileges (typically this is the Administrator role).
2.  On the dashboard, select the **Data Management** workspace.
3.  To begin importing, select the **Import** tile.
4.  On the next page, do the following:
    1.  In the **Name** field, provide a logical name for the package being imported.
    2.  In the **Source Data Format** field, select **Package** as the source data format.
    3.  Click the **Upload** button and choose the appropriate package file from the location for the data being imported. This will import all the files from the package. [![DataEntitiesDataPackages12](./media/dataentitiesdatapackages12-1024x555.png)](./media/dataentitiesdatapackages12.png)
    4.  Click **Save**, and then click **Import** to import the data.
    5.  If multiple data packages need to be imported this can be accomplished in two ways:
        -   Create new job for each package – Repeat steps 4(a) through 4(d) above, for each package. - or-
        -   Create one job to import multiple packages in a sequence. Repeat steps 4(a) through 4(c) above, and then repeat step 4(c) for all the packages that need to be imported. After you select the planned packages, execute step 4(d) to import the data from the selected data packages through a single job. [![DataEntitiesDataPackages13](./media/dataentitiesdatapackages13-1024x555.png)](./media/dataentitiesdatapackages13.png)

5.  After you click **Import**, the data will be imported through staging tables. The progress of the import can be tracked using the **Refresh** button in the upper-right corner of the screen. **Note: Utilizing the auto generated functionality** - If you have fields in entities that you want the system to generate on import, instead of providing the data in the source file, you can use the auto-generated functionality in the mapping details for the entity. For example, if you want to import customers and customer address information, but the address information was not previously imported with the Global Address Book (GAB) entities, you can have the entity auto-generate the party number upon import and the GAB information will be created. To access this functionality, view the map of the entity and click the **Mapping details** tab. Select the fields that you want to auto-generate. This will change the source field to **Auto**. [![DataEntitiesDataPackages18](./media/dataentitiesdatapackages18.png)](./media/dataentitiesdatapackages18.png)

    Troubleshooting
    ---------------

    This section describes how to troubleshoot during the different stages of data package processing.

    ### Export process

    -   If you get an error during the export process, click **View execution log** and review the log text, staging log details, and Infolog for more information
    -   If you get an error during the export process with a note directing you to not skip staging, turn off the **Skip staging**, and then add the entity. If you are exporting multiple data entities, you can use the **Skip staging** button for each data entity.

    ### Import process

    -   Upload the data entity files
    -   If data entities do not display in **Selected files and entities** after you click **Upload** during the import process, wait a few minutes, then check if the OLEDB driver is still installed. If not, then reinstall the OLEDB driver. The driver is Microsoft Access Database Engine 2010 Redistributable – AccessDatabaseEngine\_x64.exe.
    -   If data entities display in **Selected Files and Entities** with a warning after you click **Upload** during the import process, verify and fix the mapping of individual data entities by clicking **View map**. Update the mapping and click **Save** for each data entity.
    -   Import the data entities
    -   If data entities fail (shown with a red X or yellow triangle icon on the data entity tile) after you click **Import**, click **View staging data** on each tile under the **Execution summary** page to review the errors. Sort and scroll through the records with Transfer status = Error to display the errors in the Message section. Download the staging table via Microsoft Office. Fix a record (or all records) directly in staging by clicking **Edit, Validate all, and Copy data to target**,  or fix the import file (not staging file) and reimport the data.
    -   If data entities fail (shown with a red x or yellow triangle icon on the data entity tile) after you click **Import**, and **View staging data** shows no data, go back to the **Execution summary** page. Go to **View execution log**, select the data entity, and review the **Log text, Staging log details, and Infolog** for more information. **Staging log details** will display **Error column** (field) details and **Log description** will describe errors in detail.
    -   If data entities fail, you can check the import file to see if there’s an extra line in the file with text which displays, “This is a string that is inserted into Excel as a dummy cell to make the column to support more than 255 characters. By default, an Excel destination component will not support more than 255 characters. The default type of Excel will be set based on the first few rows. ”. This line is added during data export. If this line exists, delete this line, re-package the data entity, and try to import.

    ### After exports and imports

    -   Status and error details of a scheduled job can be found under the **Job history** section in the **Data management** form.
    -   Status and error details of previous runs for data entities can be displayed by selecting a data project and clicking **Job history**. In **the Execution history** form, select a job, and click **View staging data** and **View execution log**. The previous runs include data project runs that were executed as batch jobs or manually.

    ### Number sequence

    Many entities support automatic generation of identifiers based on number sequence setup. For example, when creating a product, the product number is automatically generated and the form does not allow you to edit values manually. [![DataEntitiesDataPackages15.png](./media/dataentitiesdatapackages15.png-300x213.jpg)](./media/dataentitiesdatapackages15.png.jpg) It is possible to enable manual assignment of number sequences. [![DataEntitiesDataPackages16](./media/dataentitiesdatapackages16-300x153.png)](./media/dataentitiesdatapackages16.png) In this case, you can manually provide the value and enable manual assignment of product numbers instead.[![DataEntitiesDataPackages17](./media/dataentitiesdatapackages17-300x214.png)](./media/dataentitiesdatapackages17.png)

    ### System users entity

    -   While importing the system users entity, you may receive a integrity violation error if there is a guest user in the exported package. The guest user must be deleted from the package in order for the entity to work.
    -   If a record already exists in the **UserInfo** table (the Admin record would most likely always exist), the import will fail for those records but work for other records.



See also
--------

[Data entities](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/data-entities/data-entities)

[Data entities home page](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/data-entities/data-entities-home-page)

