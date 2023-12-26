---
# required metadata

title: Invoice capture solution advanced settings
description: This article provides information about advanced settings in the Invoice capture solution.
author: sunfzam
ms.date: 09/25/2022
ms.topic: overview
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: VendorInvoiceWorkspace, VendInvoiceInfoListPage
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
ms.collection: get-started
ms.assetid: 0ec4dbc0-2eeb-423b-8592-4b5d37e559d3
ms.search.region: Global
# ms.search.industry: 
ms.author: zezhangzhao
ms.search.validFrom: 2022-09-28
ms.dyn365.ops.version: 

---

# Invoice capture solution advanced settings

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

This article provides information about advanced settings in the Invoice capture solution.

## Create additional connections for channels

You must create connections to email or file storage to enable monitoring of incoming invoices from different channels. You must register connections at the beginning to grant access for automated flows that are used in the solution.

The following connection types are used to import invoices:

- Office 365 Outlook
- Outlook.com
- OneDrive
- SharePoint

The channel for invoice importing will use the connections in further configuration steps. Before users can create a channel of a specific connection, the **Administrator** security role must be granted to them, and they must create connections.

To create a connection to Microsoft Dataverse, follow these steps.

1. Go to **Admin system \> Default solution**.
2. Select **New**, and then select **Connection Reference**.
3. In the **Display name** field, enter a name.
4. Select **Microsoft Dataverse** as the connector.
5. If you're setting up the connection for the first time, select **New connection**.
6. In the dialog box that appears, create a Dataverse connection, and then select **Create**.
7. Enter the Dataverse account and password.
8. After validation is passed, go to the connection page, select **Refresh**, select the account, and then select **Create**.

To create an email or file storage connection, follow these steps.

1. On the **Connection creation** page, in the **Connection type** field, select **Office 365 Outlook**.
2. For an email connection, you can select **Outlook.com** or **Office 365 Outlook** as the connector. For a file storage connection, you can select either **OneDrive** or **SharePoint**.

To review existing connections, go to **Default solution \> Objects \> Connection References**. The user who creates channels should have at least one Dataverse connection in addition to specific email or file storage connections. The creator of the new channel should be the owner of the connection.
