---
# required metadata

title: Use GROUPBY data sources for records grouping and aggregate calculations
description: This topic explains how you can use GROUPBY type data sources in Electronic reporting (ER).
author: NickSelin
ms.date: 12/14/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: ERModelMappingDesigner, EROperationDesigner
# ROBOTS: 
audience: Application User, Developer, IT Pro
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: nselin
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Use GROUPBY data sources for records grouping and aggregate calculations

[!include[banner](../includes/banner.md)]

While configuring [Electronic reporting (ER)](general-electronic-reporting.md) model mappings or formats, you can [add](#AddMmDataSource2) required data sources of the **GroupBy** type. At design time, a **GroupBy** data source is configured to identify [a base data source](#BaseDataSource) the records of which will be grouped at runtime, fields of the base data source using for [records grouping](#GroupingFields), and aggregate [functions](#AggregateFunctions) to specify what aggregate calculations will be performed at runtime for each discovered group. At runtime, a configured **GroupBy**  data source groups records that have the same values in the grouping fields returning a list of records every record of which represents a single group. For each group, this data source exposes values of fields the initial records have been group by, values of calculated aggregate functions, and the list of records of the base data source that belongs to this group.

## <a name="AggregateFunctions"></a>Aggregate functions

Every aggregate calculation is performed at runtime for each group of records by using values of a single field or an expression in the records of a data source that has been selected for grouping in the editable data source of the **GroupBy** type. The following aggregate functions are currently supported:

-   AVG
    -   Returns the average of the values in a group. AVG can be used with numeric fields only.
-   COUNT
    -   Returns the number of items found in a group.
-   Min
    -   Returns the minimum value among values in a group.
-   Max
    -   Returns the maximum value among values in a group.
-   SUM
    -   Returns the sum of all values in a group. SUM can be used with numeric fields only.

## <a name="ExecutionLocation"></a>Execution location

When you edit a **GroupBy** data source specifying the base data source the records of which must be grouped, the system automatically detects the most efficient [location](#ExecutionLocation) for this **GroupBy** data source execution. When the base data source is
[queryable](er-functions-list-filter.md#usage-notes) meaning that it can be executed at database level, the execution location of the
editable **GroupBy** data source is also specified as application database. Otherwise, it is specified as an application server memory.

You can change the automatically detected location manually selecting the desire execution location that is applicable for the configured data source. The validation [error](er-components-inspections.md#i5) is thrown at design time when a not applicable execution location is selected.

> [!TIP]
> It is recommended to use the database location for grouping data sources that expose large number of records.

## <a name="MemoryConsumption"></a>Memory consumption

When a **GroupBy** data source is executed in memory, by default the application server memory is used to store records of the base data source that belongs to each discovered group as records of a single group. You can reduce memory consumption by suppressing such records storage for those **GroupBy** data sources that were configured to compute aggregated functions only and whose groups records are not used at runtime. For doing this, enable the **Reduce memory usage in ER when records grouping is only used to compute aggregations** feature in the **Feature management** workspace.

## <a name="Alternatives"></a>Alternatives

Notice that similar aggregations can be calculated by using either [other](er-data-collection-data-sources.md#if-i-have-to-calculate-running-totals-and-collect-data-what-is-the-difference-between-using-a-data-collection-data-source-and-using-the-built-in-data-collection-functions) type of data sources or ER built-in functions.

To learn more about this feature, complete the example that follows.

## <a name="Example"></a>Example: Use a GROUPBY data source for aggregate calculations and records grouping

This example shows how a user in the System administrator or Electronic reporting functional consultant role can configure an ER model mapping that has a GROUPBY data source that is used to calculate aggregate functions and group records. This model mapping will be used to print the control report when the Intrastat declaration is generated. This report lets you observe reported Intrastat transactions.

The procedures in this example can be completed in the DEMF company in Microsoft Dynamics 365 Finance. 

### Prepare sample data

Make sure that you have Intrastat transactions for reporting on the Intrastat page. Notice that you need transactions for different transport codes as you will group transactions by using this field.

![Prepare Intrastat transactions on the Intrastat page.](./media/er-groupby-data-sources-prepare-transactions.png)

### Configure the ER framework

Follow the steps in [Configure the ER framework](er-quick-start2-customize-report.md#ConfigureFramework) to set up the minimal set of ER parameters. You must complete this setup before you start to use the ER framework to design an ER model mapping.

### Import the standard ER format configuration

Follow the steps in [Import the standard ER format configuration](er-quick-start2-customize-report.md#ImportERSolution1) to add the standard ER configurations to your current instance of Dynamics 365 Finance. Import version 1 of the **Intrastat model** configuration from the repository.

### Create a custom data model configuration

Follow the steps in [Add a custom data model configuration](er-quick-start3-customize-report.md#add-a-custom-data-model-configuration) to manually add a new ER data model **Intrastat model (Litware)** configuration deriving it from the imported **Intrastat model** configuration.

### Configure a custom data model component

Complete the following steps to introduce the required modifications in the derived **Intrastat model (Litware)** data model to use it for exposing transport codes with the required details:

1.  Go to **Organization administration \> Electronic reporting \> Configurations**.
2.  On the **Configurations** page, in the configuration tree, select **Intrastat model (Litware)**.
3.  Select **Designer**.
4.  On the **Data model designer** page, in the model tree, select **Intrastat**.
5.  Select **New** to add a new nested node for the selected **Intrastat** one. In the drop-down dialog box for adding a data model node, follow these steps:
    1.  In the **Name** field, enter **Transport**.
    2.  In the **Item type** field, select **Record list**.
    3.  Select **Add** to add the new node.
6.  Select **New** to add a new nested node for the added **Transport** one. In the drop-down dialog box for adding a data model node, follow these steps:
    1.  In the **Name** field, enter **Code**.
    2.  In the **Item type** field, select **String**.
    3.  Select **Add** to add the new node.
7.  Select **New** to add a new nested node for the added **Transport** one. In the drop-down dialog box for adding a data model node, follow these steps:
    1.  In the **Name** field, enter **TotalInvoicedAmount**.
    2.  In the **Item type** field, select **Real**.
    3.  Select **Add** to add the new node.
8.  Select **New** to add a new nested node for the added **Transport** one. In the drop-down dialog box for adding a data model node, follow these steps:
    1.  In the **Name** field, enter **NumberOfTransactions**.
    2.  In the **Item type** field, select **Integer**.
    3.  Select **Add** to add the new node.
9.  Select **New** to add a new nested node for the added **Transport** one. In the drop-down dialog box for adding a data model node, follow these steps:
    1.  In the **Name** field, enter **Transaction**.
    2.  In the **Item type** field, select **Record list**.
    3.  Select **Add** to add the new node.
    4.  For the added **Transaction** node, on the Node FastTab, select **Switch item reference**.
        1.  In the **Switch item reference** dialog box, in the data model tree, select **CommodityRecord**.
        2.  Select **OK**.

![Configured data model in the ER data model designer.](./media/er-groupby-data-sources-configure-data-model.png)

### Complete the design of a custom data model

Follow the steps in [Complete the design of the data model](er-quick-start3-customize-report.md#add-a-custom-data-model-configuration) to complete the design of the derived **Intrastat model (Litware)** data model.

### Create a new model mapping configuration

Follow the steps in [Create a new model mapping configuration](er-quick-start1-new-solution.md#CreateModelMapping) to manually add a new ER model mapping **Intrastat sample mapping** configuration for the derived **Intrastat model (Litware)** configuration.

### Add a new model mapping component

1.  Go to **Organization administration \> Electronic reporting \> Configurations**.
2.  On the **Configurations** page, in the configuration tree, expand the **Intrastat model** configuration.
3.  Select the **Intrastat sample mapping** configuration.
4.  Select **Designer** to open the list of mappings.
5.  Select **Delete** to remove the existing mapping component.
6.  Select **New** to add a new mapping component.
    1.  In the **Definition** field, select **Intrastat**.
    2.  In the **Name** field, enter **Intrastat mapping**.
7.  Select **Designer** to start to configure the added mapping.

### Design the added model mapping component

#### <a name="AddMmDataSource1"></a>Add a data source to access an application table

You must configure a data source to access the application tables that contain details of Intrastat transactions.

1.  On the **Model mapping designer** page, in the **Data source types** pane, select **Dynamics 365 for Operations\\Table records**.
2.  In the **Data sources** pane, select **Add root** to add a new data source that will be used to access the `Intrastat` table, where every record represents a single Intrastat transaction:
3.  In the **Data source properties** dialog box, do the following:
    1.  In the **Name** field, enter **Transaction**.
    2.  In the **Table** field, enter **Intrastat**.
    3.  Select **OK** to add the new data source.

#### <a name="AddMmDataSource2"></a>Add a data source to group Intrastat transactions

You must configure a **GroupBy** data source to group Intrastat transactions and compute aggregate functions.

1.  On the **Model mapping designer** page, in the **Data source types** pane, select **Functions\\Group by**.
2.  In the **Data sources** pane, select **Add root** to add a new data source that will be used to group Intrastat transactions and compute aggregate functions:
3.  In the **Data source properties** dialog box, do the following:
    1.  In the **Name** field, enter **TransportRecord**.
    2.  Select **Edit group by** to configure grouping conditions:
        1.  On the **Edit 'Group By' parameters** page, complete the following steps:
            1.  In the data sources list in the right pane, select the **Transaction** data source and expand it.
                1.  Select **Add field to \> What to group** to indicate that the **Transaction** data source is selected as the <a name="BaseDataSource">base data source</a> for the configured **GroupBy** data source. So, the records of the **Transaction** data source will be grouped and values of fields of this data source will be used for calculation if aggregate functions.
            2.  Select the **Transaction\Transport** field.
                1.  Select **Add field to \> Grouped field** to indicate that the **Transport** field of the base data source is selected as the <a name="GroupingFields">grouping criteria</a> for the configured **GroupBy** data source. So, the records of the **Transaction** data source will be grouped based on the value of this field. Every record of the configured **GroupBy** data source will represent a single transport code that has been met in records of the base data source.
            3.  Select the **Transaction\AmountMST** field.
                1.  Select **Add field to \> Aggregate fields** to indicate that an <a name="AggregateFunctions">aggregate function</a> will be calculated for this field.
                2.  In the **Aggregations** pane, do the following in the record that has been added for the selected **Transaction\AmountMST** field:
                    1.  In the **Method** field, select the **Sum** function.
                    2.  In the **Name** optional field, enter **TotalInvoicedAmount**.
                > This setting means that for every transport group the total amount of the **Transaction\AmountMST** field will be calculated.
            4.  Select the **Transaction\RecId** field.
                1.  Select **Add field to \> Aggregate fields** to indicate that an aggregate function will be calculated for this field.
                2.  In the **Aggregations** pane, do the following in the record that has been added for the selected **Transaction\RecId** field:
                    1.  In the **Method** field, select the **Count** function.
                    2.  In the **Name** optional field, enter **NumberOfTransactions**.
                > This setting means that for every transport group the number of transactions in this group will be calculated.
            5.  Select **Save**.
        2.  Observe the <a name="ExecutionLocation">execution</a> parameters of the editable data source.
            > Notice that the **Autodetect** value has been automatically selected in the **Execution location** field and the **Execution at** field contains the **SQL** value. This setting means that the selected **Transaction** base data source is currently queryable that allows to execute the editable **GroupBy** data source at database level.
        3.  Expand the lookup list of available values of the **Execution location** field.
            > Notice that you can explicitly select either **Query** or **In memory** option to force execution of this **GroupBy** data source on database level or in memory of application server accordingly.
        4.  Select **Save** and close the **Edit 'Group By' parameters** page.
    3.  Select **OK** to complete settings of the **GroupBy** data source.

#### <a name="AddMmBindings"></a>Bind the GroupBy data source to data model fields

You must bind the configured data source to the fields of the data model to specify how the data model will be filled in with application data at runtime.

1.  On the **Model mapping designer** page, expand the **Transport** node in the **Data model** pane.
2.  Expand the **TransportRecord** data source in the **Data sources** pane.
3.  Add a binding to expose the list of discovered transport groups:
    1.  In the **Data model** pane, select the **Transport** item.
    2.  In the **Data sources** pane, select the **TransportRecord** data source.
    3.  Select **Bind**.
4.  Add a binding to expose the transport code of each discovered transport group:
    1.  Select the **Transport.Code** data model item.
    2.  Select the **TransportRecord.grouped.TransportMode** grouped field.
    3.  Select **Bind**.
5.  Add binding to expose values of calculated aggregate functions for each discovered transport group:
    1.  Select the **Transport.NumberOfTransactions** data model item.
    2.  Select the **TransportRecord.aggregated.NumberOfTransactions** aggregated field.
    3.  Select **Bind**.
    4.  Select the **Transport.TotalInvoicedAmount** data model item.
    5.  Select the **TransportRecord.aggregated.TotalInvoicedAmount** aggregated field.
    6.  Select **Bind**.
6.  Add binding to expose transaction records that belongs to each discovered transport group:
    1.  Select the **Transport.Transaction** data model item.
    2.  Select the **TransportRecord.lines** field.
    3.  Select **Bind**.
        > You can continue configuring bindings for the nested items of the **Transport.Transaction** data model item and the **TransportRecord.lines** data source field to expose at runtime details of Intrastat transactions that belongs to each discovered transport group.

![Configured model mapping in the ER model mapping designer.](./media/er-groupby-data-sources-configure-model-mapping.png)

### Debug the added model mapping component

You can use the [ER data source debugging](er-debug-data-sources.md) for testing the configured model mapping.

1.  On the **Model mapping designer** page, select **Start debugging**.
2.  On the **Debug datasources** page, in the left pane, complete the following steps:
    1.  Select the **TransportRecord** data source.
    2.  Select **Read all records**.
3.  Expand the **TransportRecord** data source.
    1.  Select the **TransportRecord.grouped.TransportMode** data source.
    2.  Select **Get value**.
    3.  Select the **TransportRecord.grouped.NumberOfTransactions** data source.
    4.  Select **Get value**.
    5.  Select the **TransportRecord.grouped.TotalInvoicedAmount** data source.
    6.  Select **Get value**.
4.  In the right pane, select **Expand all**.

Notice that two records are exposed by the **TransportRecord** data source presenting two transport codes. For each transport code the number of transactions and the total invoiced amount are calculated.

> [!NOTE]
> Please, note that the lazy reading approach is used when a **GroupBy** data source is called to optimize database calls. Therefore, some of values of a **GroupBy** data source fields are only calculated in the ER datasource debugger when they are bound to data model fields.

![Results of the data source debugging on the Debug datasources page.](./media/er-groupby-data-sources-debug-datasource.png)

## Frequently asked questions

### Is there any way to calculate grand totals when the group totals are calculated?

For doing this, you can configure another **GroupBy** data source in which the already configured **GroupBy** data source is used as the base one. The following illustration shows the **Totals** data source of the **GroupBy** type that is used to calculate the aggregate SUM function based on the SUM aggregation of the **TransportRecord** data source of the **GroupBy** type.

![Configured model mapping in the ER model mapping designer.](./media/er-groupby-data-sources-configure-model-mapping2.png)

The following illustration shows the results of the **Totals** data source debugging.

![Results of the data source debugging on the Debug datasources page.](./media/er-groupby-data-sources-debug-datasource2.png)

## Additional resources

- [Electronic Reporting overview](general-electronic-reporting.md)
- [Debug data sources of an executed ER format to analyze data flow and transformation](er-debug-data-sources.md)
- [Use DATA COLLECTION data sources in Electronic reporting formats](er-data-collection-data-sources.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
