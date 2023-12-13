---
# required metadata

title: Load data into Business performance planning using dataflows
description: This article describes how to load data ino the Business performance planning application.
author: ShielaSogge
ms.date: 12/08/2023
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

The following steps are required to use dataflows to populate dimension or cube values

1.  A user with access to the Power Apps home page
2.  Create the dimension or cube manually in the planning application before creating the dataflow
    1.  Capture the resulting Table Name for the cube (Example: Msdyn\_xpna\_CUBENAME)
    2.  Capture the resulting Table name for the dimension (Example: Msdyn\_xpna\_dimDimensionName
3.  When creating the dataflow map for a cube load, ensure that the columns in the cube map to the dimensions that were selected when the cube was created.
4.  When creating the data flow map for the dimension load, ensure that the columns in the dimension map to the dimension attributes that were selected when the dimension was created.
5.  When creating a dataflow for a cube load, you will need to choose the Key for the cube in the Column mapping section, the key will be the DimensionSetAltKey
6.  When creating a dataflow for a dimension load, you will need to choose the Key for the dimension in the Column mapping section, the key will be the

Once the data flow is linked to the planning cube, an optional refresh can be specified.

To load data via a dataflow, the dimension or the cube must already have been created in the planning application. To see learn more about dimensions and cubes refer to the dimension (NEED LINK TO TOPIC) and cube (NEED LINK TO TOPIC) topics.

Listed below is an example of how to create a dataflow when loading fact data into a cube.

### Create the cube in the planning application

1.  To begin, navigate to the **Cube list** and choose **New cube**
2.  Enter the **cube name**
3.  Select the **dimensions** that will be a part of the cube (At least 2 dimensions are required)
4.  Select **next** and **create** the cube.

Tip: Note the name of the cube, it will start with msdyn\_xpnacube. This will be needed when creating the dataflow.

### Create the dataflow in the Power Apps home page

1.  Navigate to the Power Apps home page for your environment.
2.  Select dataflows – To learn more about dataflows: [Create and use dataflows in Microsoft Power Platform - Power Query | Microsoft Learn](https://learn.microsoft.com/en-us/power-query/dataflows/create-use)
    1.  While you can use any data connection, we will assume that for this example, Excel was selected.
3.  Give the dataflow a name.
4.  Select the source of the data. For example, choose Excel and enter in the appropriate credentials. For troubleshooting connection issues see: https://learn.microsoft.com/en-us/power-apps/maker/data-platform/create-and-use-dataflows#troubleshooting-data-connections
5.  In the left side select the data that you want to work with. For example, this might be an Excel workbook sheet or a table of data.
6.  Select **Transform data**.
7.  Within the Transform data form, columns can be combined, updated, or removed. For example, you may want to remove rows that are from the fiscal year of 2021, or for a product that is no longer being produced going forward. Learn more about transforming data here: [https://learn.microsoft.com/en-us/power-apps/maker/data-platform/create-and-use-dataflows#use-the-dataflow-editor-to-shape-or-transform-data](https://learn.microsoft.com/en-us/power-apps/maker/data-platform/create-and-use-dataflows#use-the-dataflow-editor-to-shape-or-transform-data)
8.  Once the data is transformed, select **Next**
9.  In the **Map tables** form, under Load setting, select ‘**Load to existing table’**. A **destination table** needs to be selected.

!Important

This will be the cube that was created in the planning application and will be named msdyn\_xpnacube\_<cube\_name>. Note: You can find the name of the cube in the **Cube** form in the planning app. Navigate to the cube and note the **Write back table** name under **Cube properties**.

1.  Once the planning cube is selected as the destination table, the **Source key** and **Column mapping section** will be enabled. The source key will be be the DimensionSetAltKey for Cubes. For the dimensions, it will be the NameKey (msdyn\_name)
2.  The column mapping section will reflect the **source columns** and **destination columns**. The source columns are the columns of data from fact data loaded into the dataflow. The destination columns are the dimensions that were selected as part of the cube creation in the planning app. To ensure that data is populated into the destination column, a source column must be mapped to it.

!Important

If you selected a Key at the top of the column mapping form, that column must be mapped to a destination column.

1.  Once the appropriate source columns have been mapped to a destination column, select **Next.**

Tip! You can leave the comment field unmapped.

1.  You can choose to refresh the dataflow manually or schedule a refresh cadence. To learn more about refresh settings: [https://learn.microsoft.com/en-us/power-apps/maker/data-platform/create-and-use-dataflows#set-the-refresh-frequency](https://learn.microsoft.com/en-us/power-apps/maker/data-platform/create-and-use-dataflows#set-the-refresh-frequency)

Tips

1.  When importing data, in the data transformation form, here are a few tips:
    1.  If you are using headings in your data, set ‘Use first row as headers’ in the transform section of the menu.
    2.  When the planning app creates dimensions and cubes, everything is referenced by the primary columns, which are typically string fields. Therefore, when mapping columns for the data load, make sure that column types match between the source and the destination column types. For example, in the planning app, many of the dimensions references are by name, which are of type of ‘Text’. This would mean that for the Account dimension, the Account number would need to be set to a type of ‘Text’. This can be changed by selecting the icon to the left of the column header. Not changing the type could result in an error similar to this: Error Code: Mashup Exception Data Format Error, Error Details: Couldn't refresh the entity because of an issue with the mashup document MashupException.Error: DataFormat.Error: We couldn't convert to Number. Details: Reason = DataFormat.Error;Detail = XHDCOU;Microsoft.Data.Mashup.Error.Context = User
2.  A common scenario is needing to add another dimension attribute to an already created dimension. To add another column to the dimension, you need to add the new column in the planning app first. Navigate to the **dimension** and select **New column**. Next, you will need to populate the data from dataflows. Follow the steps listed above on creating dataflows. However, you only need to select the primary column and the new column in the table mapping. Only the mapped columns will be updated. Any unmapped columns will remain unchanged.
3.  If you are unsure what the key is for the CUBE that you are importing into, you can navigate to the Power Apps home page and select TablesCustom<Table name>Double click on the table nameSchemaKeys. If you are unsure what the key is for the DIMENSION that you are importing into, you can navigate to the Power Apps home page and select TablesCustom<Table name>PropertiesPrimary column (DIMENSIONS)
