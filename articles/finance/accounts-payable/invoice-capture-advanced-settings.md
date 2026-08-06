---
title: Invoice capture solution advanced settings
description: Learn about advanced settings in the Invoice capture solution, including an outline on creating additional connections for channels.
author: sunfzam
ms.author: zezhangzhao
ms.topic: overview
ms.date: 08/03/2026
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

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

This article provides information about advanced settings in the Invoice capture solution.

## Create additional connections for channels

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
