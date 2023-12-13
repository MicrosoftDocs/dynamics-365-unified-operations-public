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
Fact data is a combination of multiple sources or must have some level of transformation done to get data into the proper structure for planning. When loading production data, it's recommended to use dataflows. Dataflows better supports typical production volume and complexity. Dataflows also provide a transform experience, detailed status results when loading data, and the option to schedule refreshes of the data.

Dataflows are a self-service, cloud-based data preparation technology. Dataflows enable customers to ingest, transform, and load data into Microsoft Dataverse environments, Power BI workspaces, or your organization's Azure data lake storage account. Dataflows are authored using Power Query, a unified data connectivity and preparation experience featured in many Microsoft products, including Excel and Power BI. Customers trigger dataflows to run either on demand or automatically on a schedule and data is always kept up to date. For more information, see [An overview of dataflows across Microsoft Power Platform and Dynamics 365 products](/power-query/dataflows/overview-dataflows-across-power-platform-dynamics-365).

Dataflows can populate dimensions and cubes within planning. When a dataflow is linked to the dimension or cube, when the data source of the dataflow is updated, planning is updated based on the refresh frequency defined in the dataflow.

## Populate dimensions and cubes

To use dataflows to populate dimension or cube values, follow these steps:

1. In Power Apps, create the dimension or cube in planning before creating the dataflow:
     - Note the table name for the cube and the dimension. For example: Msdyn\_xpna\_CUBENAME or Msdyn\_xpna\_dimDimensionName.
2.  When creating the data flow map for:
     - The cube load - confirm the columns in the cube are mapped to the dimensions selected when the cube was created.
     - The dimension load - confirm that the columns in the dimension are mapped to the dimension attributes selected when the dimension was created.
3.  When creating a dataflow for:
     - A cube load -  select the key for the cube in **Column mapping** section. The key will be the DimensionSetAltKey.
     - A dimension load - select the key for the dimension in the **Column mapping** section.
    
After the data flow is linked to the planning cube, you can specified an optional refresh.

To load data using a dataflow, the dimension or the cube must already have been created in planning. For more information, see [Microsoft Dynamics 365 Finance business performance planning dimensions](Dimensions.md) and [Create cubes](create-cubes.md).

### Example

Below is an example of how to create a dataflow when loading fact data into a cube. 

To create the cube in planning, follow these steps: 
1.  In the **Cube list**, select **New cube**.
2.  Enter a **Cube name**.
3.  Select the **Dimensions** that will be a part of the cube. A minimum of two dimensions are required.
4.  Select **Next** and **Create** the cube.

>[!Tip]
>The name of the cube will be needed to create the dataflow. It will start with msdyn\_xpnacube. 

### Create the dataflow in Power Apps 

1.  Go to Power Apps for your environment.
2.  Select dataflows: For more information about dataflows, see [Create and use dataflows in Microsoft Power Platform](/power-apps/maker/data-platform/create-and-use-dataflows).
    - Any data connection can be used. In this example, Excel is selected.
3.  Enter a name for the dataflow.
4.  Select the source of the data. For example, select Excel. For more information about troubleshooting connection issues, see [Create and use dataflows](/power-apps/maker/data-platform/create-and-use-dataflows#troubleshooting-data-connections).
5.  In the left side, select the data to work with.
6.  Select **Transform data**.
7.  In the **Transform data** page, columns can be combined, updated, or removed. For example, you may want to remove rows from the fiscal year of 2021, or for an obsolete product. For more information about transforming data, see [Transform data](/power-apps/maker/data-platform/create-and-use-dataflows#use-the-dataflow-editor-to-shape-or-transform-data).
8.  After the data is transformed, select **Next**.
9.  In the **Map tables** page, under **Load setting**, select ‘**Load to existing table’**.
10.  Select a **Destination table**.

>[!Important]
>The cube created in planning and is be named msdyn\_xpnacube\_<cube\_name>. The name of the cube is found on the **Cube** page in planning.
>Go to the cube, note the **Write back table** name under **Cube properties**.

10. After the planning cube is selected as the destination table, the **Source key** and **Column mapping section** is enabled. The source key is the DimensionSetAltKey for cubes. For the dimensions, it's the NameKey (msdyn\_name).
11. The column mapping section reflects the **Source columns** and **Destination columns**. The source columns are the data from fact data loaded into the dataflow. The destination columns are the dimensions selected as part of the cube creation in the planning app. To ensure that data is populated into the destination column, map a source column to it.

>[!Important]
>If you selected a key at the top of the **Column mapping** page, that column must be mapped to a destination column.

12. After the appropriate source columns are mapped to a destination column, select **Next**.
The **Comment** field doesn't need to be mapped.

You can refresh the dataflow manually or schedule a refresh cadence. For more information about refresh settings, see [Set the refresh frequency](/power-apps/maker/data-platform/create-and-use-dataflows#set-the-refresh-frequency).


#### Recommendations

When importing data in the **Data transformation** page, the following is recommended:
 - If you're using headings in your data, set **Use first row as headers** in the **Transform** section.
 - When the planning app creates dimensions and cubes, the primary columns are referenced and are typically string fields. When mapping columns for the data load, confirm that the column types match between the source and the destination column types. For example, in the planning app, many of the dimensions references are by name and are type **Text**. For the account dimension, the account number needs to be a type of **Text**. This can be changed by selecting the icon to the left of the column header. If the type isn't changed, an error is diplayed: 

Error Code: Mashup Exception Data Format Error, Error Details: Couldn't refresh the entity because of an issue with the mashup document MashupException.Error: DataFormat.Error: We couldn't convert to Number. Details: Reason = DataFormat.Error;Detail = XHDCOU;Microsoft.Data.Mashup.Error.Context = User.

 - To add another column to an existing dimension, add the new column in planning first. Go to **Dimension**, select **New column**. Populate the data from dataflows by following the steps listed above. You only need to select the primary column and the new column in the table mapping. Only the mapped columns are updated.
 - If you don't know what the key is for the cube that you're importing into, go to Power Apps and select TablesCustom<Table name>. Double-click on the table nameSchemaKeys.
 - If you are unsure what the key is for the dimension that you're importing into, go to Power Apps and select TablesCustom<Table name>PropertiesPrimary column (DIMENSIONS).
