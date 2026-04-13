---
title: Trace generated report results and compare them with baseline values
description: Learn how to compare the results of generated Electronic reporting (ER) reports with baseline report values, including examples.
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

# Trace generated report results and compare them with baseline values

[!include[banner](../includes/banner.md)]

You can trace the results of Electronic reporting (ER) formats that generate outgoing electronic documents. When you turn on trace generation by using the **Run in debug mode** ER user parameter, the system creates a new trace record in the ER format execution log every time it runs an ER report. Each trace record stores the following details:

- All warnings that validation rules generate
- All errors that validation rules generate
- All generated files that are stored as attachments of the trace record

You can store individual baseline application files for any ER format. Files are baseline files when they describe the expected results of reports that are run. If a baseline file exists for an ER format that you run while trace generation is turned on, the trace stores, in addition to the earlier mentioned details, the result of the comparison of the generated electronic document with the baseline file. In one click, you can also get the generated electronic document and its baseline file in a single zip file. You can then do detailed comparison by using an external tool such as WinDiff.

You can evaluate the trace to analyze whether the electronic documents that are generated include the expected content. You can do this evaluation in a user acceptance testing (UAT) environment when the code base changes (for example, when you migrated to a new instance of the application, installed hotfix packages, or deployed code modifications). In this way, you make sure that the evaluation doesn't affect the execution of ER reports that are used. For many ER reports, the evaluation can be done in unattended mode.

