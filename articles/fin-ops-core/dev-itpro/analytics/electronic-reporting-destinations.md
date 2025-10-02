---
title: Electronic reporting (ER) destinations
description: Learn about the management of Electronic reporting destinations, the types of supported destinations, and security considerations.
author: liza-golub
ms.author: egolub
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 10/01/2025
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2016-05-31
ms.search.form: DocuType, ERSolutionTable
ms.dyn365.ops.version: AX 7.0.1
ms.assetid: f3055a27-717a-4c94-a912-f269a1288be6
---

# Electronic reporting (ER) destinations

[!include [banner](../includes/banner.md)]

You configure a destination for each Electronic reporting (ER) format configuration and its output component (a folder or a file). Users who have appropriate access rights can also modify destination settings at runtime. This article explains ER destination management, the types of destinations that are supported, and security considerations.

ER format configurations usually contain at least one output component: a file. Typically, configurations contain multiple file output components of different types (for example, XML, TXT, XLSX, DOCX, or PDF) that are grouped into either a single folder or multiple folders. ER destination management lets you preconfigure what occurs when each component runs. By default, when you run a configuration, a dialog box appears that lets you save or open the file. The same behavior also occurs when you import an ER configuration and don't configure any specific destinations for it. After you create a destination for a main output component, that destination overrides the default behavior, and the folder or file is sent according to the destination's settings.

## Overview

