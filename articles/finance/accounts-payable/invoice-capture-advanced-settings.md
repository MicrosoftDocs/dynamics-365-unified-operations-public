---
title: Invoice capture solution advanced settings
description: Learn about advanced settings in the Invoice capture solution, including an outline on creating additional connections for channels.
author: NishantNalawade
ms.author: Nnalawade
ms.topic: overview
ms.date: 09/30/2026
ms.reviewer: twheeloc
ms.collection: get-started
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2022-09-28
ms.search.form: VendorInvoiceWorkspace, VendInvoiceInfoListPage
ms.dyn365.ops.version: 
ms.assetid: 0ec4dbc0-2eeb-423b-8592-4b5d37e559d3
---

# Invoice capture solution advanced settings

[!INCLUDE [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

This article provides information about advanced settings in the Invoice capture solution.

## Create extra connections for channels

Create connections to email or file storage to monitor incoming invoices from different channels. Register connections at the beginning to grant access for automated flows that the solution uses.

Use the following connection types to import invoices:

- Microsoft 365 Outlook
- Outlook.com
- OneDrive
- SharePoint

The channel for invoice importing uses the connections in further configuration steps. Before users can create a channel of a specific connection, grant them the **Administrator** security role, and they must create connections.

To create a connection to Microsoft Dataverse, follow these steps:

1. Go to **Admin system \> Default solution**.
1. Select **New**, and then select **Connection Reference**.
1. In the **Display name** field, enter a name.
1. Select **Microsoft Dataverse** as the connector.
1. If you're setting up the connection for the first time, select **New connection**.
1. In the dialog box that appears, create a Dataverse connection, and then select **Create**.
1. Enter the Dataverse account and password.
1. After validation passes, go to the connection page, select **Refresh**, select the account, and then select **Create**.

To create an email or file storage connection, follow these steps:

1. On the **Connection creation** page, in the **Connection type** field, select **Microsoft 365 Outlook**.
1. For an email connection, select **Outlook.com** or **Microsoft 365 Outlook** as the connector. For a file storage connection, select either **OneDrive** or **SharePoint**.

To review existing connections, go to **Default solution \> Objects \> Connection References**. The user who creates channels should have at least one Dataverse connection in addition to specific email or file storage connections. The creator of the new channel should be the owner of the connection.

## Manage configuration groups

Configuration groups define how invoices are processed and displayed for a set of legal entities or vendors. They control which invoice types are supported, which fields are shown, and what confidence score thresholds trigger review. The installation of Invoice capture creates a default configuration group.

### Configuration group settings

Each configuration group includes the following settings:

- **Supported invoice types** – Select at least one type of invoice that this group handles: **Purchase order**, **Non-purchase order**, or **Cost**. 
- **Confidence score error threshold** – The minimum confidence score percentage required to pass without an error. Fields that the AI model recognizes with a confidence score below this value are flagged with an error status and must be corrected before the invoice can be transferred. The default value is **60**.
- **Confidence score warning threshold** – Fields recognized with a confidence score below this value but above the error threshold are flagged with a warning status. The default value is **90**.
- **Review type** – Controls which flagged fields require manual review before the invoice can be transferred. Select **Error** to require review only for error-level fields, or **Warning** to require review for both warning-level and error-level fields. The default value is **Error**.

### Create a configuration group

To create a configuration group, follow these steps:

1. Go to **Setup** > **Configuration group**.
1. Select **New**.
1. Enter a name for the configuration group.
1. Configure the invoice types, confidence score thresholds, and review type.
1. Select **Save**.

When you create a configuration group, the field configuration is copied from the default configuration group. You can then add, remove, or modify fields to match the requirements of the intended legal entities or vendors.

### Copy a configuration group

To copy an existing configuration group, follow these steps:

1. Go to **Setup** > **Configuration group**.
1. Select the configuration group to copy.
1. Select **Copy**.
1. Enter a name for the new configuration group, and then select **Confirm**.

The copied group contains the same field configuration as the source group and you can modify it independently.

> [!NOTE]
> You can't delete the default configuration group. The system uses this group as the fallback when you don't assign a configuration group at the legal entity or vendor account level.
