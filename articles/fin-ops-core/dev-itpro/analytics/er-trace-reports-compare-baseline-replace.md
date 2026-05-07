---
title: Improve tracing the results of generated ER reports to compare with baseline values
description: Learn about improvements to the ER baseline feature in Microsoft Dynamics 365 Finance version 10.0.3 (June 2019).
author: kfend
ms.author: filatovm
ms.topic: how-to
ms.date: 04/08/2026
ms.reviewer: johnmichalak
audience: Developer, IT Pro
ms.search.region: Global
ms.search.validFrom: 2018-04-01
ms.dyn365.ops.version: Release 8.0
ms.assetid: 2685df16-5ec8-4fd7-9495-c0f653e82567
ms.custom: sfi-image-nochange
---

# Improve tracing the results of generated ER reports to compare with baseline values

[!include[banner](../includes/banner.md)]

This article describes the first set of improvements to the baseline feature of the Electronic reporting (ER) framework. These improvements are available in Microsoft Dynamics 365 Finance version 10.0.3 (June 2019) and later.

## Automate the setting of baseline rules

The [Trace generated report results and compare them with baseline values](er-trace-reports-compare-baseline.md) article explains how to configure the ER framework to collect information about ER format executions and evaluate the results of those executions. The example in this article shows the steps that you must complete.

Here are some of the steps:

- Run an ER format to generate an outbound file, and store the file locally.
- Add the locally stored file as an attachment of the baseline that you added for an ER format.
- Configure the baseline rule for the added baseline. This configuration includes the following steps:

  - Specify an ER format element that you use to generate an outbound file.
  - Select the attachment that refers to the generated outbound file.

> [!NOTE]
> You must complete these steps manually, even though the new ER capabilities enable you to automate them. To learn more about this feature, complete the following example.

## Example: Automate the setting of baseline rules

To complete the steps in this example, you must first complete the steps in the example in the [Trace generated report results and compare them with baseline values](er-trace-reports-compare-baseline.md) article, up through the "Add a new baseline for a designed ER format" section.

### Review added baseline

1. Go to **Organization administration** > **Electronic reporting** > **Configurations**.
1. Select **Baselines**.

    > [!NOTE]
    > The **Baselines** button on the Action Pane is available only when the **Run in debug mode** ER user parameter is turned on for the current company.

The baseline is added for the selected **Format to learn ER baselines** format, but you didn't add baseline rules for this baseline yet.

:::image type="content" source="media/GER-BaselineSample-AddBaseline2.PNG" alt-text="Screenshot of the Electronic reporting format baselines page, no rules yet.":::

### Create a new baseline rule

1. Go to **Organization administration** > **Electronic reporting** > **Configurations**.
1. In the tree, expand **Model to learn ER baselines**.
1. In the tree, select **Model to learn ER baselines\\Format to learn ER baselines**.
1. On the **Versions** FastTab, select **Run**.
1. In the **Enter Id** field, enter **1**.
1. Set the **Make baseline files** option to **Yes**.
1. Select **OK**.
1. Select **Baselines**.

    :::image type="content" source="media/GER-BaselineSample-ReviewAddedBaselineLine.PNG" alt-text="Screenshot of the Electronic reporting format baselines page with baselines selected.":::

    The generated outbound file is automatically attached to the baseline of the executed ER format. The baseline rule is automatically added to this baseline and also contains the reference to the attached file.

1. In the **Name** field, enter **Baseline 1**.
1. In the **File name mask** field, enter **.xml**.
1. Select **Save**.

### Run the format

You're now ready to complete the remaining steps in the example in the [Trace generated report results and compare them with baseline values](er-trace-reports-compare-baseline.md) article, starting from the "Run the designed ER format and review the log to analyze the results" section.

> [!NOTE]
> When you delete the automatically added baseline rule on the **Baselines** FastTab, the referenced attachment isn't automatically deleted.

## Configure the baseline to ignore constantly changing parts of the ER output

When you design an ER format to contain information that changes when the format runs, you must use the ER baseline feature to compare the generated results with baseline values. For example, the information might be the processing date and time or the unique identifier of a generated document in different formats (globally unique identifier \[GUID\], and so on). The new ER capabilities let you configure the baseline rule to ignore changeable elements of an ER format when the format runs with the purpose of comparing baseline values with the results of the format's execution. To learn more about this feature, complete the following example.

## Example: Configure the baseline to ignore constantly changing parts of the ER output

To complete the steps in this example, you must first complete the steps in the example in the [Trace generated report results and compare them with baseline values](er-trace-reports-compare-baseline.md) article.

### Modify a configured ER format

1. Go to **Organization administration** > **Electronic reporting** > **Configurations**.
1. In the tree, expand **Model to learn ER baselines**.
1. In the tree, select **Model to learn ER baselines\\Format to learn ER baselines**.
1. Select **Designer**.
1. In the tree, select **Output\\Document**.
1. Select **Add**.
1. In the drop-down dialog box, in the tree, select **XML\\Attribute**.
1. In the **Name** field, enter **ProcessingDateTime**.
1. Select **OK**.
1. On the **Mapping** tab, in the tree, select **Output\\Document\\ProcessingDateTime**.
1. Select **Edit formula**.
1. In the **Formula** field, enter the following expression: **DATETIMEFORMAT(NOW(), "O")**
1. Select **Save**, and then select **Test**.
1. Select **Test** again to retest the configured expression.

    :::image type="content" source="media/GER-BaselineSample-DefineProcessingDTExpression.PNG" alt-text="Screenshot of the Formula designer page.":::

    > [!NOTE]
    > The **Test result** tab shows that the configured expression returns a different date and time value whenever it's called.