You can set up destinations only for ER configurations that you [import](general-electronic-reporting.md#importing-an-er-component-from-lcs-to-use-it-internally) into the current Finance instance and for the formats that are available on the **Electronic reporting configurations** page. You can access ER destination management at **Organization administration** \> **Electronic reporting** \> **Electronic reporting destination**.

### Default behavior

The default behavior for an ER format configuration depends on the execution type that you specify when an ER format starts.

For example, in the **Intrastat Report** dialog box, on the **Run in the background** FastTab, if you set the **Batch processing** option to **No**, an ER format runs immediately in interactive mode. When this execution completes successfully, a generated outbound document is available for download.

If you set the **Batch processing** option to **Yes**, an ER format runs in [batch](../sysadmin/batch-processing-overview.md) mode. The appropriate batch job is created based on the parameters that you specify on the **Run in the background** tab of the **ER parameters** dialog box.

> [!NOTE]
> The job description informs you about the run of an ER format mapping. It also contains the name of the ER component that runs.

:::image type="content" source="./media/ER_Destinations-RunInBatchMode.png" alt-text="Screenshot of running an ER format in batch mode dialog.":::

You can find information about this job in several places:

- Go to **Common** \> **Inquiries** \> **Batch jobs** \> **My batch jobs** to check the status of the scheduled job.
- Go to **Organization administration** \> **Electronic reporting** \> **Electronic reporting jobs** to check the status of the scheduled job and the execution results of the completed job. When job execution completes successfully, select **Show files** on the **Electronic reporting jobs** page to get a generated outbound document.

    > [!NOTE]
    > This document is stored as an attachment of the current job record and is controlled by the [Document management](../../fin-ops/organization-administration/configure-document-management.md) framework. The [document type](../../fin-ops/organization-administration/configure-document-management.md#configure-document-types) that is used to store ER artifacts of this type is configured in the [ER parameters](electronic-reporting-er-configure-parameters.md#parameters-to-manage-documents).

- On the **Electronic reporting jobs** page, select **Show files** to view the list of any errors and warnings that were generated during job execution.

    :::image type="content" source="./media/ER_Destinations-ReviewERJobs.png" alt-text="Screenshot of reviewing the ER jobs list page.":::

### User-configured behavior

On the **Electronic reporting destination** page, you can override the default behavior for a configuration. Imported configurations don't appear on this page until you select **New** and then, in the **Reference** field, select a configuration to create destination settings for.

:::image type="content" source="./media/ER_Destinations-SelectFormat.png" alt-text="Screenshot of selecting a configuration in the Reference field.":::

After you create a reference, you can create a file destination for each **Folder** or **File** output component of the referenced ER format.

:::image type="content" source="./media/ER_Destinations-ConfigureElementDestination.png" alt-text="Screenshot of creating a file destination configuration.":::

Next, in the **Destination settings** dialog box, you can enable and disable individual destinations for the file destination. Use the **Settings** button to control all the destinations for a selected file destination. In the **Destination settings** dialog box, you can control each destination separately by setting the **Enabled** option for it. 

You can create **multiple file destinations** for each output component of the same format. For example, you can use this capability to configure file destinations for a file component that's used to generate an outbound document in Excel format. One destination can be configured to store the original Excel file in the ER jobs archive, and another destination can be configured to simultaneously convert the Excel file to PDF format and send the PDF file by email. Learn more in [Archive](er-destination-type-archive.md), [Email](er-destination-type-email.md), and [Convert](er-output-conversion-to-pdf.md).

:::image type="content" source="./media/ER_Destinations-SampleDestinations.png" alt-text="Screenshot of configuring multiple destinations for a single format element.":::

When you run an ER format, the system always runs all destinations that you configured for components of the format. In addition, the ER destinations functionality lets you configure different sets of destinations for a single ER format. This configuration marks each set as configured for a particular user action. The ER API was [extended](er-apis-app10-0-17.md) so that an action can be provided that the user performs by running an ER format. The action code that is provided is passed to ER destinations. You can run different destinations of an ER format, depending on the action code that is provided. Learn more in [Configure action-dependent ER destinations](er-action-dependent-destinations.md).

## Destination types

The following destinations are currently supported for ER formats. You can disable or enable all types at the same time. In this way, you can either do nothing or send the component to all configured destinations.

- [Email](er-destination-type-email.md)
- [Archive](er-destination-type-archive.md)
- [File](er-destination-type-file.md)
- [Screen](er-destination-type-screen.md)
- [Power BI](er-destination-type-powerbi.md)
- [Print](er-destination-type-print.md)

## Applicability

You can set up destinations only for ER configurations that you import and for the formats that are available on the **Electronic reporting configurations** page.

> [!NOTE]
> Configured destinations are company-specific. If you plan to use an ER format in different companies of the current Finance instance, you must configure destinations for that ER format for each of those companies.

When you configure file destinations for a selected format, you configure them for the whole format.

:::image type="content" source="./media/ER_Destinations-ConfigurationLink.png" alt-text="Screenshot of configuration link interface.":::

At the same time, you might have multiple versions of the format that you import into the current Finance instance. You can view them if you select the **Configuration** link that is offered when you select the **Reference** field.

:::image type="content" source="./media/ER_Destinations-ConfigurationVersions.png" alt-text="Screenshot of configuration versions list.":::

By default, configured destinations are applied only when you run an ER format version that has a status of either **Completed** or **Shared**. However, you sometimes must use configured destinations when you run the draft version of an ER format. For example, you modify a draft version of your format, and you want to use configured destinations to test how the system delivers generated . Follow these steps to apply destinations for an ER format when the draft version is run.

1. Go to **Organization administration** \> **Electronic reporting** \> **Configurations**.
1. On the **Configurations** page, on the Action Pane, on the **Configurations** tab, in the **Advanced settings** group, select **User parameters**.
1. Set the **Use destinations for draft status** option to **Yes**.

:::image type="content" source="./media/ER_Destinations-UserSetting1.png" alt-text="Screenshot of Use destinations for draft status option setting.":::

To use the draft version of an ER format, you must mark the ER format accordingly.

1. Go to **Organization administration** \> **Electronic reporting** \> **Configurations**.
1. On the **Configurations** page, on the Action Pane, on the **Configurations** tab, in the **Advanced settings** group, select **User parameters**.
1. Set the **Run setting** option to **Yes**.

:::image type="content" source="./media/ER_Destinations-UserSetting2.png" alt-text="Screenshot of Run setting option configuration.":::

After you complete this setup, the **Run draft** option is available for ER formats that you modify. Set this option to **Yes** to start to use the draft version of the format when the format is run.

:::image type="content" source="./media/ER_Destinations-FormatSetting.png" alt-text="Screenshot of Run draft option setting.":::

## Security considerations

Two types of privileges and duties are used for ER destinations. One type controls a user's overall ability to maintain the destinations configured for a legal entity (that is, it controls access to the **Electronic reporting destinations** page). The other type controls an application user's ability to override the destination settings that an ER developer or ER functional consultant configures at runtime.

| Role (AOT name)                     | Role name                                  | Duty (AOT name)                     | Duty name                                                        |
|-------------------------------------|--------------------------------------------|-------------------------------------|------------------------------------------------------------------|
| ERDeveloper                         | Electronic reporting developer             | ERFormatDestinationConfigure        | Configure electronic reporting format destination                |
| ERFunctionalConsultant              | Electronic reporting functional consultant | ERFormatDestinationConfigure        | Configure electronic reporting format destination                |
| PaymAccountsPayablePaymentsClerk    | Accounts payable payments clerk            | ERFormatDestinationRuntimeConfigure | Configure electronic reporting format destination during runtime |
| PaymAccountsReceivablePaymentsClerk | Accounts receivable payments clerk         | ERFormatDestinationRuntimeConfigure | Configure electronic reporting format destination during runtime |

> [!NOTE]
> The preceding duties use two privileges. These privileges have the same names as the corresponding duties: **ERFormatDestinationConfigure** and **ERFormatDestinationRuntimeConfigure**.

## Frequently asked questions

### I imported electronic configurations, and I see them on the Electronic reporting configurations page. But why don't I see them on the Electronic reporting destinations page?

Make sure that you select **New** and then select a configuration in the **Reference** field. The **Electronic reporting destinations** page shows only configurations that you configure destinations for.

### Is there any way to define which Microsoft Azure Storage account and Azure Blob storage are used?

No. The default Microsoft Azure Blob storage that is defined and used for the document management system is used.

### What is the purpose of the File destination in the destination settings? What does that setting do?

The **File** destination controls a dialog box of your web browser when you run an ER format in interactive mode. If you enable this destination, or if you don't define a destination for a configuration, an open or save dialog box appears in your web browser after an  file is created.

### Can you give me an example of the formula that refers to a vendor account that I can send email to?

The formula is specific to the ER configuration. For example, if you use the ISO 20022 Credit Transfer configuration, you can use **'$PaymentsForCoveringLetter'.Creditor.Identification.SourceID** or **model.Payments.Creditor.Identification.SourceID** to get an associated vendor account.

### One of my format configurations contains multiple files that are grouped into one folder (for example, Folder1 contains File1, File2, and File3). How do I set up destinations so that Folder1.zip isn't created at all, File1 is sent by email, File2 is sent to SharePoint, and I can open File3 immediately after the configuration runs?

Your format must first be available in the ER configurations. If this prerequisite is met, open the **Electronic reporting destination** page and create a new reference to the configuration. You must then have four file destinations, one for each  component. Create the first file destination, give it a name such as **Folder**, and select a file name that represents a folder in your configuration. Then select **Settings**, and make sure that all the destinations are disabled. For this file destination, the folder isn't created. By default, because of hierarchical dependencies between files and parent folders, the files behave in the same way. In other words, they aren't sent anywhere. To override that default behavior, you must create three more file destinations, one for each file. In the destination settings for each, you must enable the destination that the file should be sent to.

## More information

[Electronic reporting (ER) overview](general-electronic-reporting.md)

[Configure action-dependent ER destinations](er-action-dependent-destinations.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
