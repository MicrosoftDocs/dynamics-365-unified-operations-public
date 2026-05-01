---
title: Configure Electronic reporting (ER) to pull data into Power BI
description: Learn about how you can use your Electronic reporting (ER) configuration to arrange the transfer of data from your instance to Power BI services.
author: kfend
ms.author: filatovm
ms.topic: how-to
ms.date: 04/08/2026
ms.reviewer: johnmichalak
audience: Developer, IT Pro
ms.search.region: Global
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611
ms.assetid: 2685df16-5ec8-4fd7-9495-c0f653e82567
---

# Configure Electronic reporting (ER) to pull data into Power BI

[!include [banner](../includes/banner.md)]

This article explains how to use your Electronic reporting (ER) configuration to arrange the transfer of data from your instance to Power BI services. As an example, this article uses Intrastat transactions as business data that you must transfer. The Power BI map visualization uses this Intrastat transaction data to present a view for analysis of company import and export activities on the Power BI report.

## Overview

Microsoft Power BI is a collection of software services, apps, and connectors that work together to turn external sources of data into coherent, visually immersive, and interactive insights. Electronic reporting (ER) lets users easily configure data sources and arrange the transfer of data from the application to Power BI. The data is transferred as files in the OpenXML worksheet (Microsoft Excel workbook file) format. You store the transferred files on a Microsoft SharePoint Server that you configure for this purpose. Use the stored files in Power BI to make reports that include visualizations (tables, charts, maps, and so on). Share Power BI reports with Power BI users, and access them in Power BI dashboards and on the application pages. This article explains the following tasks:

- Configure Microsoft Dynamics 365 Finance.
- Prepare your ER format configuration to get data from the Finance application.
- Configure the ER environment to transfer data to Power BI.
- Use transferred data to create a Power BI report.
- Make the Power BI report accessible in Finance.

## Prerequisites

To complete the example in this article, you must have the following access:

- Access for one of the following roles:

  - Electronic reporting developer
  - Electronic reporting functional consultant
  - System administrator

- Access to the SharePoint Server that you configure for use with the application
- Access to the Power BI framework

## Configure document management parameters

1. On **Document management parameters**, configure access to the SharePoint Server that the company uses and that you sign in to (the DEMF company in this example).
1. Test the connection to the SharePoint Server to make sure that you have access.

    :::image type="content" source="./media/ger-power-bi-sharepoint-server-setting-1024x369.png" alt-text="Screenshot of the Document management parameters page." lightbox="./media/ger-power-bi-sharepoint-server-setting.png":::

1. Open the configured SharePoint site. Create a new folder where ER stores Excel files that have the business data that the Power BI reports require as a source of Power BI datasets.
1. On **Document types**, create a new document type that you use to access the SharePoint folder that you just created. Enter **File** in the **Group** field and **SharePoint** in the **Location** field, and then enter the address of the SharePoint folder.

    :::image type="content" source="./media/ger-power-bi-sharepoint-document-type-1024x485.png" alt-text="Screenshot of the Document types page." lightbox="./media/ger-power-bi-sharepoint-document-type.png":::

## Configure ER parameters

1. In the **Electronic reporting** workspace, select the **Electronic reporting parameters** link.
1. On the **Attachments** tab, select the **File** document type for all the fields.
1. In the **Electronic reporting** workspace, make the required provider active by selecting **Set active**. For more information, see the **ER Select service provider** task guide.

## Use an ER data model as the source of data

You must have an ER data model as the source of business data that Power BI reports use. You upload this data model from the ER configurations repository. For more information, see [Download Electronic reporting configurations from Lifecycle Services](download-electronic-reporting-configuration-lcs.md) or see the **ER Import a configuration from Lifecycle Services** task guide. Select **Intrastat** as the data model that you upload from the selected ER configurations repository. (In this example, version 1 of the model is used.) You can then access the **Intrastat** ER model configuration on the **Configurations** page.

:::image type="content" source="./media/ger-power-bi-data-model-1024x371.png" alt-text="Screenshot of the Intrastat ER model configuration on the Configurations page." lightbox="./media/ger-power-bi-data-model.png":::

## Design an ER format configuration

