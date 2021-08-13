---
# required metadata

title: Use DATA COLLECTION data sources in Electronic reporting formats
description: This topic explains how to use DATA COLLECTION data sources in Electronic reporting (ER) formats.
author: NickSelin
ms.date: 08/13/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: EROperationDesigner
# ROBOTS: 
audience: Application User, IT Pro
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.custom: 58771
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: nselin
ms.search.validFrom: 2021-01-01
ms.dyn365.ops.version: AX 10.0.16

---

# Use DATA COLLECTION data sources in Electronic reporting formats

[!include [banner](../includes/banner.md)]

## Overview

You can use the Operations designer of the [Electronic reporting (ER)](general-electronic-reporting.md) framework to configure the [format](general-electronic-reporting.md#FormatComponentOutbound) component of an ER solution that is used to generate outbound documents in different formats. The hierarchical structure of the configured format component consists of various types of format elements. These format elements are used to fill generated documents with the required information at runtime. By default, when you run an ER format, the format elements are run in the same order that they are presented in the format hierarchy: one by one, from top to bottom. When ER runs a format element that contains a binding, the formula of this binding is executed and the value is added to a generated document by this format element. For example, the binding can pass the value of a [data model](general-electronic-reporting.md#data-model-and-model-mapping-components) field to a format element. You can configure a DATA COLLECTION data source to collect values of such data model fields at runtime, perform value summing, and fill a generated document with the collected details. To this, change the initial binding to pass the value of a data model field to a format element by using the configured DATA COLLECTION data source. By passing values through the DATA COLLECTION data source, you can collect necessary details for further usage.

When you configure a DATA COLLECTION data source, specify a value type that will be managed in the data source. The following [data types](er-formula-supported-data-types-primitive.md) are currently supported to collect values:
- Boolean
- Date
- DateTime
- GUID
- Int64
- Integer
- Real
- String
- Time

You can use the `Collect(Value)` method of a DATA COLLECTION data source to pass a value to a data source for collection. HEre, the `Value` argument is the constant or the valid path to a data source field of the relevant data type.

Use the `Result` property of a DATA COLLECTION data source to access the list of collected values. This property returns the [Record list](er-formula-supported-data-types-composite.md#record-list) with records containing the `Value` field that you can use to access collected values.

By default, a DATA COLLECTION data source collects only unique values.

To collect all values, set the **Collect all values** field of the configured DATA COLLECTION data source to **Yes**. When the **Collect all values** field is set to ***Yes***, the parameterized property `Sum(Flag)` becomes available. You can use this property to get the total amount of all currently collected values. The `Flag` argument here is the [Boolean](er-formula-supported-data-types-primitive.md#boolean) value that you can use to indicate whether the total value must be reset.

   - When the value **False** is provided, summing is continued from the previously collected amount.
   - When the value **True** is provided, a new summing is started.

The following data types are currently supported for summing:

   - Int64
   - Integer
   - Real

To learn more about this feature, complete the example in this topic.

## Example: Configure an ER format to do counting and summing by using DATA COLLECTION data source

The following steps explain how a user in the System administrator or Electronic reporting functional consultant role can configure an ER format that contains a DATA COLLECTION data source using to calculate running totals and collect summed values.

These steps can be performed in the USMF company in Microsoft Dynamics 365 Finance.

### Upload and use the provided ER solution

1.  [Import](er-defer-sequence-element.md#import-the-sample-er-configurations) the sample ER configurations.
2.  [Activate](er-defer-sequence-element.md#activate-a-configurations-provider) a configuration provider.
3.  [Review](er-defer-sequence-element.md#review-the-imported-model-mapping) the imported model mapping.
4.  [Review](er-defer-sequence-element.md#review-the-imported-format) the imported format.
5.  [Run](er-defer-sequence-element.md#run-the-imported-format) the imported format.

### Run the format of the provided ER solution

1.  On the **Format designer** page, select **Run**.
2.  On the **Electronic report parameters** dialog box, select **OK**.
3.  Download and review the file that the web browser offers.

    ![Downloaded file - results of the initial format execution.](./media/er-data-collection-data-sources-01.png)

### Modify the format of the ER solution to calculate the running tax total

If the volume of transactions is much larger than the volume in the current example, the summing time might increase and can cause performance issues. By changing the setting of the format, you can help prevent these performance issues. Because you access tax values to include them in the generated report, you can reuse this information to sum tax values.

1.  On the **Format designer** page, on the **Mapping** tab, select **Add root**.
2.  In the **Add data source** dialog box, select **Functions** > **Data collection**.
3.  In the **'Data collection' data source properties** dialog box, in the **Name** field, enter **CollectedTaxValues**.
    1.  In the **Item type** field, select **Real**.
    2.  In the **Collect all values** field, select **Yes** and then select **OK**.
5.  Select the **Report\\Lines\\Record\\TaxAmount** numeric format element.
    
    > [!NOTE]
    > Currently, the `@.Value` binding is configured for this element to fill a generated document with tax values from the `model.Data.List.Value` field.

6.  Select **Edit formula**.
    1.  On the **Formula designer** page, in the **Formula** field, instead of `@.Value`, enter `CollectedTaxValues.Collect(@.Value)`.
    2.  Save changes and close the **Formula designer** page.

    > [!NOTE]
    > This binding will pass to a generated document, the same tax value. Additionally, those values will be collected in the **CollectedTaxValues** data source.

7.  Select the **Report\\Lines\\Record\\RunningTotal** numeric format element.
8.  Select **Edit formula**.
    1.  On the **Formula designer** page, in the **Formula** field, enter `CollectedTaxValues.Sum(false)`.
    2.  Save changes and close the **Formula designer** page.

    > [!NOTE]
    > This binding will pass to a generated document, the total amount of tax values that have been already populated to a generated document at this time.

    ![Numeric elements with updated bindings on the Format designer page.](./media/er-data-collection-data-sources-02.png)

9.  Select **Save** and on the **Format designer** page, select **Run**.
    1.  On the **Electronic report parameters** dialog box, select **OK**.
    2.  Download and review the file that the web browser offers.

    ![Downloaded file - results of the modified format execution.](./media/er-data-collection-data-sources-03.png)

### Modify the format to evaluate the list of collected tax values

1.  On the **Format designer** page, select the **Format** tab.
2.  Select the **Report\\Lines\\Record\\RunningTotal** numeric format element.
    1.  In the **Numeric type** field, instead of **Real** select **Integer**.
    2.  In the **Numeric format** field, instead of **F2** enter **F0**.
3.  Select the **Mapping** tab and select **Edit formula**.
    1.  On the **Formula designer** page, in the **Formula** field, enter `COUNT(CollectedTaxValues.Result)`.
    2.  Save changes and close the **Formula designer** page.

    > [!NOTE]
    > This binding will pass to a generated document, the number of records in the list where the tax values are collected.

5.  Select **Save** and on the **Format designer** page, select **Run**.
    1.  On the **Electronic report parameters** dialog box, select **OK**.
    2.  Download and review the file that the web browser offers.

    ![Downloaded file - results of another modified format execution.](./media/er-data-collection-data-sources-04.png)

## Frequently asked questions

### What is the difference in calculating running totals and collecting data between the usage of a DATA COLLECTION data source and built-in [DATA COLLECTION](er-functions-category-data-collection.md) functions?

Both of these techniques can be used for data collection, summing, and counting based on information that is passed to a generated outbound document. The following must be taken into consideration when you decide which one to use:

| Data source | Built-in functions |
|-------------| ------------------ |
| Collects only values | Collects named values so totals can be computed for separate groups of values <br>Groups can be extracted as a list as well <br>Text values can be collected as well |
| Automatically collects unique values | Additional settings are needed to extract the list of unique values from the collected values.  |
| Performance depends on the volume of collected values | Performance practically doesn't depend on the volume of collected values. |
| Works for all types of outbound documents | Works for only TEXT and XML documents. |

## Additional resources

- [Configure format to do counting and summing](./tasks/er-format-counting-summing-1.md)
- [Defer the execution of sequence elements in ER formats](er-defer-sequence-element.md#Example)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
