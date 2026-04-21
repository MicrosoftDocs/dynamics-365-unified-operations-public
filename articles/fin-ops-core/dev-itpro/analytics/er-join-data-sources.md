---
title: Use JOIN data sources in ER model mappings to get data from multiple application tables
description: Learn how you can use JOIN type data sources in Electronic reporting (ER), including examples and prerequisites.
author: kfend
ms.author: filatovm
ms.topic: how-to
ms.date: 04/08/2026
ms.custom:
ms.reviewer: johnmichalak
audience: Developer, IT Pro
ms.search.region: Global
ms.search.validFrom: 2019-03-01
ms.search.form: ERModelMappingDesigner, EROperationDesigner
ms.dyn365.ops.version: Release 10.0.1
ms.assetid: 
---

# Use JOIN data sources to get data from multiple application tables in Electronic reporting (ER) model mappings

[!include[banner](../includes/banner.md)]

While configuring Electronic reporting (ER) model mappings or formats, you can [add](#review) required data sources of the **Join** type. At design time, you configure a **Join** data source as a set of several data sources, each of which returns a list of records. For every data source except the first one, you need to define the necessary conditions to join records of the current and previous data sources. At runtime, a configured data source of **Join** type [returns](#executeERformat) a single joined list of records containing fields from the records of nested data sources.

The following types of joins are currently supported:

- Outer (left) join:
  - Join all records of the first (left-most) data source and then any matching records of the second (right-most) data source according to the configured conditions.
- Inner (right) join:
  - Join only records of the first (left-most) data source and only records of the second (right-most) data source that match each other according to the configured conditions.

In the configured **Join** data source, when all data sources are the **Table records** type, execution of the Join data source can be [performed at the database level](#analyze) using a single SQL statement. This statement reduces the number of database calls, which improves model-mapping performance. Otherwise, execution of **Join data** source is performed in memory.

> [!NOTE]
> Using the **VALUEIN** function in ER expressions that specify conditions for joining records in data sources of Join type isn't supported yet. For more information about this function, see [Formula designer in Electronic reporting](general-electronic-reporting-formula-designer.md).

To learn more about this feature, complete the example in this article.

## Example: Use JOIN data sources in ER model mappings

The following steps explain how the system administrator or Electronic reporting developer can configure an Electronic reporting (ER) model mapping to get data from multiple application tables at once by using data sources of the **Join** type to improve data access performance. You can perform these steps for any company of Dynamics 365 Finance or Regulatory Configuration Services (RCS).

### Prerequisites

To complete the examples in this article, you must have access to one of the following roles, depending on the service you use to complete these steps:

**Access to Finance for one of the following roles:**

- Electronic reporting developer
- Electronic reporting functional consultant
- System administrator

**Access to RCS for one of the following roles:**

- Electronic reporting developer
- Electronic reporting functional consultant
- System administrator

You must also complete the steps in the [Create a configuration provider and mark it as active](tasks/er-configuration-provider-mark-it-active-2016-11.md) procedure.

In advance, download and save the following sample ER configuration files:

| **Content description**  | **File name**   |
|--------------------------|-----------------|
| Sample **ER data model** configuration file, which is used as the data source for the examples.| [Model to learn JOIN data sources.version.1.1.xml](https://download.microsoft.com/download/5/c/1/5c1d8a57-6ebd-425b-bc5d-c71dde92c6af/ModeltolearnJOINdatasources.version.1.xml) |
| Sample **ER model mapping** configuration file, which implements the ER data model for the examples. | [Mapping to learn JOIN data sources.version.1.1.xml](https://download.microsoft.com/download/9/2/f/92f339ca-41fc-4f5e-b458-6983c957d3dd/MappingtolearnJOINdatasources.version.1.1.xml)|
| Sample **ER format** configuration file. This file describes the data to populate the ER format component for the examples. | [Format to learn JOIN data sources.version.1.1.xml](https://download.microsoft.com/download/f/f/8/ff8f1b48-14d0-4c73-9145-bcdf8b5265bc/FormattolearnJOINdatasources.version.1.1.xml) |

### Activate a configurations provider

1. Access either Finance or RCS in the first session of your web browser.
1. Go to **Organization administration \> Workspaces \> Electronic reporting**.
1. On the **Localization configurations** page, in the **Configuration providers** section, make sure that the configuration provider for the [Litware, Inc.](http://www.litware.com) sample company is listed, and that it's marked as **Active**. If you don't see this configuration provider, follow the steps in [Create a configuration provider and mark it as active](tasks/er-configuration-provider-mark-it-active-2016-11.md) procedure.

    :::image type="content" source="./media/GER-JoinDS-ActiveProvider.PNG" alt-text="Screenshot of the Electronic reporting workspace.":::

### Import sample ER configuration files

1. Select **Reporting configurations**.
1. Import the ER data model configuration file.
    1. Select **Exchange**.
    1. Select **Load from XML file**.
    1. Select **Browse** to find the **Model to learn JOIN data sources.version.1.1.xml** file.
    1. Select **OK**.
1. Import the ER model-mapping configuration file.
    1. Select **Exchange**.
    1. Select **Load from XML file**.
    1. Select **Browse** to find the **Mapping to learn JOIN data sources.version.1.1.xml** file.
    1. Select **OK**.
1. Import the ER format configuration file.
    1. Select **Exchange**.
    1. Select **Load from XML file**.
    1. Select **Browse** to find the **Format to learn JOIN data sources.version.1.1.xml** file.
    1. Select **OK**.
1. In the configurations tree, expand the **Model to learn JOIN data sources** item as well as other model items (when available).
1. Observe the list of ER configurations in the tree as well as version details on the **Versions** FastTab – they are the source of data for your sample report.

    :::image type="content" source="./media/GER-JoinDS-ConfigurationsTree.PNG" alt-text="Screenshot of the Electronic reporting configurations page.":::

### Turn on execution trace options

1. Select **CONFIGURATIONS**.
1. Select **User parameters**.
1. Set execution trace parameters as shown in the following screenshot.

    :::image type="content" source="./media/GER-JoinDS-Parameters.PNG" alt-text="Screenshot of the Electronic reporting user parameters page.":::

    When you turn on these parameters, the system generates an execution trace for every execution of the imported ER format file. By using the details in the generated execution trace, you can analyze the execution of ER format and ER model-mapping components. For more information about the ER execution trace feature, see [Trace execution of ER format to troubleshoot performance issues](trace-execution-er-troubleshoot-perf.md).

### Review ER model mapping (part 1)

Review the settings of the ER model-mapping component. The component is configured to access information about versions of ER configurations, details of configurations, and configuration providers without using data sources of the **Join** type.

1. Select **Mapping to learn JOIN data sources** configuration.
1. Select **Designer** to open the list of mappings.
1. Select **Designer** to review the mapping details.
1. Select **Show details**.
1. In the configurations tree, expand the **Set1** and **Set1.Details** data model items:

    1. Binding **Details: Record list = Versions** indicates that the **Set1.Details** item is bound to the **Versions** data source returning records of the **ERSolutionVersionTable** table. Each record of this table represents a single version of an ER configuration. The content of this table is presented in the **Versions** FastTab on the **Configurations** page.
    1. Binding **ConfigurationVersion: String = @.PublicVersionNumber** means that the value of the public version of each ER configuration’s version comes from the **PublicVersionNumber** field of the **ERSolutionVersionTable** table and goes to the **ConfigurationVersion** item.
    1. Binding **ConfigurationTitle: String = @.'>Relations'.Solution.Name** indicates that the name of an ER configuration comes from the **Name** field of the **ERSolutionTable** table, accessed by using the many-to-one relation (**'>Relations'**) between the **ERSolutionVersionTable** and **ERSolutionTable** tables. Names of ER configurations of the current application instance are presented in the configurations tree on the **Configurations** page.
    1. Binding **@.'>Relations'.Solution.'>Relations'.SolutionVendor.Name** means that the name of the configuration provider that owns the current configuration comes from the **Name** field of the **ERVendorTable** table, accessed by using the many-to-one relation between **ERSolutionTable** and **ERVendorTable** tables. Names of ER configuration providers are presented in the configurations tree on the **Configurations** page on the page header for each configuration. The entire list of ER configuration providers can be found on the **Organization administration \> Electronic reporting \> Configuration provider** table page.

    :::image type="content" source="./media/GER-JoinDS-Set1Review.PNG" alt-text="Screenshot of the ER model mapping designer page, list of bound data model items.":::

1. In the configurations tree, expand the **Set1.Summary** data model item:

    1. Binding **VersionsNumber: Integer = VersionsSummary.aggregated.VersionsNumber** indicates that the **Set1.Summary.VersionsNumber** item is bound to the **VersionsNumber** aggregation field of the **VersionsSummary** data source of the **GroupBy** type that you configured to return the number of records of the **ERSolutionVersionTable** table via the **Versions** data source.

    :::image type="content" source="./media/GER-JoinDS-Set1GroupByReview.PNG" alt-text="Screenshot of the Edit 'Group By' parameters page.":::

1. Close the page.

### <a name="review"></a> Review ER model mapping (part 2)

Review the settings of the ER model-mapping component. The component is configured to access information about versions of ER configurations, details of configurations, and configuration providers by using a data source of the **Join** type.

1. In the configurations tree, expand the **Set2** and **Set2.Details** data model items. The binding **Details: Record list = Details** indicates that the **Set2.Details** item is bound to the **Details** data source configured as the data source of the **Join** type.

    :::image type="content" source="./media/GER-JoinDS-Set2Review.PNG" alt-text="Screenshot of the ER model mapping designer page showing expanded Set2:Record data model items.":::

    Add the **Join** data source by selecting the **Functions\Join** data source:

    :::image type="content" source="./media/GER-JoinDS-AddJoinDS.PNG" alt-text="Screenshot of the ER model mapping designer page, Join data source type.":::

1. Select **Details** data source.
1. Select **Edit** in the **Data sources** pane.
1. Select **Edit join**.
1. Select **Show details**.

    :::image type="content" source="./media/GER-JoinDS-JoinDSEditor.PNG" alt-text="Screenshot of the JOIN data source parameters page.":::

    Use this page to design the required data source of the **Join type**. At runtime, this data source creates a single joined list of records from the data sources in the **Joined list** grid. The join of records starts from the **ConfigurationProviders** data source that is in the grid as the first one (the **Type** column is blank for it). Records of every other data source are joined consequently to records of the parent data source based on its order in this grid. You must configure every joining data source as a data source nested under a target data source (`1Versions` data source is nested under `1Configurations` one; `1Configurations` data source is nested under **ConfigurationProviders** one). Each configured data source must contain the conditions for the join. In the data source for this particular **Join**, the following joins are defined:

    - Each record of the **ConfigurationProviders** data source (referred to the **ERVendorTable** table) is joined with only records of the **1Configurations** one (referred to in the **ERSolutionTable** table) that have the same value in the **SolutionVendor** and **RecId** fields. The **Inner join** type is used for this join as well as the following conditions for matching records:

    FILTER (Configurations, Configurations.SolutionVendor = ConfigurationProviders.RecId)

    - Each record of the **1Configurations** data source (referred to the **ERSolutionTable** table) is joined with the only records of the **1Versions** one (referred to the **ERSolutionVersionTable** table) that have the same value in the **Solution** and **RecId** fields. **Inner join** type is used for this join as well as the following conditions for matching records:

    FILTER (ConfigurationVersions, ConfigurationVersions.Solution = ConfigurationProviders.'1Configurations'.RecId)

    - The **Execute** option is configured as **Query** meaning that this join data source is executed at runtime on database level as a direct SQL call.

    To join records of data sources that represent application tables, specify join conditions by using pairs of fields other than ones that describe existing in AOT relations between these tables. You can configure this type of join to execute at the database level as well.

1. Close the page.
1. Select **Cancel**.
1. In the configurations tree, expand the **Set2.Summary** data model item:

    - Binding **VersionsNumber: Integer = DetailsSummary.aggregated.VersionsNumber** indicates that the **Set2.Summary.VersionsNumber** item is bound to the **VersionsNumber** aggregation field of the **DetailsSummary** data source of the **GroupBy** type that you configured to return the number of joined records of the **Details** data source of the **Join** type.
    - The **Execution** location option is configured as **Query** meaning that this **GroupBy** data source runs at runtime as a direct SQL call at the database level. This behavior is possible because the base data source **Details** of the **Join** type is configured as executed at the database level.

    :::image type="content" source="./media/GER-JoinDS-Set2GroupByReview.PNG" alt-text="Screenshot of the GROUPBY data source parameters page.":::

1. Close the page.
1. Select **Cancel**.

### <a name="executeERformat"></a> Execute ER format

1. Access Finance or RCS in the second session of your web browser by using the same credentials and company as in the first session.
1. Go to **Organization administration \> Electronic reporting \> Configurations**.
1. Expand **Model to learn JOIN data sources** configuration.
1. Select **Format to learn JOIN data sources** configuration.
1. Select **Designer**.
1. Select **Show details**.
1. Select **Mapping**.
1. Select **Expand/Collapse**.

    This format populates a generated text file with a new line for every version of an ER configuration (**Version** sequence). Each generated line contains the name of a configuration provider that owns the current configuration, the configuration name, and the configuration version separated by semicolon mark. The final line of generated file contains the number of discovered versions of ER configurations (**Summary** sequence).

    :::image type="content" source="./media/GER-JoinDS-FormatReview.PNG" alt-text="Screenshot of the ER format designer page, Format tab.":::

    The **Data** and **Summary** data sources populate configuration version details to the generated file:

    - The **Set1** data model provides information when you choose **No** for the **Selector** data source at runtime on the user dialog page when running ER format.
    - The **Set2** data model provides information when you choose **Yes** for the **Selector** data source at runtime on the user dialog page.

    :::image type="content" source="./media/GER-JoinDS-FormatMappingReview.PNG" alt-text="Screenshot of the ER format designer page, Mapping tab.":::

1. Select **Run**.
1. On the dialog page, select **No** in the **Use JOIN data source** field.
1. Select **OK**.
1. Review generated file.

    :::image type="content" source="./media/GER-JoinDS-Set1Run.PNG" alt-text="Screenshot of the Electronic report parameters generated file not using JOIN data source.":::

#### Analyze ER format execution trace

1. In the first session of Finance or RCS, select **Designer**.
1. Select **Performance trace**.
1. In the **Performance trace** grid, select the top-most record of the latest execution trace of an ER format that used the current model mapping component.
1. Select **OK**.

    Execution statistics inform you about duplicated calls to application tables:

    - The process calls **ERSolutionTable** as many times as you have configuration version records in the **ERSolutionVersionTable** table, while the number of such calls could be reduced for performance improvement.
    - The process calls **ERVendorTable** twice for every configuration version record that the process discovers in the **ERSolutionVersionTable** table, while the number of such calls could be reduced.

    :::image type="content" source="./media/GER-JoinDS-Set1Run2.PNG" alt-text="Screenshot of the execution statistics on the ER Model mapping designer page.":::

1. Close the page.

### Execute ER format

1. Switch to your web browser tab with the second session of Finance or RCS.
1. Select **Run**.
1. On the dialog page, select **Yes** in the **Use JOIN data source** field.
1. Select **OK**.
1. Review generated file.

    :::image type="content" source="./media/GER-JoinDS-Set2Run.PNG" alt-text="Screenshot of the Electronic report parameters generated file using JOIN data source.":::

#### <a name="analyze"></a> Analyze ER format execution trace

1. In the first session of Finance or RCS, select **Designer**.
1. Select **Performance trace**.
1. In the **Performance trace** grid, select the top-most record representing the latest execution trace of an ER format that used the current model mapping component.
1. Select **OK**.

    The statistics inform you about the following information:

    - The application database is called once to get records from **ERVendorTable**, **ERSolutionTable**, and **ERSolutionVersionTable** tables to access required fields.

    :::image type="content" source="./media/GER-JoinDS-Set2Run2.PNG" alt-text="Screenshot of the ER Model mapping designer page performance statistics details.":::

    - The application database is called once to calculate the number of configuration versions by using joins that are configured in the **Details** data source.

    :::image type="content" source="./media/GER-JoinDS-Set2Run3.PNG" alt-text="Screenshot of the ER Model mapping designer page showing application database calls.":::

## Limitations

As you can see from the example in this article, you can build the **JOIN** data source from several data sources that describe the individual datasets of the records that you eventually join. Use the built-in ER [FILTER](er-functions-list-filter.md) function to configure those data sources. When you configure the data source so that it calls beyond the **JOIN** data source, you can use company ranges as part of the condition for data selection. The initial implementation of the **JOIN** data source doesn't support data sources of this type. For example, if you call a [FILTER](er-functions-list-filter.md)-based data source within the scope of execution of a **JOIN** data source and the called data source contains company ranges as part of the condition for data selection, an exception occurs.

In Microsoft Dynamics 365 Finance version 10.0.12 (August 2020), you can use company ranges as part of the condition for data selection in [FILTER](er-functions-list-filter.md)-based data sources that you call within the scope of execution of a **JOIN** data source. Because of the limitations of the application [query](../dev-ref/xpp-library-objects.md#query-object-model) builder, the company ranges are supported only for the first data source of a **JOIN** data source.

### Example

For example, you must make a single call to the application database to get the list of foreign trade transactions of multiple companies and the details of the inventory item that is referred to in those transactions.

In this case, you configure the following artifacts in your ER model mapping:

- **Intrastat** root data source that represents the **Intrastat** table.
- **Items** root data source that represents the **InventTable** table.
- **Companies** root data source that returns the list of companies (**DEMF** and **GBSI** in this example) where transactions must be accessed. The company code is available from the **Companies.Code** field.
- **X1** root data source that has the expression `FILTER (Intrastat, VALUEIN(Intrastat.dataAreaId, Companies, Companies.Code))`. As part of the condition for data selection, this expression contains the definition of company ranges `VALUEIN(Intrastat.dataAreaId, Companies, Companies.Code)`.
- **X2** data source as a nested item of the **X1** data source. It includes the expression `FILTER (Items, Items.ItemId = X1.ItemId)`.

Finally, you can configure a **JOIN** data source where **X1** is the first data source and **X2** is the second data source. You can specify **Query** as the **Execute** option to force ER to run this data source on the database level as a direct SQL call.

When you run the configured data source while the ER execution is [traced](trace-execution-er-troubleshoot-perf.md), the following statement is shown in the ER model mapping designer as part of the ER performance trace.

`SELECT ... FROM INTRASTAT T1 CROSS JOIN INVENTTABLE T2 WHERE ((T1.PARTITION=?) AND (T1.DATAAREAID IN (N'DEMF',N'GBSI') )) AND ((T2.PARTITION=?) AND (T2.ITEMID=T1.ITEMID AND (T2.DATAAREAID = T1.DATAAREAID) AND (T2.PARTITION = T1.PARTITION))) ORDER BY T1.DISPATCHID,T1.SEQNUM`

> [!NOTE]
> An error occurs if you run a **JOIN** data source that you configured so that it contains data selection conditions that have company ranges for additional data sources of the executed **JOIN** data source.

## Additional resources

[Formula designer in Electronic reporting](general-electronic-reporting-formula-designer.md)

[Trace execution of ER format to troubleshoot performance issues](trace-execution-er-troubleshoot-perf.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
