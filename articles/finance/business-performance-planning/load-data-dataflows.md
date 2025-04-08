---
title: Load data into Business performance planning using dataflows
description: Learn how to use dataflows to load data into the Business performance planning application, including a process for populating dimensions and cubes.
author: ShielaSogge
ms.author: twheeloc
ms.topic: article
ms.date: 06/04/2024
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2023-12-03
ms.search.form: 
ms.dyn365.ops.version: Human Resources
---

# Load data into Business performance planning using dataflows

[!include [banner](../includes/banner.md)]

Fact data is a combination of multiple sources, or some level of transformation must be done to get the data into the correct structure for planning. When you load production data, we recommend that you use dataflows. Dataflows provide better support for typical production volume and complexity. They also provide a transformation experience, detailed status results when data is loaded, and the option to schedule refreshes of the data.

Dataflows are a self-service, cloud-based data preparation technology. They enable customers to ingest, transform, and load data into Microsoft Dataverse environments, Power BI workspaces, or your organization's Azure Data Lake Storage account.

Dataflows are authored by using Power Query. Power Query is a unified data connectivity and preparation experience that's featured in many Microsoft products, including Excel and Power BI. Customers trigger dataflows to run either on demand or automatically on a schedule, and data is always kept up to date. For more information, see [What are dataflows?](/power-query/dataflows/overview-dataflows-across-power-platform-dynamics-365)

Dataflows can populate dimensions and cubes in Business performance planning. After a dataflow is linked to a dimension or cube, when the data source of the dataflow is updated, Business performance planning is updated based on the refresh frequency that's defined in the dataflow.

## Populate dimensions and cubes

To use dataflows to populate dimension or cube values, follow these steps.

1. In Power Apps, create the dimension or cube in Business performance planning before you create the dataflow. Make a note of the table name for the cube or dimension. Here are some examples:

    - **Cube:** Msdyn\_xpna\_CUBENAME
    - **Dimension:** Msdyn\_xpna\_dimDimensionName

2. Follow one of these steps, depending on what you're creating the dataflow map for:

    - **For a cube load:** Confirm that the columns in the cube are mapped to the dimensions that were selected when the cube was created.
    - **For a dimension load:** Confirm that the columns in the dimension are mapped to the dimension attributes that were selected when the dimension was created.

3. Follow one of these steps, depending on what you're creating a dataflow for:

    - **For a cube load:** In the **Column mapping** section, select the key for the cube. The key will be the **DimensionSetAltKey** value.
    - **For a dimension load:** In the **Column mapping** section, select the key for the dimension.

After the dataflow is linked to the planning cube, you can specify an optional refresh.

A dataflow can be used to load data only if the dimension or cube has already been created in Business performance planning. For more information, see [Microsoft Dynamics 365 Finance business performance planning dimensions](Dimensions.md) and [Business performance planning cubes](create-cubes.md).

### Example

This example shows how to create a dataflow when you're loading fact data into a cube.

To create the cube in Business performance planning dimensions, follow these steps.

1. In the **Cube** list, select **New cube**.
2. Enter a name for the cube.
3. Select the dimensions that should be a part of the cube. You must select a minimum of two dimensions.
4. Select **Next**, and create the cube.

> [!NOTE]
> You will need the name of the cube to create the dataflow in Power Apps. The name will start with **msdyn\_xpnacube**.

### Load data using dataflows 

1. Select **Load data**, select **Create dataflow**. This launches the **Power Query** window.

>[!Important]
>The user must have the Dataflow Maker role assigned to be able to create the dataflow. If they don't have the role, the **Create dataflow** button isn't available.

2. Select dataflows. For more information about dataflows, see [Create and use dataflows in Power Apps](/power-apps/maker/data-platform/create-and-use-dataflows).

    Any data connection can be used. For this example, select Excel.

3. Enter a name for the dataflow.
4. Select the source of the data. For this example, select Excel. For more information about how to troubleshoot connection issues, see [Troubleshooting data connections](/power-apps/maker/data-platform/create-and-use-dataflows#troubleshooting-data-connections).
5. On the left, select the data to work with.
6. Select **Transform data**.
7. On the **Transform data** page, you can combine, update, or remove columns. For example, you might want to remove rows for the fiscal year 2021 or rows for an obsolete product. For more information about how to transform data, see [Use the dataflow editor to shape or transform data](/power-apps/maker/data-platform/create-and-use-dataflows#use-the-dataflow-editor-to-shape-or-transform-data).
8. After the data is transformed, select **Next**.
9. On the **Map tables** page, under **Load setting**, select **Load to existing table**.
10. Select the table listed. This should match the cube name on the **Cube** page.

    > [!IMPORTANT]
    > The cube that's created in Business performance planning is named msdyn\_xpnacube\_\<*cube\_name*\>. You can find the name of the cube on the **Cube** page in Business performance planning.



    After you select the planning cube as the destination table, **Source key** and **Column mapping** sections become available. The source key is the **DimensionSetAltKey** value for cubes. For dimensions, it's the **NameKey** value (**msdyn\_name**).

11. The **Column mapping** section reflects the source columns and destination columns. The source columns are the data from fact data that was loaded into the dataflow. The destination columns are the dimensions that were selected as part of cube creation in the Business performance planning application. To ensure that data is populated in the destination column, map a source column to it.

    > [!IMPORTANT]
    > If you selected a key at the top of the **Column mapping** section, that column must be mapped to a destination column.

12. After the appropriate source columns are mapped to destination columns, select **Next**.

    > [!NOTE]
    > The **Comment** field doesn't have to be mapped.

You can manually refresh the dataflow, or you can schedule a refresh cadence. For more information about refresh settings, see [Set the refresh frequency](/power-apps/maker/data-platform/create-and-use-dataflows#set-the-refresh-frequency).

#### Recommendations

When you import data on the **Data transformation** page, we recommend that you follow these guidelines:

- If you're using headings in your data, set the **Use first row as headers** option in the **Transform** section.
- When the Business performance planning application creates dimensions and cubes, the primary columns are referenced and are typically string fields. When you map columns for the data load, confirm that the source column types and destination column types match. For example, in the Business performance planning application, many dimension references are by name and are of the **Text** type. For the account dimension, the account number must be of the **Text** type. You can change the type by selecting the button to the left of the column header. If you don't change the type, you receive the following error message:

    > Error Code: Mashup Exception Data Format Error, Error Details: Couldn't refresh the entity because of an issue with the mashup document MashupException.Error: DataFormat.Error: We couldn't convert to Number. Details: Reason = DataFormat.Error;Detail = XHDCOU;Microsoft.Data.Mashup.Error.Context = User.

- To add another column to an existing dimension, first add the new column in Business performance planning. Go to **Dimension**, and select **New column**. Follow the steps earlier in this article to populate the data from dataflows. You only have to select the primary column and the new column in the table mapping. Only the mapped columns are updated.
- If you don't know what the key is for the cube that you're importing into, in Power Apps, select **Tables** on the left navigation pane and select **Custom**, and select the table name in the grid. Then, on the details page under **Schema**, select **Keys**.
- If you don't know what the key is for the dimension that you're importing into, in Power Apps, select **Tables** on the left navigation pane, select **Custom**, and select the table name in the grid. On the details page, select **Properties**. Then, in the **Edit table** dialog box, select the **Primary column** tab.

