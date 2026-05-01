---
title: Archive ER destination type
description: Learn about how to configure an archive destination for each FOLDER or FILE component of an Electronic reporting (ER) format.
author: kfend
ms.author: filatovm
ms.topic: article
ms.date: 04/02/2026
ms.reviewer: johnmichalak
audience: Developer, IT Pro
ms.search.region: Global
ms.search.validFrom: 2016-05-31
ms.search.form: DocuType, ERSolutionTable, ERFormatDestinationTable
ms.dyn365.ops.version: AX 7.0.1
ms.assetid: 
---

# Archive ER destination type

[!include [banner](../includes/banner.md)]

You can configure an archive destination for each **Folder** or **File** component of an Electronic reporting (ER) format configured to generate outbound documents. Based on the destination setting, the system stores a generated document as an attachment of a record in the ER jobs list. To view the results, go to **Organization administration** > **Electronic reporting** > **Electronic reporting jobs**.

Use this option to send the generated document to a Microsoft SharePoint folder or Microsoft Azure Storage. Set **Enabled** to **Yes** to send output to a destination that the selected document type defines. You can only select document types where the group is set to **File**. You define document [types](../../fin-ops/organization-administration/configure-document-management.md#configure-document-types) at **Organization administration** > **Document management** > **Document types**. The configuration for ER destinations is the same as the configuration for the document management system.

:::image type="content" source="./media/ER_Destinations-SharePointDocuType.png" alt-text="Screenshot of the Document types page." lightbox="./media/ER_Destinations-SharePointDocuType.png":::

The location determines where the file is saved. After you enable the **Archive** destination, the results can be saved in the Job archive. You can view the results at **Organization administration** > **Electronic reporting** > **Electronic reporting archived jobs**.

> [!NOTE]
> Select a document type for the Job archive by navigqting to **Organization administration** > **Workspaces** > **Electronic reporting** > **Electronic reporting parameters**. For more information, see [Configure the Electronic reporting (ER) framework](electronic-reporting-er-configure-parameters.md#prerequisites-for-er-setup).

## SharePoint

You can save a file in a designated SharePoint folder. To define the default SharePoint server, go to **Organization administration** > **Document management** > **Document management parameters**. On the **SharePoint** tab, configure the SharePoint folder. Then, you can select it as the folder where the ER output is saved. You must select the **SharePoint** location in this document type.

:::image type="content" source="./media/ER_Destinations-SharePointDocuTypeLocation.png" alt-text="Screenshot of selecting a SharePoint folder." lightbox="./media/ER_Destinations-SharePointDocuTypeLocation.png":::

## Azure Storage

When the document type location is set to **Azure storage**, you can save a file to Azure Storage.

> [!NOTE] 
> Unlike the Data management framework, which applies a seven-day retention policy for documents that must be processed, the ER framework permanently stores files in Azure Blob storage. For more information, see [API for getting message status](../data-entities/recurring-integrations.md#api-for-getting-message-status) and [Status check API](../data-entities/data-management-api.md#status-check-api). The ER-related files are stored in Azure Blob storage as attachments of application table records for as long as necessary. A single file is deleted from Azure Blob storage along with the application table record that this file was attached to.

## Additional resources

- [Electronic reporting (ER) overview](general-electronic-reporting.md)
- [Electronic reporting (ER) destinations](electronic-reporting-destinations.md)
- [Configure document management](../../fin-ops/organization-administration/configure-document-management.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
