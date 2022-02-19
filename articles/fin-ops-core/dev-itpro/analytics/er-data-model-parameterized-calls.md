---
# required metadata

title: Support parameterized calls of ER data models
description: This topic provides information about how to implement parameterized calls of ER data models.
author: NickSelin
ms.date: 02/19/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: ERModelMappingDesigner, EROperationDesigner, ERExpressionDesignerFormula, ERDataModelDesigner
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
ms.search.validFrom: 2020-10-01
ms.dyn365.ops.version: 10.0.15

---

# Support parameterized calls of ER data models

[!include [banner](../includes/banner.md)]

## Overview

To generate business documents, you must configure an [Electronic reporting (ER)](general-electronic-reporting.md) solution that contains the following ER components:

-   [Format](er-overview-components.md#format-component) component - to specify the structure of a business document
-   Format mapping - to control how a business document is filled in at runtime
-   [Model mapping](er-overview-components.md#model-mapping-component) - to specify what data is pulling out of application to a format mapping
-   [Data model](er-overview-components.md#data-model-component) - to pass information between individual components

When you run an ER format, every format element is executed starting from the root one. Whenever an executed format element contains a binding to a [data source](general-electronic-reporting.md#configuring-data-model-mappings-for-outgoing-documents), this data source is executed to deliver the expected data and use it to fill in this format element. When a data source of the **Model** type is called, the appropriate model mapping is called to pull data out of application based on model mapping settings.

Initially, such model mapping calls cannot be parameterized to make them dependent on the logic of the executed format and the only presented below data flow was supported.

<table>
    <tr align="center">
        <td><b>Format</b><br>Format element<br>&nbsp;</td>
        <td><i>Binding</i><br> > request ><br> < value < </td>
        <td><b>Format mapping</b><br>Data source<br>&nbsp;</td>
        <td><i>Data model</i><br> > request ><br> < value < </td>
        <td><b>Model mapping</b><br>Data source<br>&nbsp;</td>
        <td><i>Binding</i><br> > request ><br> < value < </td>
        <td><b>Table</b><br>Record<br>Field</td>
    </tr>
</table>

However, in version 10.0.15 and later, ER allows to configure data model fields the call of which can be performed only when values of the configured parameters are provided. So, when such a field is configured and called from a format component, the required parameters must be provided in a format binding as arguments of such a call. In this case values of such arguments can be specified
based on format specific values. So, this allows you to use **dynamic runtime parametrization** for data model calls and support the data flow that is presented below.

<table>
    <tr align="center">
        <td>
            <b>Format</b>
            <br>Format element 1
            <br>
            <br>Format element 2
            <br>
            <br>&nbsp;
        </td>
        <td>
            <i>Binding</i>
            <br> > request 1 > 
            <br> < value 1 < 
            <br> > request 2 > 
            <br> < value 3 < 
            <br>&nbsp;
        </td>
        <td>
            <b>Format mapping</b>
            <br>Data source 1
            <br>&nbsp;
            <br><b>value2=Func(value1)</b>
            <br>&nbsp;
            <br>&nbsp;
        </td>
        <td>
            <i>Data model</i>
            <br> > field1 >
            <br> < value 1 < 
            <br><b> > field2(value2) ></b>
            <br> < value 3 < 
            <br>&nbsp;
        </td>
        <td>
            <b>Model mapping</b>
            <br>Data source 1
            <br>
            <br>Data source 2
            <br>&nbsp;
            <br>&nbsp;
        </td>
        <td>
            <i>Binding</i>
            <br> > request 1 >
            <br> < value 1 < 
            <br> > request 2 >
            <br> < value 3 <
            <br>&nbsp;
        </td>
        <td><b>Table 1</b><br>Record 1<br>Field 1<br><b>Table 2</b><br>Record 2<br>Field 2</td>
    </tr>
</table>

With this new functionality, you can parametrize the call to any data model field of the [*Record*](er-formula-supported-data-types-composite.md#record) or [*Record list*](er-formula-supported-data-types-composite.md#record-list) type. The following data type are supported for parameters of a data model field:

-   [*Boolean*](er-formula-supported-data-types-primitive.md#boolean)
-   [*Container*](er-formula-supported-data-types-composite.md#container)
-   [*Date*](er-formula-supported-data-types-primitive.md#date)
-   [*DateTime*](er-formula-supported-data-types-primitive.md#datetime)
-   [*GUID*](er-formula-supported-data-types-primitive.md#guid)
-   [*Int64*](er-formula-supported-data-types-primitive.md#int64)
-   [*Integer*](er-formula-supported-data-types-primitive.md#integer)
-   [*Real*](er-formula-supported-data-types-primitive.md#real)
-   [*String*](er-formula-supported-data-types-primitive.md#string)

You can specify every parameter of a data model field the argument of which can be provided as a single value of the defined data type as well as the [*list*](er-formula-supported-data-types-composite.md#record-list) of such values.

> [!NOTE]
> Be aware that the default value for a parameter of a data model field is not supported. So, if you add a parameter to a field of a data model the version of which has been already released and published, you must [rebase](general-electronic-reporting.md#upgrading-a-format-selecting-a-new-version-of-base-format-rebase) to the new version of this model all corresponding model mappings ad format as this data model change is not backward compatible.

You can configure parametrized data model fields to make model mapping calls format specific. It can help you to reduce the number of model mappings that must be configured for many formats of a single data model. You can also use this technique to improve the execution performance of your formats and reduce the time needed to generate business documents. To learn more about this feature, complete the example in this topic.

## Example: Use parameterized calls of ER data models

The following steps explain how the System administrator or Electronic reporting developer can design an ER solution that contains a data model, a model mapping and a format ER component that were configured to call a model mapping from a format providing an argument for such call the value of which has been calculated at runtime by using the formula of the running format. 

These steps can be completed in the **DEMF** company. No code modifications are required. 

In this example, you will create required ER [configurations](general-electronic-reporting.md#Configuration) for the sample company, **Litware, Inc.** Make sure that the configuration provider for the **Litware, Inc.** (http://www.litware.com) sample company is listed for the ER framework, and that it's marked as active. If this configuration provider isn't listed, or if it isn't marked as active, follow the steps in the [Create a configuration provider and mark it as active](tasks/er-configuration-provider-mark-it-active-2016-11.md) topic.

### Business scenario

Let's assume that you have an ER solution the format of which you can run to generate an electronic document for audit purposes that contains sales orders and purchase orders related tax transactions with required details (transaction date, tax value, etc.). Starting from the new fiscal year, the structure of this document has changed - you must submit the extended document that must additionally contain details (names) of all parties (customers and vendors) whose transactions are presented in a generated report. So, you must modify your ER solution to generate a document that is compliant with this new requirement.

### Configure the ER framework

Follow the steps in [Configure the ER framework](er-quick-start2-customize-report.md#ConfigureFramework) to set up the minimal set of ER parameters. You must complete this setup before you start to use the ER framework to design a new ER solution.

### Design a domain-specific data model

You must create a new ER configuration that contains the required data model component. This data model will later be used as a data source when you design an ER format to generate an audit report. By completing the steps in this section, you will import the required data model from the provided XML file.

1.  Download the [Sample audit model.version.1.xml](https://download.microsoft.com/download/b/.../Sample_audit_model.version.1.xml) file, and save it to your local computer.
2.  Go to **Organization administration \> Workspaces \> Electronic reporting**.
3.  In the **Electronic reporting** workspace, select **Reporting configurations**.
4.  On the Action Pane, select **Exchange \> Load from XML file**.
5.  Select **Browse**, and then find and select the **Sample audit model.version.1.xml** file.
6.  Select **OK** to import the configuration.

![The imported ER data model configuration on the Configurations page.](./media/er-data-model-parameterized-calls-imported-model.png)

The following illustration shows the editable version of the configured data model on the **Data model designer** page.

![The structure of the ER data model on the Data model designer page.](./media/er-data-model-parameterized-calls-model1.png)

Notice that currently the model is designed to expose only tax transactions with required details.

### Design a model mapping for the configured data model

As a user in the Electronic Reporting Developer role, you must create a new ER configuration that contains a model mapping component for the Sample audit data model. Because this component implements the configured data model for Finance application, it's Finance-specific. You must configure the model mapping component to specify the application objects that must be used to fill in the configured data model with application data at runtime. To complete this task, you must be aware of the implementation details of the data structure of the tax business domain in Finance. By completing the steps in this section, you will import the required model mapping from the provided XML file.

1.  Download the [Sample audit model mapping.version.1.1.xml](https://download.microsoft.com/download/b/.../Sample_audit_model_mapping.version.1.1.xml) file, and save it to your local computer.
2.  Go to **Organization administration \> Workspaces \> Electronic reporting**.
3.  In the **Electronic reporting** workspace, select **Reporting configurations**.
4.  On the Action Pane, select **Exchange \> Load from XML file**.
5.  Select **Browse**, and then find and select the **Sample audit model mapping.version.1.1.xml** file.
6.  Select **OK** to import the configuration.

![The imported ER model mapping configuration on the Configurations page.](./media/er-data-model-parameterized-calls-imported-mapping.png)

The following illustration shows the editable version of the configured model mapping on the **Model mapping designer** page.

![The structure of the ER model mapping on the Model mapping designer page.](./media/er-data-model-parameterized-calls-mapping1.png)

Notice that currently the model mapping is designed to expose tax transactions with required details fetching this information from the `TaxTrans` application table by using the configured `TaxTrans` and `TaxTransFiltered` ER data sources.

### Design a new format

As a user in the Electronic Reporting Functional Consultant role, you must create a new ER configuration that contains a format component. You must configure the format component to populate tax transactions to a generated report with all required details. By completing the steps in this section, you will import the required format from the provided XML file.

1.  Download the [Sample audit format.version.1.1.xml](https://download.microsoft.com/download/b/.../Sample_audit_format.version.1.1.xml) file, and save it to your local computer.
2.  Go to **Organization administration \> Workspaces \> Electronic reporting**.
3.  In the **Electronic reporting** workspace, select **Reporting configurations**.
4.  On the Action Pane, select **Exchange \> Load from XML file**.
5.  Select **Browse**, and then find and select the **Sample audit format.version.1.1.xml** file.
6.  Select **OK** to import the configuration.

![The imported ER format configuration on the Configurations page.](./media/er-data-model-parameterized-calls-imported-format.png)

The following illustration shows the editable version of the configured format on the **Format designer** page.

![The structure of the ER format on the Format designer page.](./media/er-data-model-parameterized-calls-format1.png)

Notice that the ER format is configured to generate a report as a text file in CSV format.

### Run the imported format

1.  On the Action pane, for the selected **Sample audit format** configuration, select **Run**.
2.  On the **Electronic report parameters** dialog, on the **Records to include** tab, select **Filter**.
    1.  Specify conditions to select tax transactions of the *PIV-110000004* and *INV-10000001* vouchers.
    2.  Select **OK**.
3.  Select **OK**.
4.  Review the generated document that contains tax transactions of the selected vouchers.
    
    ![Preview the generated document with tax transactions.](./media/er-data-model-parameterized-calls-output1.png)

### Adjust the imported ER solution

Based on the new requirement, you must submit a document that contains names of customers and vendors whose transactions are presented in it. So, you must modify the imported ER solution to generate a document that is compliant with this new requirement. You must decide how you want to implement the required modifications of the imported ER components.

First, you might implement the following obvious modification:

-   In your data model, add the new `Transaction.Party.Name` data model field of the *String* type.
-   In your model mapping, configure the binding for the added data model field using available table relations to access the relevant record  of the `DirPartyTable` application table and fetch from this record the value of the `Name` field.

This approach will work but it might cause some performance issues as the `TaxTrans` table is the transaction table and, therefore, may contain a large volume of records. In this case the number of calls to `DirPartyTable` must be equal to the number of records in the `TaxTrans` table that can cause performance degradation of the SQL database.

Alternatively, you might implement another modification:

-   In your data model, add the new `Party` root and the new `Party.Name` field.
-   In your model mapping, add a new data source that will join all records of tables that are used in table relations to access the relevant record of the `DirPartyTable` application table starting from the `TaxTrans` table.

This approach will work but it might cause some memory consumption issues. Even when a new [JOIN](er-join-data-sources.md) data source will be executed as a single SQL request to application database to prevent database performance issues, the result must be fetched to the memory of the application server. As the number of records will be quite large as well as the number of fields of those records, it might cause a very heavy memory consumption or even the out-of-memory runtime exception might be thrown.

Let's implement the modification when an executed format will collect in memory the unique identification codes of customers and vendors for all tax transactions that are placed to a generated report. As we plan to keep only unique codes, the final set of codes will not be too large to hit memory consumption. Then, this set of codes will be passed to the model mapping as the argument of another call of the data source of the **Model** type. Based on the call, the model mapping will execute a new ER data source that will place a single SQL request to application database for fetching records from `DirPartyTable` for only parties whose codes are presented in the provided set of codes.

### Adjust the imported data model

1.  Go to **Organization administration \> Electronic reporting \> Configurations**.
2.  On the **Configurations** page, in the configurations tree in the left pane, select **Sample audit model**.
    1.  In the **Versions** FastTab, select version 2  that is in [**Draft**](general-electronic-reporting.md#component-versioning) status.
    2.  Expand the **Configuration components** FastTb.
3.  Select **Designer** to open the data model for editing.
4.  On the **Data model** page, for the selected `Root` field, select **New**.
    1.  In the **New mode as** field, leave **Child of an active node**.
    2.  In the **Name** field, type **Party**.
    3.  In the **Item type** field, select **Record list**.
    4.  Select **Add** to finish a new field entry.
5.  For the selected `Root.Party` field, in the **Node** tab, select **Parameters**.
    1.  On the **Parameters** dialog, in the **Parameters** tab, select **New**.
    2.  In the **Name** field, type **PartyRefRecId**.
    3.  In the **Type** field, select **Int64**.
    4.  Check the **List** field.
    5.  Select **OK** to finish parameters entry.

    > [!NOTE]
    > You configured the `Root.Party` data model field as a field the call to which must be performed with providing the value of the **PartyRefRecId** parameter and this value must be the list of records containing the field with the `Value` name the *Int64* data type.

    ![The structure of the ER data model on the Data model designer page.](./media/er-data-model-parameterized-calls-model2a.png)

6.  For the selected `Root.Party` field, select **New**.
    1.  In the **New mode as** field, leave **Child of an active node**.
    2.  In the **Name** field, type **Name**.
    3.  In the **Item type** field, select **String**.
    4.  Select **Add** to finish a new field entry.
7.  Select **Save** and close the **Data model** page.

    ![The structure of the ER data model on the Data model designer page.](./media/er-data-model-parameterized-calls-model2b.png)

8.  In the **Versions** FastTab, for version 2, select **Change status \> Complete**, and select **OK**.
    > [!TIP]
    > Notice that your data model changes were stored in the 2nd revision of the **Sample audit model** data model component that is located in the 2nd version of the **Sample audit model** ER configuration.

    ![The updated ER data model configuration on the Configurations page.](./media/er-data-model-parameterized-calls-updated-model.png)

### Adjust the imported model mapping

1.  On the **Configurations** page, in the configurations tree in the left pane, expand **Sample audit model**.
2.  Select **Sample audit model mapping**.
3.  In the **Versions** FastTab, do the following:
    1.  Select the 2nd mapping version that is based on the 1st data model version (version 1.2) that is in **Draft** status.
    2.  Select **Rebase**.
    3.  In the **Target version** field, leave version 2 of the **Sample audit model** base model.
    4.  Select **OK** to do rebase aligning your model mapping with recent data model changes.
    > [!TIP]
    > Notice that the version number of your editable model mapping has changed from 1.2 to 2.2 indicating that the 2nd model version is currently used as a base.
4.  Select **Designer**.
5.  On the **Model to datasource mapping** page, select **Designer** for the current model mapping.
6.  Add a new data source to access the `DirPartyTable` application table.
    1.  On the **Data source type** pane, select **Dynamics 365 for Operations \> Table records**.
    2.  On the **Data sources** pane, select **Add root**.
    3.  In the **Name** field, enter **PartyTable**.
    4.  in the **Table** field, enter **DirPartyTable**.
    5.  Select **OK** to finish a new data source entry.
7.  Add a new data source to request **DirPartyTable** records based on the provided list of record identification codes.
    1.  On the **Data source type** pane, select **General \> Empty container**.
        1.  On the **Data sources** pane, select **Add root**.
        2.  In the **Name** field, enter **Data**.
        3.  Select **OK** to finish a new data source entry.
    2.  On the **Data sources** pane, select the **Data** data source.
    3.  On the **Data source type** pane, select **Functions \> Calculated field**.
    4.  On the **Data sources** pane, select **Add**.
        1.  In the **Name** field, enter **DirParty**.
        2.  Select **Edit formula**.
            1.  On the **Formula designer** page, select **Parameters**.
                1.  On the **Parameters** dialog, in the **Parameters** tab, select **New**.
                2.  In the **Name** field, enter **DirPartyId**.
                3.  In the **Type** field, select *Int64*.
                4.  Check the **List** field.
                5.  Select **OK**.
                > [!TIP]
                > You configured this calculated field as the one that is capable to accept at runtime an argument of a single parameter that is configured as a record list with a single `Value` field of the *Int64* type.
            2.  In the **Formula** field, enter the `FILTER(PartyTable, VALUEINLARGE(PartyTable.RecId, DirPartyId, DirPartyId.Value))` expression.
            > [!TIP]
            > You configured this **DirParty** calculated field to fetch only `DirPartyTable` records whose record identification codes are among codes of the `DirPartyId` list that is provided as an argument when the **DirParty** field is called.

            ![The formula to fetch party names from the application table on the Formula designer page.](./media/er-data-model-parameterized-calls-formula1.png)

            3.  Select **Save** and close the **Formula designer** page.
        3.  Select **Save** and select **OK** to finish a new data source entry.
8.  Bind the added data source to the new data model field to use data model for exposing party names.
    1.  On the **Data model** pane, select the `Root.Party` data model field.
        1.  On the **Data model** pane, select **Edit**.
        2.  On the **Formula designer** page, in the **Formula** field, enter the `Data.DirParty(PartyRefRecId)` expression.
        3.  Select **Save** and close the **Formula designer** page.
        > [!TIP]
            > You configured this binding to call the configured `Data.DirParty` data source providing the list of record identification codes that will be specified in the format when the `Root.Party` data model field will be called.
    2.  On the **Data model** pane, select the `Root.Party.Name` data model field.
        1.  On the **Data model** pane, select **Edit**.
        2.  On the **Formula designer** page, on the **Data source** pane, complete the following steps:
            1.  Expand **Data \> DirParty**.
            2.  Select  **Data \> DirParty \> Name**.
            3.  Select **Add data source**.
            4.  Select **Save** and close the **Formula designer** page.
    
    ![The structure of the ER model mapping on the Model mapping designer page.](./media/er-data-model-parameterized-calls-mapping2.png)

9.  Select **Save** and close the **Model mapping designer** page.
10. Close the **Model to datasource mapping** page.
11. In the **Versions** FastTab, for version 2.2, select **Change status \> Complete**, and select **OK**.

### Adjust the imported format

1.  On the **Configurations** page, select **Sample audit format**.
2.  In the **Versions** FastTab, select the version 1.2 that is in **Draft** status.
    1.  Select **Rebase**.
    2.  In the **Target version** field, leave version 2 of the **Sample audit model** base model.
    3.  Select **OK** to do rebase aligning your format with recent data model changes.
3.  Select **Designer**.
4.  On the **Format designer** page, in the format structure tree in the left pane, select **Expand / Collapse**.
5.  Add a new format element to collect record identification codes of parties whose transactions are populated to a generated report.
    1.  In the format structure tree, select the **Report.Row.Trans** sequence element.
    2.  Select **Add**.
    3.  On the **Add** dialog, select **Data source \> Item**.
    4.  On the **Component properties** dialog, in the **Name** field, enter **Id**.
    5.  In the **Data type** field, select **Int64**.
    6.  Select **OK**.

    > [!TIP]
    > Notice that a **Data source \> Item** element can only be used to perform internal calculations and data transformation in scope of the running format. Therefore, by adding this format element, you do not change the content of a generated document.
    
6.  Add new format elements to populate party names to a generated report.
    1.  Select the **Report.Row** sequence element.
        1.  Select **Add**.
        2.  On the **Add** dialog, select **Text \> Sequence**.
        3.  On the **Component properties** dialog, in the **Name** field, enter **Party**.
        4.  Select **OK**.
    2.  Select the **Report.Row.Party** sequence element.
        1.  Select **Add**.
        2.  On the **Add** dialog, select **Text \> String**.
        3.  On the **Component properties** dialog, in the **Name** field, enter **Name**.
        4.  Select **OK**.
7.  Select the **Mapping** tab.
8.  Add a new data source to collect record identification codes of parties whose transactions are populated to a generated report.
    1.  On the **Mapping** tab, select **Add root**.
    2.  On the **Add data source** dialog, select **Functions \> Data collection**.
    3.  On the **'Data collection' data source properties** dialog, in the **Name** field, enter **PartyIds**.
    4.  In the **Item type** field, select **Int64**.
    5.  Select **OK**.
9.  Add a new binding to collect record identification codes of parties whose transactions are populated to a generated report.
    1.  In the format structure tree, select the **Report.Row.Trans.Id** data item element.
    2.  Select **Edit formula**.
        1.  On the **Formula designer** page, enter the `PartyIds.Collect(model.Transaction.Party.RecId)` expression.
        2.  Select **Save** and close the **Formula designer** page.
10. Add new bindings to populate party names to a generated report.
    1.  In the format structure tree, select the **Report.Party** sequence element.
    2.  Select **Edit formula**.
        1.  On the **Formula designer** page, enter the `model.Party(PartyIds.Result)` expression.
        2.  Select **Save** and close the **Formula designer** page.
    3.  In the format structure tree, select the **Report.Party.Name** sequence element.
        1.  On the **Mapping** tab, select the `model.Party.Name` data model field.
        2.  Select **Bind**.
    
    ![The structure of the ER format on the Format designer page.](./media/er-data-model-parameterized-calls-format2.png)

11. Select **Save** and close the **Format designer** page.
12. Close the **Model to datasource mapping** page.
13. In the **Versions** FastTab, for version 2.2, select **Change status \> Complete**, and select **OK**.

### Run the adjusted format

1.  On the Action pane, for the selected **Sample audit format** configuration, select **Run**.
2.  On the **Electronic report parameters** dialog, on the **Records to include** tab, select **Filter**.
    1.  Specify conditions to select tax transactions of the *PIV-110000004* and *INV-10000001* vouchers.
    2.  Select **OK**.
3.  Select **OK**.
4.  Review the generated document that contains tax transactions of the selected vouchers and names of the corresponding customer and vendor.

    ![Preview the generated document with tax transactions and party names.](./media/er-data-model-parameterized-calls-output2.png)

5.  Go to **Accounts payable \> Vendors \> All vendors** to review details of the selected *PIV-110000004* voucher including the vendor name.

    ![Review the purchase voucher details on the All vendors and Invoice journal pages.](./media/er-data-model-parameterized-calls-review1.gif)

6.  Go to **Accounts receivable \> Customers \> All customers** to review details of the selected *INV-10000001* voucher including the customer name.

    ![Review the sales voucher details on the All customers and Posted sales tax pages.](./media/er-data-model-parameterized-calls-review2.gif)

To get more details regarding the execution of the ER solution, trace this execution by using the ER built-it [performance trace](trace-execution-er-troubleshoot-perf.md) parser.

## Additional resources

-   [Support parameterized calls of ER data sources of the *Calculated field* type](er-calculated-field-type.md)
-   [Trace the execution of ER formats to troubleshoot performance issues](trace-execution-er-troubleshoot-perf.md)
-   [Use DATA COLLECTION data sources in Electronic reporting formats](er-data-collection-data-sources.md)
-   [ValueInLarge ER function](er-functions-logical-valueinlarge.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
