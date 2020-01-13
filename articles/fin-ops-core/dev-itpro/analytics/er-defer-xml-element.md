---
# required metadata

title: Defer execution of XML elements in ER formats
description: This topic This topic explains how the execution of an XML element in an ER format can be deferred.
author: NickSelin
manager: kfend
ms.date: 01/14/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

ms.search.form: EROperationDesigner
# ROBOTS: 
audience: Application User, IT Pro
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 58771
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: nselin
ms.search.validFrom: 2020-01-01
ms.dyn365.ops.version: AX 10.0.9

---

# Defer execution of an XML element in ER format

[!include [banner](../includes/banner.md)]

## Overview

You can use the Operations designer of the [Electronic reporting (ER)](general-electronic-reporting.md) framework to [configure](./tasks/er-format-configuration-2016-11.md) the [format component](general-electronic-reporting.md#FormatComponentOutbound) of an ER solution using to generate outbound documents in XML format. The hierarchical structure of the configured format component consists of format elements of various types using to populate at runtime necessary information to generated documents. By default, when you run an ER format, these format elements are executed in the same sequence as they are presented in the format hierarchy – one by one from top to bottom order. At design time, you can change this default execution order for any of XML elements of the configured format component. 

You can turn on the <a name="DeferredXmlElementExecution"></a>**Deferred execution** option for an XML element to postpone the execution of this element. When this option for an XML element is on in the configured format, execution of this element is deferred until all other elements of its parent have been executed.

To learn more about this feature, complete the example in this topic.

## Limitations

> Note that the **Deferred execution** option is supported for the only XML elements that are configured for an ER format using to generate **outbound** documents in XML format.

> Note that the **Deferred execution** option is supported for the only an XML element that resides in only another XML element. Therefore, this option is not applicable for an XML element that resides in other type of format elements, for example, in an **XML sequence** element.

> Note that the **Deferred execution** option is not supported for XML elements that reside in **Common\\File** format element the option **Split file** of which is set to **Yes**. To learn more how to split XML files, see [Split generated XML files based on file size and content quantity](er-split-files.md).

# <a name="Example"></a>Example: Defer execution of an XML element in ER format

The following steps explain how a user in either the System administrator or Electronic reporting functional consultant [role](https://docs.microsoft.com/dynamics365/fin-ops-core/dev-itpro/sysadmin/tasks/assign-users-security-roles) can configure an ER format containing an XML element the order of execution of which differs from its order in the format’s hierarchy.

These steps can be performed in the **USMF** company of Microsoft Dynamics 365 Finance.

## Prerequisites

To complete the examples in this topic, you must have access to the **USMF** company of Finance for one of the following roles:

- Electronic reporting functional consultant
- System administrator

If you have not yet completed the example in the [Defer execution of a sequence element in ER format](er-defer-sequence-element.md#Example) topic, download the following [configurations](http://general-electronic-reporting.md/#Configuration) of the sample ER solution.

| **Content description**        | **File name**                      |
|--------------------------------|------------------------------------|
| ER data model configuration    | [Model to learn deferred elements.version.1.xml](https://mbs.microsoft.com/customersource/Global/AX/downloads/hot-fixes/365optelecrepeg)   |
| ER model mapping configuration | [Mapping to learn deferred elements.version.1.1.xml](https://mbs.microsoft.com/customersource/Global/AX/downloads/hot-fixes/365optelecrepeg) |

In advance, you must also download and save locally the following configuration of the sample ER solution.

| **Content description**        | **File name**                      |
|--------------------------------|------------------------------------|
| ER format configuration        | [Format to learn deferred XML elements.version.1.1.xml](https://mbs.microsoft.com/customersource/Global/AX/downloads/hot-fixes/365optelecrepeg) |

## Import sample ER configurations

1.  Go to **Organization administration \> Workspaces \> Electronic reporting**.
2.  Select **Reporting configurations**.
3.  If the **Model to learn deferred elements** configuration is not available in the tree, import the ER data model configuration.
    -   Select **Exchange**.
    -   Select **Load from XML file**.
    -   Select **Browse** to find the **Model to learn deferred elements.1.xml** file.
    -   Select **OK**.
4.  If the **Mapping to learn deferred elements** configuration is not available in the tree, import the ER model mapping configuration.
    -   Select **Exchange**.
    -   Select **Load from XML file**.
    -   Select **Browse** to find the **Mapping to learn deferred elements.1.1.xml** file.
    -   Select **OK**.
5.  Import the ER format configuration.
    -   Select **Exchange**.
    -   Select **Load from XML file**.
    -   Select **Browse** to find the **Format to learn deferred XML elements.1.1.xml** file.
    -   Select **OK**.
6.  In the configurations tree, expand the **Model to learn deferred elements**.
7.  Observe the list of imported ER configurations in the tree.
    
    ![Electronic reporting configuration page](./media/ER-DeferredXml-Configurations.png)

## Activate a configurations provider

1.  Go to **Organization administration \> Workspaces \> Electronic reporting**.
2.  On the **Localization configurations** page, in the **Configuration
    providers** section, make sure that the configuration
    [provider](general-electronic-reporting.md#Provider) for the Litware, Inc. (<http://www.litware.com>) sample company is listed, and that it's marked as **Active**. If you don't see this configuration provider or it is not marked as **Active**, follow the steps in [Create a configuration provider and mark it as active](./tasks/er-configuration-provider-mark-it-active-2016-11.md.
    
    ![Electronic reporting workspace page](./media/ER-DeferredXml-ElectronicReportingWorkspace.png)

## Review the imported model mapping

Review settings of the ER model mapping component configured to access tax transactions and expose accessed data upon request.

1.  Go to **Organization administration \> Workspaces \> Electronic reporting**.
2.  Select **Reporting configurations**.
3.  Expand **Model to learn deferred elements**.
4.  Select **Mapping to learn deferred elements** configuration.
5.  Select **Designer** to open the list of mappings.
6.  Select **Designer** to review the mapping details.
7.  Toggle **Show details** on.

    Review data sources configured to access tax transactions.

    -   The **Transactions** data source of the *Table record* type is configured to access records of the **TaxTrans** application table.
    -   The **Vouchers** data source of the *Calculated field* type is configured to return required voucher codes **INV-10000349** and **INV-10000350** as the list of records.
    -   The **Filtered** data source of the *Calculated field* type is configured to select from the **Transactions** data source only tax transactions of the required vouchers.
    -   The **\$TaxAmount** field of the *Calculated field* type is added for the **Filtered** data source to expose tax value with the opposite sign.
    -   The **Grouped** data source of the *Group By* type is configured to group filtered tax transactions of the **Filtered** data source.
    -   The **TotalSum** aggregation field of the **Grouped** data source is configured to summarize values of the **\$TaxAmount** field of the **Filtered** data source for all filtered tax transactions of the **Filtered** data source.

        ![GroupBy data source parameters page](./media/ER-DeferredXml-GroupByParameters.png)

    Review how configured data sources are bound to the data model exposing accessed data to make it available in an ER format.

    -   The **Filtered** data source is bound to the **Data.List** field of the data model.
    -   The **\$TaxAmount** field of the **Filtered** data source is bound to the **Data.List.Value** field of the data model.
    -   The **TotalSum** field of the **Grouped** data source is bound to the **Data.Summary.Total** field of the data model.

        ![Electronic reporting model mapping designer page](./media/ER-DeferredXml-ModelMapping.png)

8.  Close the model mapping designer page.
9.  Close the model mappings page.

## Review the imported format

1.  Select **Format to learn deferred XML elements** configuration.
2.  Select **Designer** to review the format details.
3.  Toggle **Show details** on.

    Review settings of ER format components configured to generate an outbound document in XML format and to place to this document details of tax transactions.

    The **Report\\Message** XML element is configured to populate to an outbound document a single node holding nested XML elements **Header**, **Record** and **Summary**.

    ![Electronic reporting format designer page](./media/ER-DeferredXml-Format.png)

    The **Report\\Message\\Header** XML element is configured to populate to outbound document a single header node to show date and time when the processing starts.

    The **Report \\Message\\Record** XML element is configured to populate to outbound document a single record node with details of a single tax transaction.
    
    The **Report\\Message\\Summary** XML element is configured to populate to outbound document a single summary node with the sum of tax values of the processed tax transactions.

4.  Select the **Mapping** tab.

    -   The **Report\\Message\\Header** element is bound to no data source to output a single node to an outbound document.
    -   The **ExecutionDateTime** attribute outputs the date and time (including milliseconds) when the header node is added.
    -   The **Report\\Message\\Record** element is bound to **model.Data.List** list to output a single record node for every record from the bound list.
    -   The **TaxAmount** attribute is bound to **model.Data.List.Value** (shown as **\@.Value** by using the relative path view) to output the tax value of the current tax transaction.
    -   The **RunningTotal** attribute is a placeholder for running total of the tax values. Currently, this attribute outputs nothing as neither a binding nor a default value is configured for it.
    -   The **ExecutionDateTime** attribute outputs the date and time (including milliseconds) when the current transaction is processed in this report.
    -   The **Report\\Message\\Summary** element is bound to no data source to output a single node to an outbound document.
    -   The **TotalTaxAmount** attribute is bound to **model.Data.Summary.Total** to output the sum of tax values of the processed tax transactions.
    -   The **ExecutionDateTime** attribute outputs the date and time (including milliseconds) when the summary node is added.

        ![Electronic reporting format designer page](./media/ER-DeferredXml-Format2.png)

## Run the imported format

1.  Select **Run**.
2.  Download the offered by a web browser file and open it for review.

![Electronic reporting format designer page](./media/ER-DeferredXml-Run.png)

Notice that the summary node presents the sum of tax values of the processed transactions. As you have this format configured to return this sum by using the **model.Data.Summary.Total** binding, this sum is calculated by calling the **TotalSum** aggregation of the **Grouped** data source of the *GroupBy* type in using model mapping. To compute this aggregation, model mapping iterates over all transactions that have been selected in the **Filtered** data source. Comparing the execution time of the summary node and the last record node, you can see that it took 12 milliseconds to perform this summing. Comparing the execution time of the first and last record nodes, you can see that It took 9 milliseconds to generate all record nodes. Totally, it took 21 milliseconds.

## Modify the format to do summing based on generated output

With much larger volume of transactions than in the current example, the summing time may increase causing performance issues. You can change the setting of this format to prevent the appearance of such performance issues. As you access tax values to output them to generated report, you can re-use this information for doing summing of tax values. See [Configure format to do counting and
summing](./tasks/er-format-counting-summing-1.md)
for more details.

1.  Select the **Format** tab.
2.  Select the **Report** file element in the format tree.
3.  Set the **Collect output details** option to **Yes**.  
      
    By turning this option on, you can configure this format using the content of already generated report as a data source accessible by using ER built-in functions of the [Data collection](er-functions-category-data-collection.md) category.

4.  Select the **Mapping** tab.
5.  Select the **Report\\Message\Record** XML element.
6.  Configure the **Collected data key name** expression as `WsColumn`.
7.  Configure the **Collected data key value** expression as `WsRow`.

    ![Electronic reporting format designer page](./media/ER-DeferredXml-Format3.png)

8.  Select the **Report\\Message\\Record\\TaxAmount** attribute.
9.  Configure the **Collected data key name** expression as `SummingAmountKey`.

    ![Electronic reporting format designer page](./media/ER-DeferredXml-Format4.png)

    You may consider this setting as the fulfillment of a virtual worksheet when the value of the A1 cell is appended by the value of tax amount from every processed tax transaction.

10.  Select the **Report\\Message\\Record\\RunningTotal** attribute.
11.  Select **Edit formula**.
12.  Configure the `SUMIF(SummingAmountKey, WsColumn, WsRow)` expression by using the [SUMIF](er-functions-datacollection-sumif.md) built-in ER function.
13.  Select **Save**.

     ![Electronic reporting formula designer page](./media/ER-DeferredXml-FormulaDesigner.png)

14.  Close the formula designer page.
15.  Select **Save**.
16.  Select **Run**.
17.  Download the offered by a web browser file and open it for review.

     ![Electronic reporting format designer page](./media/ER-DeferredXml-Run1.png)

     The last record node contains the tax value running total that is computed for all processed transactions by using the generated output as a data source - starting from the beginning of the report up to the last tax transaction inclusively. The summary node contains the sum of tax values for all processed transactions that is computed in model mapping by using the data source of the **GroupBy** type. Notice that these values equal which means that the output-based summing can be used instead of the **GroupBy** one. Comparing the execution time of the first record node and the summary node, you can see that It took 11 milliseconds to generate all record nodes and perform summing. From the record nodes generation and tax values summing perspective, the modified format is approximately in two times faster than the original one.

18.  Select the **Report\\Message\\Summary\\TotalTaxAmount** attribute.
19.  Select **Edit formula**.
20.  Enter the `SUMIF(SummingAmountKey, WsColumn, WsRow)` expression instead of the existing one.
21.  Select **Save**.
22.  Select **Run**.
23.  Download the offered by a web browser file and open it for review.

     ![Electronic reporting format designer page](./media/ER-DeferredXml-Run2.png)

     Now the tax value running total in the last record node equals the sum in the summary node.

## Place values of output-based summing to the report header

Assume that you must present the sum of tax values in the header of your report. You can modify your format for doing this.

1.  Select the **Format** tab.
2.  Select the **Report\\Message\\Summary** XML element.
3.  Select **Move up**.
4.  Select **Save**.
5.  Select **Run**.
6.  Download the offered by a web browser file and open it for review.

     ![Electronic reporting format designer page](./media/ER-DeferredXml-Run3.png)

     Notice that the sum of tax values in the summary node equals zero. It happens because now this sum is computed based on generated output and at the time when the first record node is generated, the generated output contains no record nodes with transaction details yet. You can configure this format to defer the execution of the **Report\\Message\\Summary** element until the **Report\\Message\\Record** element has been executed for all tax transactions.

## Defer execution of the summary XML element to use calculated total

1.  Select the **Report\\Message\\Summary** XML element.
2.  Set the **Deferred execution** option to **Yes**.

     ![Electronic reporting format designer page](./media/ER-DeferredXml-Format5.png)

3.  Select **Save**.
4.  Select **Run**.
5.  Download the offered by a web browser file and open it for review.

     ![Electronic reporting format designer page](./media/ER-DeferredXml-Run4.png)

     The execution of the **Report\\Message\\Summary** element is now performed at the end of execution of all other nested items of the **Report\\Message** element that is the parent element of the **Report\\Message\\Summary** one. Therefore, it happens after the execution of the **Report\\ Message\\Record** element for all tax transactions of the **model.Data.List** data source. The execution time of the first and last record nodes as well as the execution time of the header and summary nodes illustrates this.

## Additional resources

[Configure format to do counting and
summing](./tasks/er-format-counting-summing-1.md)

[Trace execution of ER format to troubleshoot performance
issues](trace-execution-er-troubleshoot-perf.md)

[Defer execution of a sequence element in ER format](er-defer-sequence-element.md#Example)
