# Tables

To see the full list of tables available to the Demand planning app, select **Tables** on the navigation pane. Here, each table is listed by name.

-   The **Name** columns shows the name of each table. Select a table name to view and edit details about that table, including column definitions, relationships, and data.

-   The **Is System** column tells whether each table is a standard table provided by the system or a custom table added by a user. It shows one of the following values:

    -   *Yes* – The table is a system table and can't be deleted.

    -   *No* – The table is a custom table added by a user. You can delete these tables if you don't need them anymore.

**Note**: Tables holding prices aren't marked as systems tables.

## Standard tables

There are a set of tables that are out-of-the box in the application. These are the most commonly used for demand planning.

Most of the system tables represent important data imported from Supply Chain Management. However, many of these tables are modified slightly in Demand planning with minor name changes and extra columns. This section lists these important tables and how they are modified in Demand planning.

## Site Location table

Sites and warehouses are implemented as a hierarchy. Site is the parent, and a site can have one or more warehouses. This concept is inherited from Supply Chain Management.

To import sites from Supply Chain Management, export an Excel file from the **Sites V2** data entity in Supply Chain Management and then import that file into Demand planning.

In the current release, only one-level relations are supported in transformations. This means that the **Site location** table and its data cannot be used in transformation. Site ID values can still be obtained from the **Warehouse Location** table.

## Warehouse Location table

The **Location** table from Supply Chain Management is renamed to **Warehouse Location** in Demand planning.

Local columns named **Operation Site ID** and **Site Location ID** have also been added to the **Warehouse Location** table in Demand planning. These extra columns let you generate forecasts based on warehouse and/or site location ID.

You can derive site IDs by applying a warehouse location ID to the historical demand.

To import warehouses from Supply Chain Management, export an Excel file from the **Warehouses** data entity in Supply Chain Management and then import that file into Demand planning.

## Customer Accounts table

**Customer Accounts** is a new table that lets you import customers and related details such as customer group, address information (such as country/region), and so on.

This table lets you generate forecasts based on customer, customer group, and/or customer country.

To import customer accounts from Supply Chain Management, export an Excel file from the **Customer definitions** data entity in Supply Chain Management and then import that file into Demand planning.

## Legal Entity table

The **Legal Entity** table stores information about legal entities and related details. You'll usually import this data from Supply Chain Management.

This table lets you generate forecasts across legal entities, but also lets you slice forecasts according to the owning legal entity.

To import legal entities from Supply Chain Management, export an Excel file from the **Legal entities** data entity in Supply Chain Management and then import that file into Demand planning.

**Note**: When you export forecasts back into Supply Chain Management for use in supply planning, you must include the **Legal Entity ID** column because supply planning is performed per legal entity in Supply Chain Management.

## Product table

The **Product** table stores product information and related details. You'll usually import this data from Supply Chain Management.

The **Product** table supports both *Product* and*Service* product types.

You can forecast on products and product variants as a hierarchy, which means you can get an aggregate of product variants.

You can add columns for color ID, size ID, style ID, and configuration ID to the forecast. This will allow you to slice the forecast across products variants. For example, you could forecast demand for all silver LCD TVs across sizes.

To import products from Supply Chain Management, export an Excel file from the **Distinct products or product variants** data entity in Supply Chain Management and then import that file into Demand planning. This entity is only available in Supply Chain Management version 10.0.32 and later.

## Historical Demand table

The **Historical Demand** table stores information about historical demand in the form of orders. Each order includes a buyer and seller, which caters both to external sales and inter-company trade. An order can also be internal (same buyer and seller). You'll usually import this data from Supply Chain Management.

The **Historical Demand** table includes an **Order Type** column, which classifies the origin of the demand (*Sales*, *Transfer*, or*Production*). Sales returns are classified as sale with a negative quantity.

When you install and enable Demand planning, a new data entity named **HistoricalSalesDemandEntity** is added to Supply Chain Management. This entity lets you export historical sales based on the data available on the Sales packing slip.  

To import historical sales from Supply Chain Management, export an Excel file from the **HistoricalSalesDemandEntity** data entity in Supply Chain Management and then import that file into Demand planning. This entity is only available in Supply Chain Management version 10.0.32 and later.

