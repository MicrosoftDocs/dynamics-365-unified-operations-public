---
title: View and customize tables for holding imported data
description: To accommodate data that is imported into Demand planning, tables must be set up with the required fields and relations.
author: t-benebo
ms.author: benebotg
ms.topic: overview
ms.date: 02/20/2024
ms.custom: bap-template
ms.reviewer: kamaybac
ms.search.form:
---

# View and customize tables for holding imported data

[!include [banner](../includes/banner.md)]

Data that's imported into Demand planning must be loaded into tables that are set with the fields and relations that are required to accommodate the incoming data. Demand planning includes a set of predefined tables that support the most useful standard data that you'll probably want to import from Microsoft Dynamics 365 Supply Chain Management. If you've customized your tables in Supply Chain Management, you can use the tools that are provided to reproduce the custom fields. You can also create new custom tables to store data from Supply Chain Management and other sources.

## View tables

To view the full list of tables that are available to Demand planning, select **Data management** \> **Tables and data** on the navigation pane. The tables are listed by name.

- The **Name** column shows the name of each table. Select a table name to view and edit details about that table, including column definitions, relationships, and data.
- The **Is System** column indicates whether each table is a standard table that's provided by the system or a custom table that was added by a user. It shows one of the following values:

    - *Yes* – The table is a system table. You can't delete these tables.
    - *No* – The table is a custom table that was added by a user. You can delete these tables if you no longer need them.

> [!NOTE]
> Tables that hold prices aren't marked as systems tables.

## Standard tables

Demand planning includes a set of predefined *system tables* that support the most useful standard data that you'll probably want to import from Supply Chain Management. Most system tables represent important data that's imported from Supply Chain Management. However, many of these tables are slightly modified in Demand planning through minor name changes and the addition of extra columns. This section lists these important tables and explains how they're modified in Demand planning.

### Site Location table

Sites and warehouses are implemented as a hierarchy. The site is the parent, and each site can have one or more warehouses. This concept is inherited from Supply Chain Management.

To import sites from Supply Chain Management, export an Excel file from the **Sites V2** data entity in Supply Chain Management, and then import that file into Demand planning.

In the current release, only one-level relations are supported in transformations. Therefore, the **Site location** table and its data can't be used in transformations. Site ID values can still be obtained from the **Warehouse Location** table.

### Warehouse Location table

The **Location** table from Supply Chain Management is renamed **Warehouse Location** in Demand planning. Local columns that are named **Operation Site ID** and **Site Location ID** have been added to the **Warehouse Location** table in Demand planning. These extra columns let you generate forecasts based on the warehouse and/or site location ID.

You can derive site IDs by applying a warehouse location ID to the historical demand.

### Customer Accounts table

**Customer Accounts** is a new table that lets you import customers and related details such as the customer group and address information (for example, country/region). This table also lets you generate forecasts based on the customer, the customer group, and/or the customer's country/region.

### Legal Entity table

The **Legal Entity** table stores information about legal entities and related details. Usually, you'll import this data from Supply Chain Management.

This table lets you generate forecasts across legal entities. It also lets you slice forecasts according to the owning legal entity.

> [!NOTE]
> When you export forecasts back into Supply Chain Management so that they can be used in supply planning, you must include the **Legal Entity ID** column, because supply planning is performed per legal entity in Supply Chain Management.

### Product table

The **Product** table stores product information and related details. Usually, you'll import this data from Supply Chain Management.

The **Product** table supports both *Product* and *Service* product types.

You can forecast on products and product variants as a hierarchy. In this way, you can get an aggregate of product variants.

You can add columns for color ID, size ID, style ID, and configuration ID to the forecast. In this way, you can slice the forecast across products variants. For example, you can forecast demand for all silver LCD TVs across sizes.

### Historical Demand table

The **Historical Demand** table stores information about historical demand in the form of orders. Each order includes a buyer and a seller, to cater to both external sales and intercompany trade. An order can also be internal. (In this case, the buyer and the seller are the same.) Usually, you'll import this data from Supply Chain Management.

The **Historical Demand** table includes an **Order Type** column that classifies the origin of the demand (*Sales*, *Transfer*, or *Production*). Sales returns are classified as sales that have a negative quantity.

## Create or edit a table and its columns and relationships

You can create your own non-system tables, or you can extend system tables by adding extra non-system columns. Custom tables and columns can be used in Demand planning just as system tables and columns can. For example, you can add important signals, such as weather data, inflation statistics, or other macroeconomic data.

To create or edit a table, follow these steps.

1. On the navigation pane, select **Data management** \> **Tables and data**.
1. Follow one of these steps:

    - To add a new non-system table, select **New** on the Action Pane.
    - To edit an existing table, select the link for it in the **Name** column.
    - To delete one or more existing non-system tables, select the checkbox next to the name of each table, and then select **Delete** on the Action Pane.

