---
# required metadata

title: Archive ER destination type
description: This topic provides information about how to configure an archive destination for each FOLDER or FILE component of an Electronic reporting (ER) format that is configured to generate outbound documents.
author: NickSelin
manager: AnnBe
ms.date: 01/27/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

ms.search.form: DocuType, ERSolutionTable, ERFormatDestinationTable
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 97423
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: nselin
ms.search.validFrom: 2016-05-31
ms.dyn365.ops.version: AX 7.0.1

---

# <a name="ArchiveDestinationType">Archive destination</a>

[!include [banner](../includes/banner.md)]

You can configure an archive destination for each FOLDER or FILE component of an Electronic reporting (ER) format that is configured to generate outbound documents. Based on the destination setting, a generated document is stored as an attachment of a record of the ER jobs list.

You can use this option to send the generated document to a Microsoft SharePoint folder or Microsoft Azure Storage. Set **Enabled** to **Yes** to send output to a destination that is defined by the selected document type. Only document types where the group is set to **File** are available for selection. You define document [types](https://docs.microsoft.com/dynamics365/fin-ops-core/fin-ops/organization-administration/configure-document-management#configure-document-types) at **Organization administration** \> **Document management** \> **Document types**. The configuration for ER destinations is the same as the configuration for the document management system.

[![Document types page](./media/ER_Destinations-SharePointDocuType.png)](./media/ER_Destinations-SharePointDocuType.png)

The location determines where the file is saved. After the **Archive** destination is enabled, the results can be saved in the Job archive. You can view the results at **Organization administration** \> **Electronic reporting** \> **Electronic reporting archived jobs**.

> [!NOTE]
> Select a document type for the Job archive by navigating to **Organization administration** \> **Workspaces** \> **Electronic reporting** \> **Electronic reporting parameters**. For more information, [Configure the Electronic reporting (ER) framework](electronic-reporting-er-configure-parameters.md#prerequisites-for-er-setup).

## SharePoint

You can save a file in a designated SharePoint folder. To define the default SharePoint server, go to **Organization administration** \> **Document management** \> **Document management parameters**. On the **SharePoint** tab, configure the SharePoint folder. Then, you can select it as the folder where the ER output will be saved. The **SharePoint** location must be selected in this document type.

[![Selecting a SharePoint folder](./media/ER_Destinations-SharePointDocuTypeLocation.png)](./media/ER_Destinations-SharePointDocuTypeLocation.png)

## Azure Storage

When the document type location is set to **Azure storage**, you can save a file to Azure Storage.

## Additional resources

- [Electronic reporting (ER) overview](general-electronic-reporting.md)
- [Electronic reporting (ER) destinations](electronic-reporting-destinations.md)
- [Configure document management](../../fin-ops/organization-administration/configure-document-management.md)
