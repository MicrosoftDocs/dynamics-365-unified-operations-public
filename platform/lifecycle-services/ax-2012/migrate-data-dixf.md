---
# required metadata

title: Migrate data using the Data import/export framework (AX 2012)
description:  This topic describes how to use the Data Import/Export Framework for Microsoft Dynamics AX 2012 to migrate data.
author: kfend
manager: AnnBe
ms.date: 2015-12-02 16 - 55 - 52
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
ms.custom: 13341
ms.assetid: 6f49739f-2690-4bad-8afc-3310274315fa
ms.search.region: Global
# ms.search.industry: 
ms.author: kfend
ms.dyn365.ops.intro: 
ms.dyn365.ops.version: 2012

---

# Migrate data using the Data import/export framework (AX 2012)

 This topic describes how to use the Data Import/Export Framework for Microsoft Dynamics AX 2012 to migrate data.

**Note:** This topic includes information about features that were added or changed for cumulative update 7 or later for Microsoft Dynamics AX 2012 R2. This information also applies to AX 2012 R3. This topic includes the following processes:

-   Determine which Microsoft Dynamics AX entities to use
-   Using the Data Import and Export Framework:
    -   Define your source data formats
    -   Identify entities to add to a processing group
    -   Create a new target entity
    -   Modify an entity’s target mapping
    -   Define a processing group
    -   Optional: Change the source to staging mapping for an entity
    -   Optional: Change the staging to target mapping for an entity
    -   Define security for a processing group
    -   Preview errors before processing
    -   Process export data
    -   Process import data

## Plan to migrate data
Data import is a complex process that usually requires several iterations. The import process includes the following general steps:

1.  Identify the data in your existing system that must be imported.
2.  Consider cleaning up the data in your existing system. For example, determine whether old records can be deleted or archived, whether the current database contains duplicate records, and whether you want to change numbering schemes.
3.  Become familiar with the relevant data structures in Microsoft Dynamics AX that the data from your existing system must be moved to. **Note:** Data from one table in another system might have to be moved into multiple tables in Microsoft Dynamics AX.
4.  Determine the appropriate tools and techniques to use for the data that you must import. For a list of the tools that can be used, see [Plan data import, export, and migration](http://technet.microsoft.com/library/a05289fb-0f8f-4563-be3c-7c840bfea7e1(AX.60).aspx).
5.  Prepare a test Microsoft Dynamics AX environment. Required configuration for master records must be completed before you import data.
6.  Create a backup of your existing system and your Microsoft Dynamics AX environment before you import any data.
7.  Perform a trial import of all types of data that are required. **Note:** Expect to encounter errors the first time that you perform an import. Review the errors that you encounter, make any fixes that are required, and perform the import again.

If you are moving from another ERP system to Microsoft Dynamics AX, you must import master and reference data. **Note:** We recommend that you not import transactional data or historical data into Microsoft Dynamics AX. Instead, close all open transactions before import, if these transactions can be closed. Maintain the database that contained your previous transactional data, for reporting and compliance purposes. Data export is usually less complex but might still require some planning. The export process includes the following general steps:

1.  Identify the data in your existing system that must be exported.
2.  Consider cleaning up the data in your existing system. For example, determine whether old records can be deleted or archived, whether the current database contains duplicate records, and whether you want to change numbering schemes.
3.  Become familiar with the relevant data structures in the system that the data must be exported to.
4.  Determine the export format. The format can be AX if you are moving data to another Microsoft Dynamics AX instance or File if you are moving data to any other kind of system.
5.  Determine whether any of the data has to be transformed or cleaned in the staging table before export.

### Determine which Microsoft Dynamics AX entities to use

For a list of the predefined target entities that the Data Import/Export Framework includes, see [Data import/export framework entities (DIXF, DMF)](entities-dixf.md). Each entity must be associated with an entity class, a staging table, and a target table. For predefined entities, these values are pre-populated.

-   The staging table is the table that the data is written to before it is transformed when this entity is used for import procedures.
-   The entity class is where X++ transformation logic is stored. You can create a copy of an entity class and modify the transformation logic.
-   The target table is the table that data is pulled from for export procedures, or the table that fully modified data is written to for import procedures.

**Important: **The mapping from the staging table schema to the target table schema is automatically generated. Unless you have customized your target Microsoft Dynamics AX system, you should not have to modify the staging-to-target mapping. For details about each target entity, you can review the information in **Data Import/Export Framework** &gt; **Setup** &gt; **Target entities**. If no default target entity suits your purposes, you can create a new target entity by using an entity that is already present in the system. If no entity that is already present in the system is appropriate, you can create a custom entity. For more information about how to create a custom entity, see [Create a custom target entity for the Data import/export framework (DIXF, DMF)](create-custom-target-entity-dixf.md).

## Using the Data Import/Export Framework
This section provides information about how to use the Data Import/Export Framework to import or export data. This section contains the following subsections:

-   Define your source data formats
-   Identify entities to add to a processing group
-   Create a new target entity
-   Modify an entity’s target mapping
-   Define a processing group
-   Optional: Change the source to staging mapping for an entity
-   Optional: Change the staging to target mapping for an entity
-   Define security for a processing group
-   Preview errors before processing
-   Process export data
-   Process import data

### Define your source data formats

You must create source data formats for data that you want to export or import. Review the data that you plan to migrate to or from Microsoft Dynamics AX. Determine whether that data is in files, in data stores that can be accessed through Open Database Connectivity (ODBC) connections, or in existing AX 2012 installations. Create a source data format for each type of data that you are migrating.

#### Configure a source data format for data from a CSV or fixed-width file

For files, you must define whether the data comes from a list that consists of comma-separated values, a fixed-width file, a Microsoft Excel file, or an XML file. Source files can contain default values for a column.

1.  Open **Data import export framework** &gt; **Setup** &gt; **Source data formats**.
2.  Click **New**, and then provide a name and description for the source.
3.  Verify that the type is **File**.
4.  On the **General** tab, select values for the following options if you are using a delimited or fixed-width file.
    <table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th>Option</th>
    <th>Description</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><strong>File format</strong></td>
    <td>Select <strong>Delimited</strong> or <strong>Fixed width</strong>. Delimited formats use a specific character to separate fields. Fixed-width formats set aside a specific number of characters for each field. <strong>Note:</strong> Field widths are defined for each entity, not in the data format.</td>
    </tr>
    <tr class="even">
    <td><strong>First row header</strong></td>
    <td>Select this option if the first row of your data files contains header information.For fixed-width formats, you can specify delimiter characters to define the values in the header row, if there is a header row.</td>
    </tr>
    <tr class="odd">
    <td><strong>Row delimiter</strong></td>
    <td>Select the delimiter for rows.
    <table>
    <thead>
    <tr class="header">
    <th>Value</th>
    <th>Description</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>{CR}{LF}</td>
    <td>The header row is delimited by a carriage return/line feed combination.</td>
    </tr>
    <tr class="even">
    <td>{CR}</td>
    <td>The header row is delimited by a carriage return.</td>
    </tr>
    <tr class="odd">
    <td>{LF}</td>
    <td>The header row is delimited by a line feed.</td>
    </tr>
    <tr class="even">
    <td>Semicolon {;}</td>
    <td>The header row is delimited by a semicolon.</td>
    </tr>
    <tr class="odd">
    <td>Colon {:}</td>
    <td>The header row is delimited by a colon.</td>
    </tr>
    <tr class="even">
    <td>Comma {,}</td>
    <td>The header row is delimited by a comma.</td>
    </tr>
    <tr class="odd">
    <td>Tab {t}</td>
    <td>The header row is delimited by a tab.</td>
    </tr>
    <tr class="even">
    <td>Vertical bar {|}</td>
    <td>The header row is delimited by a vertical bar.</td>
    </tr>
    </tbody>
    </table></td>
    </tr>
    <tr class="even">
    <td><strong>Column delimiter</strong></td>
    <td>Select the delimiter for columns. For a list of the available values, see the description of the Row delimiter parameter.</td>
    </tr>
    <tr class="odd">
    <td><strong>Text qualifier</strong></td>
    <td>Enter the delimiter that is used if the text values in a row contain the character that you are using as a row or column delimiter. For example, if your organization names include commas, but you are using commas as column delimiters, you should enter another delimiter to use for text values. In this example, you might want to use a double quotation mark (&quot;).</td>
    </tr>
    <tr class="even">
    <td><strong>Skip row</strong></td>
    <td>Select this option to leave rows that contain errors unprocessed and continue with the processing. If this option is selected, errors are written to the log.</td>
    </tr>
    </tbody>
    </table>

5.  Set the following general parameters for regional settings.
    | Option              | Description                                                                                              |
    |---------------------|----------------------------------------------------------------------------------------------------------|
    | **Code page**       | Specify the code page for non-Unicode text.                                                              |
    | **Unicode**         | Select this option to use Unicode.                                                                       |
    | **Language locale** | Specify the locale to provide language-specific information for ordering, and for date and time formats. |

6.  Set the following general parameters for multiple value separators.
    | Parameter                    | Description                                                                                                                                                                 |
    |------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | **Multiple value separator** | Optional: Enter the delimiter to use for fields that contain multiple values that are associated with a single record, such as email addresses, telephone numbers, or URLs. |

7.  Click **Application** to set the parameter values to **Dimensions** and **Name sequence**.
8.  Set the following general parameters for dimensions.
    | Parameter                       | Description                                                                                                                                                        |
    |---------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | **Dimension code**              | Optional: Specify the list of financial dimensions that are part of the source file. The codes for the financial dimensions are pulled from Microsoft Dynamics AX. |
    | **Chart of accounts delimiter** | The delimiter between financial dimension values.                                                                                                                  |
    | **Dimension format**            | The predefined format of the dimension, based on the financial dimensions and delimiter that you selected.                                                         |

9.  Set the following value for name sequences.
    | Parameter         | Description                                                                      |
    |-------------------|----------------------------------------------------------------------------------|
    | **Name sequence** | Specify the default name sequence for parties that are created during migration. |

10. Close the form.

#### Configure a source data format for data from an XML file

This section describes how to create a source data format for data from an XML file.

1.  Open **Data import export framework** &gt; **Setup** &gt; **Source data formats**.
2.  Click **New**, and then provide a name and description for the source.
3.  Verify that the type is **XML**.
4.  On the **General** tab, select values for the following options:
    1.  In the **File format** field, select **XML**.
    2.  In the **Language locale** field, select a language locale.
    3.  Optional: Under **Multiple value separator**, select a role separator to use to delimit fields that contain multiple values that are associated with a single record, such as email addresses, telephone numbers, or URLs.

5.  Click **Application** to set the parameter values to **Dimensions** and **Name sequence**.
6.  Set the following general parameters for dimensions.
    | Parameter                       | Description                                                                                                                                                        |
    |---------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | **Dimension code**              | Optional: Specify the list of financial dimensions that are part of the source file. The codes for the financial dimensions are pulled from Microsoft Dynamics AX. |
    | **Chart of accounts delimiter** | The delimiter between financial dimension values.                                                                                                                  |
    | **Dimension format**            | The predefined format of the dimension, based on the financial dimensions and delimiter that you selected.                                                         |

7.  Set the following value for name sequences.
    | Parameter         | Description                                                                      |
    |-------------------|----------------------------------------------------------------------------------|
    | **Name sequence** | Specify the default name sequence for parties that are created during migration. |

8.  Close the form.

#### Configure a source data format for data from an Excel file

This section describes how to create a source data format for data from an Excel file.

1.  Open **Data import export framework** &gt; **Setup** &gt; **Source data formats**.
2.  Click **New**, and then provide a name and description for the source.
3.  Verify that the type is **Excel**.
4.  On the **General** tab, select values for the following options:
    1.  In the **File format** field, select **Excel**.
    2.  In the **Language locale** field, select a language locale.
    3.  Optional: Under **Multiple value separator**, select a role separator to use to delimit fields that contain multiple values that are associated with a single record, such as email addresses, telephone numbers, or URLs.

5.  Click **Application** to set the parameter values to **Dimensions** and **Name sequence**.
6.  Set the following general parameters for dimensions.
    | Parameter                       | Description                                                                                                                                                        |
    |---------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | **Dimension code**              | Optional: Specify the list of financial dimensions that are part of the source file. The codes for the financial dimensions are pulled from Microsoft Dynamics AX. |
    | **Chart of accounts delimiter** | The delimiter between financial dimension values.                                                                                                                  |
    | **Dimension format**            | The predefined format of the dimension, based on the financial dimensions and delimiter that you selected.                                                         |

7.  Set the following value for name sequences.
    | Parameter         | Description                                                                      |
    |-------------------|----------------------------------------------------------------------------------|
    | **Name sequence** | Specify the default name sequence for parties that are created during migration. |

8.  Close the form.

#### Configure a source data format for data from an ODBC connection

This section describes how to configure a source data format for data from an ODBC connection.

1.  Open **Data Import/Export Framework** &gt; **Setup** &gt; **Source data formats**.
2.  Click **New**.
3.  Click **Type**, and then select **ODBC**.
4.  The Data Import/Export Framework connects to ODBC by using a data source name (DSN) type. In the **DSN** section, define which type of DSN you are using to connect, and where the DSN is located.If you have not yet defined a DSN for your ODBC connection, determine which type of DSN to use. For more information about DSNs, see [Using the ODBC Data Source Administrator](http://go.microsoft.com/fwlink/?LinkId=269895).
    -   **User DSN** – This type is available only to the person who created the DSN.
    -   **System DSN** – This type is available to all users of a computer.
    -   **File DSN** – This type lets you connect to a data provider. File DSNs can be shared by users who have the same drivers installed.

5.  Click **Validate** to make sure that the account that is used by the Data Import/Export Framework can connect to the DSN. If the Data Import/Export Framework service account can connect, the validation icon turns green.
6.  Close the form.

#### Configure a source data format for data from Microsoft Dynamics AX

This section describes how to configure a source data format for data from Microsoft Dynamics AX.

1.  Open **Data Import/Export Framework** &gt; **Setup** &gt; **Source data formats**.
2.  Click **New**.
3.  Click **Type**, and then select **AX**.
4.  You must set the parameter values for **Dimensions** and **Name sequence**. Set the following general parameters for dimensions.
    | Parameter                       | Description                                                                                                                                                        |
    |---------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | **Dimension code**              | Optional: Specify the list of financial dimensions that are part of the source file. The codes for the financial dimensions are pulled from Microsoft Dynamics AX. |
    | **Chart of accounts delimiter** | The delimiter between financial dimension values.                                                                                                                  |
    | **Dimension format**            | The predefined format of the dimension, based on the financial dimensions and delimiter that you selected.                                                         |

5.  Set the following value for name sequences.
    | Parameter         | Description                                                                      |
    |-------------------|----------------------------------------------------------------------------------|
    | **Name sequence** | Specify the default name sequence for parties that are created during migration. |

6.  Close the form.

### Identify entities to add to a processing group

The entities that are included in a processing group are processed together. You should include the following types of entities in a processing group:

-   Related entities that must be processed together
-   Entities that require that processing be performed in a specific sequence

Examples of entities that you might want to migrate together include **Customer** and **Customer Address**.

### Create a new target entity

If data that you want to migrate does not map to one of the default target entities, you can create a new entity. There are three types of entities that you can create:

-   **Entity** – Maps a single entity to a staging table and a target table.
-   **Table** – Lets you import data from a source to a target Microsoft Dynamics AX table directly, without using a staging table or applying any business logic. For table entities, unlike other types of entities, data cannot be pushed from one source table to multiple target tables. A table entity must be a one-to-one mapping from source to target. Table entities should be used only with fairly simple reference data that requires no modification and is easily mapped to the target table.
-   **Composite entity** – Lets you create one entity that is composed of several related entities. An example of a composite entity is a combination of a sales order entity and a sales line entity. You use a composite entity when you import from a source that contains data from multiple related tables in a single file. Composite entities support only file data sources.

To add a new target entity, follow these steps.

1.  Open **Data Import/Export Framework** &gt; **Setup** &gt; **Target entities**.
2.  Click **New**.
3.  In the **Entity type** field, select the type of entity to add.
    -   For an entity of the entity type, select the entity in the first **Entity** field, select the application module that the entity belongs to in the **Application module** field, and provide a unique name in the second **Entity** field. The other fields are populated automatically.
    -   For an entity of the table type, select the application module that the entity belongs to in the **Application module** field, provide a unique name in the second **Entity** field, and specify the target table in the **Staging table** field. Leave the **Entity class** and **Target entity** fields blank.
    -   For an entity of the composite entity type, select the application module that the entity belongs to in the **Application module** field, and provide a unique name in the second **Entity** field. Leave the **Staging table**, **Entity class**, and **Target entity** fields blank. Click **Child entities** to identify the entities that make up the composite entity.You add one child entity for each entity in the system that should be the target for part of the composite data. For example, you are importing composite sales information that contains both sales header data and sales line item data. In this case, you add one child entity for **DMFSalesTableEntity** and one child entity for **DMFSalesLineEntity**.
        1.  In the **Target entities** form, click **New** to add the first child entity.
        2.  In the **Application module** field, select the application module that the entity belongs to. In the second **Entity** field, provide a unique name. Select the related **Staging** table, **Entity** class, and **Target** entity values that belong to the target entity for part of the composite data.
        3.  Repeat steps 1 and 2 until you have added child entities for all targets of the composite data. Then click **Close**.

        All child entities in each composite entity must include a **RowID** field. By default, the following entities in the Data Import/Export Framework include a **RowID** field and can be used in composite entities: **DMFSalesTableEntity**, **DMFSalesLineEntity**, **DMFPurchTableEntity**, **DMFPurchLineEntity**, **DMFBOMEntity**, and **DMFBOMVersionEntity**.

### Modify an entity’s target mapping

You can change the sequence in which fields in an entity are processed. You can also enable a field to call the **validateField** method or the **modifiedField** method to check business logic when the field is processed. **Important:** Even if you set the **Call validate** field method or **Call modified** field method value for a field, you do not guarantee that a method will be run. These values only *enable* the methods to be run. However, the settings for the processing group determine whether a method is actually run for a specific operation.

1.  Open **Data import export framework** &gt; **Setup** &gt; **Target entities**.
2.  Select the target entity to modify, and then click **Modify target mapping**. The **Map staging to target** form opens.The default **Mapping visualization view** shows the staging fields, functions (entity classes that contain transformations), and target fields that are associated with the target entity.
3.  Click **Mapping details**.
4.  To modify the order in which a field is processed, change the **Sequence** value.
5.  To enable a field to be run together with any business logic in the **validateField** method, select **Call validate Field method**.
6.  To enable a field to be run together with any business logic in the **modifiedField** method, select **Call modified Field method**.
7.  Click **Save**, and then click **Close**.

### Define a processing group

When you import data, we recommend that you have a sample data file for any entity that uses a file-based data source. If you do not already have a sample file, you can create one when you add the entity to the processing group.

1.  Open **Data import export framework** &gt; **Common** &gt; **Processing group**. Click **New** to create a new processing group, and then enter a name and description.
2.  Select the processing group, and then click **Entities** to add entities to it.
    -   If you are adding an entity for import, the entity uses a file-based data source, and you have sample data, follow these steps:
        1.  Click **New**. In the **Entity** list, select an entity.
        2.  In the **Source data format** field, select the format of the source file.
        3.  In the **Sample file path** field, enter the location of the sample file.
        4.  Optional: If the source file is in Excel format, in the **Sample file path** field, specify the worksheet that contains the sample data.
    -   If you are adding an entity for import and the entity uses a file-based data source, but you do not have sample data, follow these steps:
        1.  Click **New**. In the **Entity** list, select an entity.
        2.  In the **Source data format** field, select the format of the source file.
        3.  If you are working with a fixed-width format, click **Specify file format**. If you are working with any other file-based format, click **Generate source file**.
        4.  On the second page of the wizard, select the fields that must be in the data source file. If you are using an XML data source, in the **XML type** field, select **XML** or **XSD**. Click **Generate sample file**.
        5.  If you are using an XML data source and selected an XSD XML type, a schema file is generated but not opened, and the path is displayed. Otherwise, the sample file is opened in Notepad or Excel, depending on the source data format, and contains the appropriate structure. Add some sample data. To save the sample file, click **File** &gt; **Save as**, and save the file to a location of your choice.
        6.  Click **Finish** to close the wizard.
        7.  In the **Sample file path** field, enter the location of the sample file that you just created.
    -   If you are adding an entity for export to a file, follow these steps:
        1.  Click **New**. In the **Entity list**, select an entity.
        2.  In the **Source data format** field, select the format of the source file.
        3.  In the **Sample file path** field, enter the location of a sample file. This file is used to determine the format of the exported data. Only the structure of the file is used. Any data that the file contains is ignored.
    -   If you are adding an entity for import that uses an ODBC data source, follow these steps:
        1.  Click **New**. In the **Entity** list, select an entity.
        2.  In the **Source data format** field, select the format of the source file.
        3.  In the **Sample file path** field, enter a SQL query to select the data that you want from the data source. For example, to retrieve customer data from another database, enter **select \* from Customers**.
    -   If you are adding an entity for import or export that uses a Microsoft Dynamics AX data source, follow these steps:
        1.  Click **New**. In the **Entity** list, select an entity.
        2.  In the **Source data format** field, select the format of the source file.

3.  Click **Generate source mapping**.
4.  Optional: For entities where you want to enable data conversion logic to run in those methods, select **Sample file path**.
5.  Optional: For entities where you want to enable data validation, select **Sample file path**.
6.  Optional: To change the order in which entities are processed, modify the Sequence values. Typically, you change the processing order only when one entity depends on another. For example, Customers should be processed before Customer Addresses.
7.  When you have finished, click **Close**.

### Optional: Change the source-to-staging mapping for an entity

After you have associated an entity with a processing group, you should validate that the entity is mapped correctly to the staging tables. Make any changes that are required. The following changes are typically made to a source-to-staging mapping:

-   Add default strings or numbers as new column values when data is imported.
-   Convert values during import.

#### Add default strings and numbers during the source-to-staging mapping

1.  Open **Data import export framework** &gt; **Common** &gt; **Processing group** &gt; **Entities**. Click **Modify source mapping**.The default Mapping visualization view lets you quickly see which source fields are mapped to which staging fields.
2.  Click **Mapping details**.
3.  In the **Source field** field, select a field, and then select the staging field that the field applies to.
4.  To add a default value for the field, follow these steps:
    1.  Select **Auto default** for the field.
    2.  Click **Default value**.
    3.  In the **Staging value** field, enter a value, and then click **OK**.

5.  To automatically generate a value for a field, based on a defined number sequence, select **Auto generate** for the field. You can also use a query to set criteria that are used to assign numbers to groups of values. Click **Query criteria**, select the field to use to create groups that numbers can be assigned numbers to, and then close the **Query criteria** form.
6.  Close the **Map source to staging** form.

#### Convert values during source-to-staging mapping

1.  Open **Data import export framework** &gt; **Common** &gt; **Processing group** &gt; **Entities**. Click **Modify source mapping**.
2.  Click **Mapping details**.
3.  In the **Source field** field, select a field, and then select the staging field that the field applies to.
4.  Click **Conversion**.
5.  In the **Define Conversion values** form, in the **Source value** and **Staging value** fields, enter values, and then click **Close**.
6.  Close the **Map source to staging** form.

### Optional: Change the staging-to-target mapping for an entity

By default, a staging-to-target mapping is generated. If you determine that the staging-to-target mapping is incorrect, you can manually update it in the **Mapping details** form.

### Define security for processing groups

You can set security for processing groups to define which users or roles can run a processing group. You can set a processing group to work for a single company instead of all companies. You can also disable a processing group from being run, without deleting it. You do not have to set security for processing groups. However, by default, all users have access to the data in processing groups.

#### Set security for a processing group

1.  After you have created your processing group, open **Data import export framework** &gt; **Setup** &gt; **Setup of roles for processing group**.
2.  Click **New** to set security.
3.  Enter values for the following fields:
    1.  In the **Apply processing group to** field, select **All** to apply security to all processing groups or **Table** to apply security to a single processing group.
    2.  If you selected **Table**, under **Processing group**, select the processing group to help secure.
    3.  Optional: To help secure a specific entity, in the **Entity** field, select the entity. This option is useful if you want different levels of security for entities in the same processing group.
    4.  In the **Grant access to** field, select whether to grant access to a role, a user, or all users.
    5.  If you selected to grant access by role, in the **Role name** field, select the role to which to grant access to run the processing group.
    6.  If you selected to grant access by user, in the **User name** field, select the user to which to grant access to run the processing group.

4.  Click **Close** to save your changes.

#### Disable a processing group

1.  Open **Data import export framework** &gt; **Setup** &gt; **Setup of roles for processing group**.
2.  Select a processing group, click **Disable**, and then click **Close**.

#### Set a processing group to run against a single company

By default, all processing groups can be run against all companies. To restrict a processing group so that it runs on a single company, follow these steps.

1.  Open **Data import export framework** &gt; **Common** &gt; **Processing group**.
2.  Select a processing group, expand the menu, and then click **Company**.
3.  In the **Company** form, select the first row, click **Delete**, and then click **New**.
4.  Select the company to restrict the processing group to, and then click **Close**.

### Preview errors before processing

Before you run a job to copy data from source to staging, you can preview the process to determine whether errors will be generated.

1.  Open **Data import export framework** &gt; **Common** &gt; **Processing group** &gt; **Entities**.
2.  In the **Select entities for processing group** form, click **Preview source file**.The **Preview** field lists the rows that can be processed. An Infolog displays the number of rows that have errors.
3.  To view the errors, either click **Log** in the Infolog, or click **Preview error details** in the **Select entities for processing group** form.The **Log text** field lists any rows that could not be processed.

### Process export data

You can export data so that it can be used in another Microsoft Dynamics AX instance. Alternatively, you can export data to a flat file so that it can be imported into another system. You can also export a processing group or the staging data from a processing group.

#### Export to Microsoft Dynamics AX

To export data to Microsoft Dynamics AX, follow these steps.

1.  Open **Data import export framework** &gt; **Common** &gt; **Processing group**. Select the processing group to work with. The processing group must contain only entities that have a source data format type of **AX**.
2.  Click **Get staging data**.
3.  In the **Create a job ID for staging data job** form, click **OK**.
4.  In the **Staging data execution** form, click **Run**.
5.  In the **Staging** form, change any job execution parameters that require changes, and then click **OK**.
6.  Click **Export to AX**.
7.  In the **Export options** form, enter the path and name of the .dat file to create, and then click **OK**.

#### Export to a file

To export data to a file, follow these steps.

1.  Open **Data import export framework** &gt; **Common** &gt; **Processing group**. Click **New** to create a new processing group.
2.  Select the new processing group, and then click **Entities**.
3.  In the **Select entities for processing group** form, add an entity that have a source data format type of text file.
4.  In the **Sample file path** field, enter the location of a sample file. This file is used to determine the format of the exported data. Only the structure of the file is used. Any data that the file contains is ignored. The format of this file must match the structure of the Microsoft Dynamics AX data that you are exporting. **Note:** You can use the demo files that are provided with the Data Import/Export Framework as sample files. For example, to export the **Barcode setup entity** to a file, you can use the **BarcodeSetupEntity.txt** file to provide the format for the export data file. For more information about the demo files, see [Demo files for the Data import/export framework (DIXF, DMF)](demo-files-dixf.md).
5.  Click **Generate source mapping**.
6.  Repeat steps 3 through 5 to add other entities as required. When you have finished, click **Close**.
7.  Open **Data import export framework** &gt; **Common** &gt; **Processing group**. Select the processing group that should provide Microsoft Dynamics AX data. All entities in the processing group must map to the file formats that you created in the other processing group and must have a source data format type of **AX**.
8.  Click **Get staging data**.
9.  In the **Create a job ID for staging data job** form, record the job ID, and then click **OK**.
10. In the **Staging data execution** form, click **Run**.
11. In the **Staging** form, change any job execution parameters that you want to change, and then click **OK**.
12. Click **Export to file**.
13. In the **Create a job ID for staging data job** form, select the job ID of the staging data job, and then click **OK**.
14. In the **Entity export details** form, in the **Processing group** field, select the processing group that contains the text file formats. (You created this processing group in steps 1 through 6 of this procedure.)
15. Click **Run**.
16. In the **Export to flat file** form, change any job execution parameters that you want to change, and then click **OK**.

#### Export a processing group

If you run the Data Import/Export Framework in multiple environments, you might want to export a processing group. When you export a processing group, you export the entities in the group, the mappings that you have set for the entities, and the staging data.

1.  Open **Data import export framework** &gt; **Common** &gt; **Processing group**.
2.  Select a processing group, and then click **Export to AX**.
3.  In the **Export options** form, enter the path and name of the .dat file to create, and then click **OK**.

#### Export staging data

If you run the Data Import/Export Framework in multiple environments, you might want to export staging data. When you export staging data, you create a file of staging data that you can import into another environment.

1.  Open **Data import export framework** &gt; **Common** &gt; **Processing group**.
2.  Select a processing group.
3.  Click **Execution history**, click **View staging data**, and then click **Export to file**.
4.  In the **Export to flat file** form, on the **General** tab, select a processing group. On the **Batch** tab, change any job execution parameters that you want to change, and then click **OK**.

### Process import data

This section describes how to import data by copying it from source to staging and then from staging to target.

#### Copy data from source to staging

You can copy data from source to staging, one processing group at a time.

1.  Open **Data import export framework** &gt; **Common** &gt; **Processing group**. Select the processing group to work with.
2.  Click **Get staging data**. The **Create a job ID for the staging data job** dialog box opens.
3.  By default, an ID is generated for the job. You can optionally modify the ID and add a description. Click **OK**. The **Staging data execution** dialog box opens.
4.  Under **Entity details**, enter the path of the file that contains all the source data, not just sample data.
5.  Click **Run**. In the **Get data from source to staging** dialog box, select **Batch processing** to run the job as part of a batch, or click **OK** to run the job immediately. The source data is copied to the staging tables.

#### Validate the data in staging

After the job has finished running, follow these steps to validate the data in staging.

1.  Open **Data import export framework** &gt; **Common** &gt; **Processing group**. Click **Execution history**, and then select the job that ran.
2.  Click **View staging data**.
3.  Review the staging data to validate that it matches the source file.
4.  Click **Validate** to verify that all the related reference data is correct and present in the system.
5.  Optional: Modify the staging data if changes are required.

#### Process data from staging to target

You can copy data from staging to target, one processing group at a time.

1.  Open **Data import export framework** &gt; **Common** &gt; **Processing group**. Select the processing group to work with.
2.  Click **Copy data to target**. The **Select a job ID to run** dialog box opens.
3.  Select a job. By default, the processing group is run for all rows. To limit the rows, in the **Run for** field, select **Criteria**, and then select which rows to run the job for. You can select **Rows with previous errors**, **Rows selected by the user**, or both.
4.  Click **OK**. The **Target data execution** form opens.
5.  To improve performance, consider setting the **Number of batch tasks** field. The total number of records is then split into the specified number of batch tasks, and those tasks are run at the same time, if resources are available.
6.  To run the job immediately, click **Run**. To run the job as part of a batch, click **Batch processing**. The data is copied to the target entities.

#### Validate the data in target

After the job has finished running, follow these steps to validate the data in target.

1.  Open **Data import export framework** &gt; **Common** &gt; **Processing group**.
2.  Click **Execution history **and review the status of the job.

#### Clean up staging data

After you have finished migrating your data, you should clean up the staging tables. Open **Data import export framework** &gt; **Periodic** &gt; **Staging cleanup** to identify data that you no longer require.