Create a new ER format configuration that uses the **Intrastat** data model as the source of business data. This format configuration generates output results as electronic documents in OpenXML (Excel file) format. For more information, see the **ER Create a configuration for reports in OPENXML format** task guide. Name the new configuration **Import / export activities**, as shown in the following illustration. Use the [ER data - import and export details](https://download.microsoft.com/download/f/7/5/f755c0fd-025c-4aa9-920b-909abb8302ad/ER-data-import-and-export-details.xlsx) Excel file as a template when you design the ER format. For information about how to import a format template, see the task guide.

:::image type="content" source="media/ger-power-bi-format-configuration.png" alt-text="Screenshot of the Import / export activities configuration." lightbox="media/ger-power-bi-format-configuration.png":::

To modify the **Import / export activities** format configuration, follow these steps:

1. Select **Designer**.
1. On the **Format** tab, name the file element for this format **Excel output file**.

    :::image type="content" source="./media/ger-power-bi-format-configuration-file-element-name-1024x395.png" alt-text="Screenshot of the Excel output file element." lightbox="./media/ger-power-bi-format-configuration-file-element-name.png":::

1. On the **Mapping** tab, specify the name of the Excel file that this format generates whenever it runs. Configure the related expression to return the value **Import and export details**. The .xlsx file name extension is added automatically.

    :::image type="content" source="./media/ger-power-bi-format-configuration-output-file-name-1024x396.png" alt-text="Screenshot of the Format designer." lightbox="./media/ger-power-bi-format-configuration-output-file-name.png":::

1. Add a new data source item for this format. This enumeration is required for further data binding.

    1. Name the data source **direction\_enum**.
    1. Select **Data model enumeration** as the data source type.
    1. Refer to the **Direction** data model enumeration.

    :::image type="content" source="./media/ger-power-bi-format-configuration-mapping-added-enum-1024x454.png" alt-text="Screenshot of the direction_enum data source." lightbox="./media/ger-power-bi-format-configuration-mapping-added-enum.png":::

1. Bind elements of the **Intrastat** data model to elements of the designed format, as shown in the following illustration.

    :::image type="content" source="./media/ger-power-bi-format-configuration-mapping-details-1024x454.png" alt-text="Screenshot of completing the binding." lightbox="./media/ger-power-bi-format-configuration-mapping-details.png":::

After you run it, the ER format generates the output result in Excel format. It sends the details of the Intrastat transactions to the output result, and separates them as transactions that describe either import activities or export activities. Select **Run** to test the new ER format for the list of Intrastat transactions on the **Intrastat** page (**Tax** &gt; **Declarations** &gt; **Foreign trade** &gt; **Intrastat**).

:::image type="content" source="./media/ger-power-bi-format-test-run-transactions-1024x322.png" alt-text="Screenshot of the Intrastat page." lightbox="./media/ger-power-bi-format-test-run-transactions.png":::

The following output result is generated. The file is named **Import and export details.xlsx**, as you specified in the format settings.

:::image type="content" source="./media/ger-power-bi-format-test-run-output-1024x472.png" alt-text="Screenshot of the Import and export details.xlsx output file." lightbox="./media/ger-power-bi-format-test-run-output.png":::

## Configure the ER destination

You must configure the ER framework to send the output result of the new ER format configuration in a special way.

- The output result must go to the folder of the selected SharePoint Server.
- Each execution of the format configuration must create a new version of the same Excel file.

On **Electronic reporting** (**Organization administration** > **Electronic reporting**), select **Electronic reporting destination**, and add a new destination. In the **Reference** field, select the **Import / export activities** format configuration that you created earlier. Follow these steps to add a new file destination record for the reference.

1. In the **Name** field, enter the title of the file destination.
1. In the **File name** field, select the name **Excel output file** for the Excel file format component.

Select the **Settings** button for the new destination record. Then, in the **Destination settings** dialog box, follow these steps:

1. On the **Power BI** tab, set the **Enabled** option to **Yes**.
1. In the **SharePoint** field, select the **Shared** document type that you created earlier.

## Schedule execution of the configured ER format

1. On **Configurations** (**Organization administration** > **Electronic reporting** > **Configurations**), in the configurations tree, select the **Import / export activities** configuration that you created earlier.
1. Change the status of version 1.1 from **Draft** to **Complete** to make this format available for use.

    :::image type="content" source="./media/ger-power-bi-format-configuration-complete-1024x401.png" alt-text="Screenshot of the Import/export activities configuration on the Configurations page." lightbox="./media/ger-power-bi-format-configuration-complete.png":::

1. Select the completed version of the **Import / export activities** configuration, and then select **Run**. The configured destination is applied to the output result that is generated in Excel format.
1. Set the **Batch processing** option to **Yes** to run this report in unattended mode.
1. Select **Recurrence** to schedule the required recurrence of this batch execution. The recurrence defines how often the updated data is transferred to Power BI.

    :::image type="content" source="./media/ger-power-bi-format-configuration-run-to-schedule-1024x413.png" alt-text="Screenshot of the Electronic report parameters dialog box." lightbox="./media/ger-power-bi-format-configuration-run-to-schedule.png":::

1. After you configure it, you can find the ER report execution job on the **Batch jobs** page (**System administration** > **Inquiries** > **Batch jobs**).

    :::image type="content" source="./media/ger-power-bi-format-configuration-running-job-1024x410.png" alt-text="Screenshot of the Batch jobs page." lightbox="./media/ger-power-bi-format-configuration-running-job.png":::

1. When you run this job for the first time, the destination creates a new Excel file that has the configured name in the selected SharePoint folder. Every subsequent time that you run the job, the destination creates a new version of this Excel file.

    :::image type="content" source="./media/ger-power-bi-output-file-in-sharepoint-server-folder-2-1024x412.png" alt-text="Screenshot of the new version of the Excel file." lightbox="./media/ger-power-bi-output-file-in-sharepoint-server-folder-2.png":::

## Create a Power BI dataset by using the output result of the ER format

1. Sign in to Power BI, and either open an existing Power BI group (workspace) or create a new group. Either click **Add** under **Files** in the **Import or Connect to Data** section, or click the plus sign (**+**) next to **Datasets** in the left pane.

    :::image type="content" source="./media/ger-power-bi-add-dataset-1024x524.png" alt-text="Screenshot of creating a dataset." lightbox="./media/ger-power-bi-add-dataset.png":::

1. Select the **SharePoint – Team sites** option, and then enter the path of SharePoint Server that you're using (`https://ax7partner.litware.com` in our example).
1. Browse to the **/Shared Documents/GER data/PowerBI** folder, and select the Excel file that you created as the source of data for the new Power BI dataset.

    :::image type="content" source="./media/ger-power-bi-add-dataset-select-excel-file-1024x522.png" alt-text="Screenshot of selecting the Excel file." lightbox="./media/ger-power-bi-add-dataset-select-excel-file.png":::

1. Click **Connect**, and then click **Import**. A new dataset is created that is based on the selected Excel file. The dataset can also be added automatically to the newly created dashboard.

    :::image type="content" source="./media/ger-power-bi-added-dataset-1024x489.png" alt-text="Screenshot of the dataset on the dashboard." lightbox="./media/ger-power-bi-added-dataset.png":::

1. Configure the refresh schedule for this dataset to force a periodic update. Periodic updates enable the consumption of new business data that comes via periodic execution of the ER report through new versions of the Excel file that are created on the SharePoint Server.

## Create a Power BI report by using the new dataset

1. Select the **Import and export details** Power BI dataset that you created.
1. Configure the visualization. For example, select the **Filled map** visualization, and configure it as follows:

    - Assign the **CountryOrigin** dataset field to the **Location** field of the map visualization.
    - Assign the **Amount** dataset field to the **Color saturation** field of the map visualization.
    - Add the **Activity** and **Year** dataset fields to the **Filters** fields collection of the map visualization.

1. Save the Power BI report as **Import and export details report**.

    :::image type="content" source="./media/ger-power-bi-added-report-1024x498.png" alt-text="Screenshot of the Import and export details report." lightbox="./media/ger-power-bi-added-report.png":::

    The map shows the countries and regions that are mentioned in the Excel file (Austria and Switzerland in this example). These countries and regions are colored to show the proportion of invoiced amounts for each.

1. Update the list of Intrastat transactions. The export transaction that originated from Italy is added.

    :::image type="content" source="./media/ger-power-bi-new-run-new-transaction-1024x321.png" alt-text="Screenshot of the Intrastat transactions list." lightbox="./media/ger-power-bi-new-run-new-transaction.png":::

1. Wait for the next scheduled execution of the ER report and the next scheduled update of the Power BI dataset. Then review the Power BI report (select to show import transactions only). The updated map now shows Italy.

    :::image type="content" source="./media/ger-power-bi-new-run-new-map-1024x511.png" alt-text="Screenshot of the updated map." lightbox="./media/ger-power-bi-new-run-new-map.png":::

## Access Power BI report in Finance

Set up the integration with Power BI. For more information, see [Configure Power BI integration for workspaces](configure-power-bi-integration.md).

1. On the **Electronic reporting** workspace page that supports Power BI integration (**Organization administration** &gt; **Workspaces** &gt; **Electronic reporting workspace**), select **Options** &gt; **Open report catalog**.
1. Select the **Import and export details** Power BI report that you created, to show that report as an action item on the selected page.
1. Select the action item to open the page that shows the report that you designed in Power BI.

    :::image type="content" source="./media/ger-power-bi-review-bi-report-in-ax-form-1024x586.png" alt-text="Screenshot of the Import and export details report designed in Power BI." lightbox="./media/ger-power-bi-review-bi-report-in-ax-form.png":::

## Additional resources

[Electronic reporting (ER) destinations](electronic-reporting-destinations.md)

[Electronic reporting (ER) overview](general-electronic-reporting.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
