---
title: View and customize tables for holding imported data
description: Data imported into Demand planning must be loaded into tables that are set with the fields and relations needed to accommodate the incoming data. This topic describes the predefined tables provided with the app and explains how to customize them and create new ones.
author: t-benebo
ms.author: benebotg
ms.reviewer: kamaybac
ms.search.form:
ms.topic: overview
ms.date: 10/19/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# View and customize tables for holding imported data

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../includes/preview-banner.md)]

Data imported into Demand planning must be loaded into tables that are set with the fields and relations needed to accommodate the incoming data. Demand planning includes a set of predefined tables that support the most useful standard data that you would probably want to import from Supply Chain Management. If you've customized your tables in Supply Chain Management, you can reproduce your custom fields using the tools provided. You can also create new custom tables to store data from Supply Chain Management and other sources.

## View tables

To see the full list of tables available to the Demand planning app, select **Tables** on the navigation pane. Here, each table is listed by name.

- The **Name** columns shows the name of each table. Select a table name to view and edit details about that table, including column definitions, relationships, and data.
- The **Is System** column tells whether each table is a standard table provided by the system or a custom table added by a user. It shows one of the following values:
    - *Yes* – The table is a system table and can't be deleted.
    - *No* – The table is a custom table added by a user. You can delete these tables if you don't need them anymore.

> [!NOTE]
> Tables holding prices aren't marked as systems tables.

## Standard tables

Demand planning includes a set of predefined *system tables* that support the most useful standard data that you would probably want to import from Supply Chain Management. Most of the system tables represent important data imported from Supply Chain Management. However, many of these tables are modified slightly in Demand planning with minor name changes and extra columns. This section lists these important tables and how they are modified in Demand planning.

### Site Location table

Sites and warehouses are implemented as a hierarchy. Site is the parent, and a site can have one or more warehouses. This concept is inherited from Supply Chain Management.

To import sites from Supply Chain Management, export an Excel file from the **Sites V2** data entity in Supply Chain Management and then import that file into Demand planning.

In the current release, only one-level relations are supported in transformations. This means that the **Site location** table and its data cannot be used in transformation. Site ID values can still be obtained from the **Warehouse Location** table.

### Warehouse Location table

The **Location** table from Supply Chain Management is renamed to **Warehouse Location** in Demand planning.

Local columns named **Operation Site ID** and **Site Location ID** have also been added to the **Warehouse Location** table in Demand planning. These extra columns let you generate forecasts based on warehouse and/or site location ID.

You can derive site IDs by applying a warehouse location ID to the historical demand.

To import warehouses from Supply Chain Management, export an Excel file from the **Warehouses** data entity in Supply Chain Management and then import that file into Demand planning.

### Customer Accounts table

**Customer Accounts** is a new table that lets you import customers and related details such as customer group, address information (such as country/region), and so on.

This table lets you generate forecasts based on customer, customer group, and/or customer country.

To import customer accounts from Supply Chain Management, export an Excel file from the **Customer definitions** data entity in Supply Chain Management and then import that file into Demand planning.

### Legal Entity table

The **Legal Entity** table stores information about legal entities and related details. You'll usually import this data from Supply Chain Management.

This table lets you generate forecasts across legal entities, but also lets you slice forecasts according to the owning legal entity.

To import legal entities from Supply Chain Management, export an Excel file from the **Legal entities** data entity in Supply Chain Management and then import that file into Demand planning.

> [!NOTE]
> When you export forecasts back into Supply Chain Management for use in supply planning, you must include the **Legal Entity ID** column because supply planning is performed per legal entity in Supply Chain Management.

### Product table

The **Product** table stores product information and related details. You'll usually import this data from Supply Chain Management.

The **Product** table supports both *Product* and*Service* product types.

You can forecast on products and product variants as a hierarchy, which means you can get an aggregate of product variants.

You can add columns for color ID, size ID, style ID, and configuration ID to the forecast. This will allow you to slice the forecast across products variants. For example, you could forecast demand for all silver LCD TVs across sizes.

To import products from Supply Chain Management, export an Excel file from the **Distinct products or product variants** data entity in Supply Chain Management and then import that file into Demand planning. This entity is only available in Supply Chain Management version 10.0.32 and later.

### Historical Demand table