1. On the **General** tab, set the following fields:

    - **Name** – For new tables, enter the table name. For existing tables, this field is read-only.
    - **Owner** – Select the owner of the table (user account, master data manager, or a similar role).
    - **Key** – Specify one or more columns whose combined values will uniquely identify each row in the table. If you're creating a new table, you can't set this field until you add the columns that you'll use as keys. This limitation is important because it helps prevent duplicate records from being created at each import.

1. On the Action Pane, select **Save**.
1. On the **Columns** tab, you can view the name, data type, and system status of each column. Use the buttons on the toolbar to add new columns or delete existing non-system columns. Each column must have a **Name** value and a **Data Type** value.

    > [!NOTE]
    > To transform a table and its data into a time series, the table must include at least three columns:
    >
    > - One *timestamp* column (*DateTime* data type)
    > - One *measure* column (*Decimal* or *Integer* data type)
    > - One *dimension* column (*String* data type)

1. If you didn't specify key columns in step 3, go back to the **General** tab, and specify them.
1. Select the **Relationships** tab.

    Relationships between tables let you construct a data model that's suitable for your organization's needs. As for tables and columns, predefined system relationships are required. Therefore, the **Is System** field is set to *Yes* for them. You can also add custom relationships as you require. (Set the **Is System** field to *No* for these custom relationships.) System relationships can't be deleted or changed.

    Each relationship links two tables together. This link lets you match related information that's stored in different tables. Only columns from related tables can be selected in transformations. You can set up both *many-to-one* (n:1) and *many-to-many* (n:n) relationships. For *many-to-many* relationships, the system shows the first matching record.

    Relationships are currently *directional*. Therefore, it's important that you pay attention to which table is the "from" table and which is the "to" table. Often, the "from" table is a transactional table such as **Historical Demand**.

1. To add a new relationship, select **New Relationship** on the toolbar, and then set the following fields in the **Quick Create: Relationship** dialog box:

    - **From Table** – This table is the current table. It's usually a table that holds transaction data.
    - **From Column** – Select the field in the "from" table that holds values that should be matched in the related table.
    - **To Table** – Select the target table that contains the data that you want to relate to.
    - **To Column** – Select the field in the "to" table that holds data values that should be matched to the value that's found in the "from" column.

1. Select **Save and Close**.

    By default, all relationships are active. Therefore, columns from related tables can be selected in transformations. You can change the activation status of a relationship or completely delete the relationship. Select the relationship on the **Relationship** tab, and then select the appropriate button on the toolbar.

1. On the **Data** tab, inspect the data that your table contains.
1. Select **Save** on the Action Pane to save your changes.

## Delete all records in a table

As required, you can delete all the records from a selected table but keep the table schema and its relationships. This approach can be useful if you must correct data that was incorrectly imported.

To delete all the records in a table, follow these steps.

1. On the navigation pane, select **Data management** \> **Tables and data**.
1. In the **Name** column, select the name of the target table.
1. On the Action Pane, select **Delete Data**.
1. Select **OK** to confirm the deletion.

## Import data from Supply Chain Management

You can easily import data from Supply Chain Management into the standard tables by using the Finance and Operations connector. By default, all system (standard) entities are selected, and their fields are automatically mapped.

You can edit any relationship, unmap fields, or add custom field mappings as you require. Before you can import a custom field, you must add it in the standard table.

When you create an import job, an export data project for the required data entities is created in Supply Chain Management.

## Security configuration for custom entities

To allow data to be read from custom entities, you must configure their security settings in Dynamics 365 Supply Chain Management. To do so, follow these steps:

1. Go to **System Administration \> Security \> Security Configuration**.
1. Open the **Privileges** tab.
1. Select **Create new** from the toolbar.
1. In the dialog, add a **Name** for your new privilege, and then select **OK**.
1. Your new privilege is added to the list and selected. In the middle column, select **Entities**.
1. On the toolbar, select **Add references**.
1. In the dialog, find and select your custom entity. Select the access properties you want to grant and then select **OK**.
1. In the middle column, select **Duties**.
1. On the toolbar, select **Add references**.
1. In the dialog, find and select the duty named *View Document entity data for data management* or *Create data management project and details using entity*. Choose the duty based on the level of access you require.
    - *View Document entity data for data management* is commonly associated with entities used in the Data Management Framework in Supply Chain Management. It's typically assigned to the role *Data management migration user*, which is a subordinate role to *Demand planning app role*.
    - *Create data management project and details using entity* is part of the *Demand planning app role* role. *Demand planning app role* is assigned to *DemandPlanAppUser*, which is a user role often employed for integrating the Demand Planning Service with Supply Chain Management.

1. Select **OK** to add the selected duty to your new privilege.
1. Open the **Unpublished objects** tab. On the toolbar, select **Publish all**.
