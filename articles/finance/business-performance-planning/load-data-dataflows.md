---
# required metadata

title: Load data into Business performance planning using dataflows
description: This article describes how to load data ino the Business performance planning application.
author: ShielaSogge
ms.date: 12/13/2023
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 

# ms.tgt_pltfrm: 
ms.custom: 7521
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2023-12-03
ms.dyn365.ops.version: Human Resources

---
# Load data into Business performance planning using dataflows

[!include [banner](../includes/banner.md)]

## Loading data via dataflows
Fact data is a combination of multiple sources or must have some level of transformation done to get data into the proper structure for planning. If loading production data it is recommended to use dataflows, this will better support typical production volume and complexity. Dataflows also provide a transform experience, detailed status results when loading data, and the option to schedule refreshes of the data.

Dataflows are a self-service, cloud-based data preparation technology. Dataflows enable customers to ingest, transform, and load data into Microsoft Dataverse environments, Power BI workspaces, or your organization's Azure Data Lake Storage account. Dataflows are authored by using Power Query, a unified data connectivity and preparation experience already featured in many Microsoft products, including Excel and Power BI. Customers can trigger dataflows to run either on demand or automatically on a schedule; data is always kept up to date. Learn more about dataflows: [An overview of dataflows across Microsoft Power Platform and Dynamics 365 products - Power Query | Microsoft Learn](https://learn.microsoft.com/en-us/power-query/dataflows/overview-dataflows-across-power-platform-dynamics-365)

Dataflows can be used to populate dimensions and cubes within planning. One of the benefits of linking a dataflow to the dimension or cube, is that when the data source of the dataflow is updated with new data, the planning application will be updated based on the refresh frequency defined in the dataflow.

## Populate dimensions and cubes

To use dataflows to populate dimension or cube values, follow these steps:

1. In Power Apps, create the dimension or cube in the planning application before creating the dataflow:
     - Note the table name for the cube and the dimension - for example: Msdyn\_xpna\_CUBENAME or Msdyn\_xpna\_dimDimensionName
2.  When creating the data flow map for:
     - the cube load - confirm the columns in the cube map to the dimensions that were selected when the cube was created.
     - the dimension load - confirm that the columns in the dimension map to the dimension attributes that were selected when the dimension was created.
3.  When creating a data flow for:
     - a cube load -  select the key for the cube in **Column mapping** section. The key will be the DimensionSetAltKey.
     - a dimension load - select the key for the dimension in the **Column mapping** section.
    
After the data flow is linked to the planning cube, an optional refresh can be specified.

To load data using a dataflow, the dimension or the cube must already have been created in the planning application. For more information, see [Microsoft Dynamics 365 Finance business performance planning dimensions](dimensions.md) and [Create cubes](create-cubes.md).


### Load data into a cube example

Below is an example of how to create a dataflow when loading fact data into a cube. 

#### Create the cube in the planning application

1.  Go to the **Cube list**, select **New cube**.
2.  Enter the **Cube name**.
3.  Select the **Dimensions** that will be a part of the cube. A minimum of two dimensions are required.
4.  Select **Next** and **Create** the cube.

>[!Tip]
>The name of the cube will be needed to create the data flow. It will start with msdyn\_xpnacube. 

### Create the dataflow in the Power Apps 

1.  Go to Power Apps for your environment.
2.  Select dataflows – For more information about dataflows, see [Create and use dataflows in Microsoft Power Platform](/power-query/dataflows/create-use)
    - Any data connection can be used. In this example, Excel was selected.
3.  Enter a name for the data flow.
4.  Select the source of the data. For example, choose Excel and enter in the appropriate credentials. For more information about troubleshooting connection issues, see [Create and use dataflows](/power-apps/maker/data-platform/create-and-use-dataflows.md#troubleshooting-data-connections).
5.  In the left side, select the data to work with. For example, this is the Excel workbook sheet or a table of data.
6.  Select **Transform data**.
7.  In the **Transform data** page, columns can be combined, updated, or removed. For example, you may want to remove rows that are from the fiscal year of 2021, or for a product that is no longer being produced going forward. For more information about transforming data, see [Transform data](/power-apps/maker/data-platform/create-and-use-dataflows.md#use-the-dataflow-editor-to-shape-or-transform-data).
8.  After the data is transformed, select **Next**.
9.  In the **Map tables** page, under **Load setting**, select ‘**Load to existing table’**. A **Destination table** needs to be selected.

>[!Important]
>This is the cube created in the planning application and is be named msdyn\_xpnacube\_<cube\_name>. You can find the name of the cube in the **Cube** page in the planning app.
>Go to the cube and note the **Write back table** name under **Cube properties**.

10. After the planning cube is selected as the destination table, the **Source key** and **Column mapping section** will be enabled. The source key will be be the DimensionSetAltKey for cubes. For the dimensions, it will be the NameKey (msdyn\_name)
11. The column mapping section will reflect the **Source columns** and **Destination columns**. The source columns are the columns of data from fact data loaded into the dataflow. The destination columns are the dimensions that were selected as part of the cube creation in the planning app. To ensure that data is populated into the destination column, a source column must be mapped to it.

>[!Important]
>If you selected a key at the top of the **Column mapping** page, that column must be mapped to a destination column.

12. After the appropriate source columns have been mapped to a destination column, select **Next.**

You can leave the comment field unmapped.

You can choose to refresh the dataflow manually or schedule a refresh cadence. For more information about refresh settings, see[Set the refresh frequency](/power-apps/maker/data-platform/create-and-use-dataflows.md#set-the-refresh-frequency).


#### Recommendations

When importing data in the data transformation page, it's recommended: 
 - If you are using headings in your data, set **Use first row as headers** in the **Transform** section.
 - When the planning app creates dimensions and cubes, everything is referenced by the primary columns, which are typically string fields. When mapping columns for the data load, confirm that column types match between the source and the destination column types. For example, in the planning app, many of the dimensions references are by name and are type **Text**. For the account dimension, the account number would need to be set to a type of **Text**. This can be changed by selecting the icon to the left of the column header. If the type is not changed, this could result in an error: Error Code: Mashup Exception Data Format Error, Error Details: Couldn't refresh the entity because of an issue with the mashup document MashupException.Error: DataFormat.Error: We couldn't convert to Number. Details: Reason = DataFormat.Error;Detail = XHDCOU;Microsoft.Data.Mashup.Error.Context = User.
 - A common scenario is adding another dimension attribute to an already created dimension. To add another column to the dimension, add the new column in the planning app first. Go to **Dimension**, select **New column**. Populate the data from dataflows by following the steps listed above. You only need to select the primary column and the new column in the table mapping. Only the mapped columns will be updated. Any unmapped columns will remain unchanged.
 - If you are unsure what the key is for the cube that you are importing into, go to Power Apps and select TablesCustom<Table name>Double click on the table nameSchemaKeys. If you are unsure what the key is for the dimension that you are importing into, go to Power Apps and select TablesCustom<Table name>PropertiesPrimary column (DIMENSIONS).