The **Historical Demand** table stores information about historical demand in the form of orders. Each order includes a buyer and seller, which caters both to external sales and inter-company trade. An order can also be internal (same buyer and seller). You'll usually import this data from Supply Chain Management.

The **Historical Demand** table includes an **Order Type** column, which classifies the origin of the demand (*Sales*, *Transfer*, or*Production*). Sales returns are classified as sale with a negative quantity.

When you install and enable Demand planning, a new data entity named **HistoricalSalesDemandEntity** is added to Supply Chain Management. This entity lets you export historical sales based on the data available on the Sales packing slip.  

To import historical sales from Supply Chain Management, export an Excel file from the **HistoricalSalesDemandEntity** data entity in Supply Chain Management and then import that file into Demand planning. This entity is only available in Supply Chain Management version 10.0.32 and later.

## Create or edit a table and its columns and relationships

You can create your own non-system tables or extend system tables by adding extra non-system columns. Custom tables and columns can be used in Demand planning equally as system tables and columns. For example, you could add important signals such as weather data, inflation stats, or other macro-economic data.

To create or edit a table, follow these steps:

1. On the navigation pane, select **Configurations &gt; Tables**.

1. Do one of the following steps:
    - To add a new non-system table, select **New** from the Action Pane.
    - To edit an existing table, select a link in the **Name** column.
    - To delete one or more existing non-system table, select the check box next to the names of the target tables and then select **Delete** from the Action Pane.

1. Open the **General** tab and make the following settings:
    - **Name** – For new tables, enter the table name. For existing tables, this is read only.
    - **Owner** – Select the user account, master data manager or similar role, that owns the table.
    - **Key** – Identify one or more columns whose combined values will uniquely identify each row in the table. If you're making a new table, then you won't be able to make this setting until after you've added the column(s) you will use as keys. This is important for avoiding creating duplicate records with each import.

1. On the Action Pane, select **Save**.

1. Open the **Columns** tab. Here you can see the name, data type, and system status of each column. Use buttons on the toolbar to add new columns or delete existing non-system columns. Each column must have a **Name** and a **Data Type**.

    > [!NOTE]
    > To be able to transform a table and its data into a time series, the table must include at least three types of columns:
    >
    > - 1 *timestamp* column (DateTime)
    > - 1 *measure* column (Decimal or Integer)
    > - 1 *dimension* column (String)

1. If necessary, go back to the **General** tab and identify your **Key** column(s).

1. Open the **Relationships** tab. Relationships between tables let you construct a data model suitable for your organization's needs. As with tables and columns, pre-defined system relationships are required and are therefore marked with **Is System** set to *Yes*. You can also add custom relationships as needed (with **Is System** set to *No*). System relationships can't be deleted or changed.

    Each relationship links two tables together, which enables you to match related information stored in different tables. Only columns from related tables can be selected in transformation. You can set up both *many to one* and*many to many* relationships. In the case of a*many to many* relationship, the system will display first matching record

    Relations are currently *directional*, so it is important to pay attention to which table is the**From Table** and which is the **To Table**. Often, the **From table** will be a transactional table like **Historical Demand**.

    ![A close up of a white background Description automatically generated](media/image5.png)

1. To add a new relationship, select **New Relationship** from the toolbar and then make the following settings in the **Quick Create: Relationship** dialog:
    - **From Table** – This is the current table. It's usually a table that holds transaction data.
    - **From Column** – Select the field from the **From table** that holds values to be matched in the related table.
    - **To Table** – Select the target table that contains the data you want to relate to.
    - **To Column** – Select the target field, which holds data values that will be matched to the value found in the **From Column**.

1. Select **Save and Close**.

    All relationships are *Active* by default, which means that columns from related tables can be selected in transformation. You can change the activation status of a relationship, or delete the relationship entirely by selecting it on the **Relationship** tab and selecting the appropriate action on the toolbar.

1. Open the **Data** tab to inspect the data your table contains.

1. Select **Save** on the Action Pane to save your changes.

## Delete all records in a table

If necessary, you can delete all the records from a selected table while keeping the table schema and its and relationships. This can be useful if you need to correct wrongly imported data.

To delete all the records in a table, follow these steps:

1. On the navigation pane, select **Configurations &gt; Tables**.
1. In the **Name** column, select the name of the target table.
1. On the Action Pane, select **Delete Data**.
1. Select **OK** to confirm the deletion.