1. Close the **Formula designer** page, and then select **Save**.

    :::image type="content" source="media/GER-BaselineSample-FormatMappingDesign2.PNG" alt-text="Screenshot of the Format designer page.":::

1. Close the **Format designer** page.

### Remove an existing baseline rule

1. Go to **Organization administration** > **Electronic reporting** > **Configurations**.
1. Select **Baselines**.
1. In the list of baselines, select the baseline that you configured for the **Format to learn ER baselines** format.
1. On the **Baselines** FastTab, select **Delete** to remove the baseline rule that you configured earlier.

:::image type="content" source="media/GER-BaselineSample-AddBaseline3.PNG" alt-text="Screenshot of the Electronic reporting format baselines page after deletion.":::

### Define replacements for bindings of designed ER format

1. On the **Configurations** page, on the **Replacements** FastTab, select **Select components**.
1. In the format components tree, expand **Output**, expand **Output\\Document**, and then select the check box for **Output\\Document\\ProcessingDateTime**.
1. Select **OK**.

:::image type="content" source="media/GER-BaselineSample-AddBaseline4.PNG" alt-text="Screenshot of the Electronic reporting format baselines page with components selected.":::

The selected ER format component is added to the list of components on the **Replacements** FastTab. When you run the base ER format in debug mode, the format's binding for each component is replaced by the binding that appears in the **Binding** column. To change the default binding for a component that appears on the **Replacements** FastTab, select **Edit**.

### Create a new baseline rule

Follow the steps in the "Example: Automate the setting of baseline rules" section earlier in this article. A notification warns you that the outbound file is generated by using baseline settings, and that a forced replacement of the format bindings occurs.

:::image type="content" source="media/GER-BaselineSample-FormatRunToMakeBaselineFile4.PNG" alt-text="Screenshot of the notification on the Configurations page.":::

### Suppress warnings about the replacement of format bindings

Set specific ER parameters to suppress notifications about the replacement of format bindings. This suppression is useful when the Regression Suite Automation Tool replaces format bindings in unattended mode. In this case, the warning can cause the test case to fail.

1. On **Configurations**, on the Action Pane, on the **Configurations** tab, select **User parameters**.
1. Set the **Suppress baseline warnings** option to **Yes**, and then select **OK**.

### Review the generated baseline file

1. Go to **Organization administration** > **Electronic reporting** > **Configurations**.
1. Select **Baselines**.
1. Select **Attachments**.
    > [!NOTE]
    > The generated file contains the processing date and time text (**"#"**) from the binding that you configured in the added baseline rule, not from the format's binding.

1. Close **Attachments**.

### Run the designed ER format and review the log to analyze the results

1. Go to **Organization administration** > **Electronic reporting** > **Configurations**.
1. In the tree, expand **Model to learn ER baselines**.
1. In the tree, select **Model to learn ER baselines\\Format to learn ER baselines**.
1. On the **Versions** FastTab, select **Run**.
1. In the **Enter Id** field, type **1**.
1. Select **OK**.
1. Go to **Organization administration** > **Electronic reporting** > **Configuration debug logs**.

The execution log contains information about the results of the comparison of the generated file with the configured baseline. The log indicates that the generated file and the baseline are equal, even though the executed format contains the binding to enter a constantly changing date and time value in the outbound file.

> [!NOTE]
> Although the outbound file is generated by using baseline settings that force the replacement of the format's bindings, you don't receive any warnings about the replacement.

## Exchange baseline settings between environments

### Export baseline settings

The new ER capabilities let you export baseline settings for the selected ER format from the current environment and store them as XML files.

To export baseline settings, on the **Electronic reporting format baselines** page, select **Export**.

### Import baseline settings

You can import exported baseline settings into a different environment. First, import the environment as an ER format. Then, import the baseline settings.

To import baseline settings from a locally stored XML file, on the **Electronic reporting format baselines** page, select **Import**, and then select **Browse** to select the XML file.

:::image type="content" source="media/GER-BaselineSample-ImportBaseline1.PNG" alt-text="Screenshot of the Import baseline settings dialog box.":::

To import baseline settings from an XML file that is stored on the Microsoft SharePoint Server, based on the current Document management settings and the selected document type, on the **Electronic reporting format baselines** page, select **Import from source**. Then select the document type and the XML file. You must configure the required document type to access the SharePoint folder.

:::image type="content" source="media/GER-BaselineSample-ImportBaseline2.PNG" alt-text="Screenshot of the Import from source dialog box.":::

> [!NOTE]
> Use Task recorder to record the steps for selecting the required document type and the file name in the **Import from source** dialog box. By using this method, you can keep required baseline settings on SharePoint Server and then automatically import them by playing a task recording when you run automated tests by using the Regression Suite Automation Tool.

## Additional resources

- [Trace generated report results and compare them with baseline values](er-trace-reports-compare-baseline.md)
- [Task recorder resources](../user-interface/task-recorder.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