To learn more about this feature, watch the **ER Generate reports and compare results (Part 1)** and **ER Generate reports and compare results (Part 2)** task guides. These task guides are part of the **7.5.4.3 Test IT services/solutions (10679)** business process and can be downloaded from the [Microsoft Download Center](https://go.microsoft.com/fwlink/?linkid=874684). These task guides walk you through the process of configuring the ER framework to use baseline files to evaluate generated electronic documents.

## Example: Trace generated report results and compare them with baseline values

This procedure explains how to configure the ER framework to collect information about ER format executions and then evaluate the results of those executions. As part of that evaluation, generated documents are compared with their baseline files. In this example, you create the required ER configurations for the Litware, Inc. sample company. This procedure is intended for users who have the System administrator or Electronic reporting developer role assigned to them. You can complete these steps by using any data set.

To complete the steps in this example, you must first complete the steps in [Create configuration providers and mark them as active](tasks/er-configuration-provider-mark-it-active-2016-11.md).

1. Go to **Organization administration** > **Workspaces** > **Electronic reporting**.
1. On **Localization configurations**, in the **Configuration providers** section, verify that the configuration provider for the Litware, Inc. sample company is listed and marked as **Active**. If you don't see this configuration provider, follow the steps in [Create configuration providers and mark them as active](tasks/er-configuration-provider-mark-it-active-2016-11.md).

### Configure document management parameters

1. Go to **Organization administration** > **Document management** > **Document types**, and create a new document type to store baseline files.
1. In the **Class** field, enter **Attach file**.
1. In the **Group** field, enter **File**.

   :::image type="content" source="media/GER-BaselineSample-SetupDocumentType.PNG" alt-text="Screenshot of the Document types page.":::

   > [!NOTE]
   > You must configure a new document type with the same name for each data set where you plan to use the ER baseline feature.

### Configure ER parameters to start using the baseline feature

1. In the **Electronic reporting** workspace, in the **Related links** section, select **Electronic reporting parameters**.

   :::image type="content" source="media/GER-BaselineSample-ERWorkspace.PNG" alt-text="Screenshot of the Electronic reporting workspace.":::

1. On the **Attachments** tab, in the **Baseline** field, enter or select the document type that you just created.

   :::image type="content" source="media/GER-BaselineSample-ERParameters.PNG" alt-text="Screenshot of the Electronic reporting parameters.":::

1. Select **Save**, and then close the **Electronic reporting parameters** page.

### Add a new ER model configuration

1. In the **Electronic reporting** workspace, in the **Configurations** section, select the **Reporting configurations** tile.
1. On the Action Pane, select **Create configuration**.
1. In the drop-down dialog box, in the **Name** field, enter **Model to learn ER baselines**.
1. Select **Create configuration** to confirm the creation of a new ER data model entry.

   :::image type="content" source="media/GER-BaselineSample-ModelAdd.PNG" alt-text="Screenshot of the Create configuration dialog with 'Model to learn ER baselines' in the Name field and Create configuration button.":::

### Design a data model

1. On **Configurations**, on the Action Pane, select **Designer**.
1. Select **New**.
1. In the drop-down dialog box, in the **Name** field, enter **Root**.
1. Select **Add**.
1. Select **Root reference**.
1. Select **OK**, and then select **Save**.
1. Close the **Model designer** page.
1. Select **Change status**.
1. Select **Complete**, and then select **OK**.

   :::image type="content" source="media/GER-BaselineSample-ModelComplete.PNG" alt-text="Screenshot of the Configurations page.":::

### Add a new ER format configuration

1. On **Configurations**, on the action pane, select **Create configuration**.
1. In the drop-down dialog box, in the **New** field group, select **Format based on data model Model to learn ER baselines**.
1. In the **Name** field, enter **Format to learn ER baselines**.
1. Select **Create configuration** to confirm the creation of a new ER format entry.

   :::image type="content" source="media/GER-BaselineSample-FormatAdd.PNG" alt-text="Screenshot of Create configuration dialog with Format based on data model option selected and Name field filled.":::

### Design a format

For this example, create a simple ER format to generate XML documents.

1. On **Configurations**, on the Action Pane, select **Designer**.
1. Select **Add root**.
1. In the drop-down dialog box, follow these steps:

   1. In the tree, select **Common\\File**.
   1. In the **Name** field, enter **Output**.
   1. Select **OK**.

1. Select **Add**.
1. In the drop-down dialog box, follow these steps:

   1. In the tree, select **XML\\Element**.
   1. In the **Name** field, enter **Document**.
   1. Select **OK**.

1. In the tree, select **Output\\Document**.
1. Select **Add**.
1. In the drop-down dialog box, follow these steps:

   1. In the tree, select **XML\\Attribute**.
   1. In the **Name** field, enter **ID**.
   1. Select **OK**.

      :::image type="content" source="media/GER-BaselineSample-FormatLayoutDesign.PNG" alt-text="Screenshot of Format designer showing Document XML Element selected with Id XML Attribute in the tree.":::

1. On the **Mapping** tab, select **Delete**.
1. Select **Add root**.
1. In the drop-down dialog box, in the tree, select **General\\User input parameter**, and then follow these steps:

   1. In the **Name** field, enter **ID**.
   1. In the **Label** field, enter **Enter ID**.
   1. Select **OK**.

1. In the tree, select **Output\\Document\\Id**.
1. Select **Bind**, and then select **Save**.

   :::image type="content" source="media/GER-BaselineSample-FormatMappingDesign.PNG" alt-text="Screenshot of Format designer Mapping tab with Id XML Attribute bound to User input parameter Description.":::

Based on the designed structure, the configured format generates an XML file. This XML contains the **Root** element that has the **ID** attribute set to the value that the user enters in the ER runtime dialog box.

### Generate a new baseline file for a designed ER format

1. On **Configurations**, on the **Versions** FastTab, select **Run**.
1. In the **Enter ID** field, enter **1**.
1. Select **OK**.

   :::image type="content" source="media/GER-BaselineSample-FormatRunToMakeBaselineFile1.PNG" alt-text="Screenshot of the Electronic report parameters dialog box.":::

1. Save a local copy of the **out.Admin.xml** file that is generated, so you can use it later as a baseline for this ER format.

   :::image type="content" source="media/GER-BaselineSample-FormatRunToMakeBaselineFile2.PNG" alt-text="Screenshot of the notification about the generated file on the Configurations page.":::

### Configure ER parameters to use the baseline feature

1. On **Configurations**, on the Action Pane, on the **Configurations** tab, select **User parameters**.
1. Set the **Run in debug mode** option to **Yes**.
1. Select **OK**.

   :::image type="content" source="media/GER-BaselineSample-ERUserParameters.PNG" alt-text="Screenshot of the User parameters dialog box.":::

### Add a new baseline for designed ER format

1. Go to **Organization administration** > **Electronic reporting** > **Configurations**.
1. On the Action Pane, select **Baselines**.

   :::image type="content" source="media/GER-BaselineSample-OpenBaselinePage.PNG" alt-text="Screenshot of the Baselines button on the Configurations page.":::

1. On the Action Pane, select **New**.
1. Select the **Format to learn ER baselines** ER format that you designed earlier.
1. Select **Save**.

   :::image type="content" source="media/GER-BaselineSample-AddBaseline.PNG" alt-text="Screenshot of Electronic reporting format baselines page with empty Baselines grid and Format to learn ER baselines selected.":::

The baseline is added for the **Format to learn ER baselines** format.

### Configure a baseline rule for the added baseline

1. On **Electronic reporting format baselines**, on the Action Pane, select the **Attachments** button (the paper clip symbol).
1. On the Action Pane, select **New** \> **File**. In the ER parameters, select the **File** document type as the document type that stores baseline files.
1. Select **Browse**, and select the **out.Admin.xml** file that was generated when you ran the configured ER format earlier.

   :::image type="content" source="media/GER-BaselineSample-UploadBaselineFile.PNG" alt-text="Screenshot of the Attachments page.":::

1. Close the **Attachments** page.
1. On the **Baselines** FastTab, select **New**.
1. In the **Name** field, enter **Baseline 1**.
1. In the **File component name** field, enter or select **Output**. This value indicates that the configured baseline is compared with a file that uses the **Output** format element.
1. In the **File name mask** field, enter **\*.xml**.

   > [!NOTE]
   > You can define the file name mask. When you define the file name mask, the baseline record evaluates the generated output only when the name of the output file satisfies that mask.

1. If users must run the **Format to learn ER baselines** ER format and sign in to specific companies to use the configured baseline, select those companies in the **Companies** field.
1. In the **Baseline** field, enter or select the **out.Admin** attachment.
1. Select **Save**.

   :::image type="content" source="media/GER-BaselineSample-SetupBaselineLine.PNG" alt-text="Screenshot of Electronic reporting format baselines page showing Baseline 1 with Output component, *.xml mask, and out.Admin baseline selected.":::

### Run the designed ER format and review the log to analyze the results

1. Go to **Organization administration** > **Electronic reporting** > **Configurations**.
1. In the tree, expand **Model to learn ER baselines**, and then select **Model to learn ER baselines\\Format to learn ER baselines**.
1. On the **Versions** FastTab, select **Run**.
1. In the **Enter ID** field, enter **1**.
1. Select **OK**.
1. Go to **Organization administration** > **Electronic reporting** > **Configuration debug logs**.

   :::image type="content" source="media/GER-BaselineSample-ReviewBaselineComparison1.PNG" alt-text="Screenshot of the Electronic reporting run logs page.":::

   > [!NOTE]
   > The execution log contains information about the results of the comparison of the generated file with the configured baseline. In this example, the log indicates that the generated file and the baseline are equal.

1. Select **Delete all**.

### Run the designed ER format and review the log to analyze the results

1. Go to **Organization administration** > **Electronic reporting** > **Configurations**.
1. In the tree, expand **Model to learn ER baselines**, and then select **Model to learn ER baselines\\Format to learn ER baselines**.
1. On the **Versions** FastTab, select **Run**.
1. In the **Enter ID** field, enter **2**.
1. Select **OK**.
1. Go to **Organization administration** > **Electronic reporting** > **Configuration debug logs**.

   :::image type="content" source="media/GER-BaselineSample-ReviewBaselineComparison2.PNG" alt-text="Screenshot of Electronic reporting run logs showing a warning that generated file 'out.Admin.xml' differs from baseline.":::

   > [!NOTE]
   > The execution log contains information about the results of the comparison of the generated file with the configured baseline. In this example, the log indicates that the generated file and the baseline differ.

1. Select **Compare**.

  > [!NOTE]
  > The generated file and the baseline file are offered as a zip file. You can use external comparison tools such as WinDiff to compare the files and review the differences.

## Additional resources

- [Configure the Electronic reporting (ER) framework](electronic-reporting-er-configure-parameters.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
