---
# required metadata

title: Configure the Invoice capture solution
description: This article explains how to configure the Invoice capture solution.
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
ms.custom: ["13971", "intro-internal"]
ms.assetid: 0ec4dbc0-2eeb-423b-8592-4b5d37e559d3
ms.search.region: Global
# ms.search.industry: 
ms.author: zezhangzhao
ms.search.validFrom: 2022-09-28
ms.dyn365.ops.version: 

---

# Configure the Invoice capture solution

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

After the Invoice capture solution is installed, you must configure the environment. The process consists of the following basic steps.

1. **Required:** Synchronize the legal entities from Microsoft Dynamics 365 Finance. This step is used to set up the organization structure in Microsoft Power Platform.
2. **Required:** Configure the channels for the import of invoice images. The solution supports the following channels:

    - Office 365 Outlook (default)
    - Outlook.com
    - OneDrive
    - SharePoint

3. **Optional:** Define additional configuration groups for the optical character recognition (OCR) service.
4. **Optional:** Define mapping rules for the legal entity, vendor account, item, and procurement type.

This article is focused on the two required steps of the process. For more information about configuration groups, see [Invoice capture solution configuration groups](invoice-capture-config-group.md). For more information about mapping rules, see [Invoice capture solution mapping rules](invoice-capture-mapping-rules.md).

## Manage legal entities

Finance defines legal entities as organizations that are identified through registration with legal authorities. Business activities are performed and recorded in separate legal entities. In Microsoft Power Platform, business units, security roles, and users are linked together in a manner that conforms to the role-based security model.

Business units are used together with security roles to control data access. Users see only the information that they require to do their jobs. The Invoice capture solution provides a configuration space where you can load basic information from existing legal entities in Finance and manage those entities that are created manually. The legal entities are used on vendor invoices and in security control.

When a legal entity is created and shown in the list view, a default business unit that has the same name is automatically created. The team is granted the **AP clerk** security role. When legal entities are imported, basic master data from Finance is imported. The nonexistent items will be identified by legal entity and will add them to the Invoice capture solution. The default configuration group is assigned to new legal entities.

### Sync legal entities

You can't create legal entities directly. However, you can sync legal entities from Finance. To sync legal entities, follow these steps.

1. Go to **Setup \> System setup \> Manage legal entities**.
2. Select **Sync legal entities**, and then select **OK** in the confirmation dialog box.

After synchronization is completed, the number of new legal entities is shown. The new legal entities are shown in the list view. The default configuration group is assigned to the new legal entities.

## Configure invoice import channels

Vendors send invoices from different channels (email, file workspace, or invoice portal) via different formats (paper or image). The Invoice capture solution can handle different channels and formats. The following types are supported:

- Office 365 Outlook
- Outlook.com
- SharePoint
- OneDrive

When a channel is created for a specific account, an automated flow that has a predefined template is constructed to monitor the incoming emails or files in the inbox or space. Any file that has a valid invoice can be recognized and sent to the invoice area to await processing by the Accounts payable (AP) clerk. The attachment should be in PDF or image format. Invoices can be loaded into the Invoice capture solution according to the channel configuration.

### Create a channel

If you've imported the additional solution package (Dynamics 365 Invoice capture – Installation Tools), the default connection for Office 365 Outlook is ready to use. If you want to create more connections for different email accounts or other channel types, see [Create additional connections for channels](invoice-capture-advanced-settings.md#create-additional-connections-for-channels).

To create a channel, follow these steps.

1. Go to **Setup \> System setup \> Config channels**.
2. Select **New**.
3. Set the following fields:

    - Channel name
    - Description
    - Type
    - Connection

Only emails or files that match the following criteria can be imported into the solution.

| Type               | Configuration  | More information |
|--------------------|----------------|------------------|
| Office 365 Outlook | Folder         | The email folder must be under the root directory. By default, the Inbox folder is used. A subfolder isn't supported. |
|                    | Subject filter | (Optional) A substring that should be included in the subject. |
|                    | From           | (Optional) The email address of the sender or senders. If you specify multiple addresses, use a semicolon (;) as the separator. |
| SharePoint         | Site address   | The URL of the site address. |
|                    | Folder         | The folder in the site address. |

### Activate the channel

When a flow is saved, fields show the status of the channel and the time when it was created. Initially, the **Status** field is set to **Inactive**. The **Status reason** field indicates that the channel has been initialized and is ready to be activated.

To activate the channel, select **Activate**. The **Status** and **Status reason** fields are updated.

If a channel isn't required, you can deactivate it. To deactivate a channel, select **Deactivate**. The **Status** and **Status reason** fields are updated.

### Manage flows in flow management

You can view a channel on the **Config channels** page or in flow management.

To view more details, go to **Admin system \> Default solution \> Cloud flows**, and select the target flow. The details that are shown include linked connections, owners, and run histories.

To sync the status, select **Check** to confirm that the status of the channel matches the status of the flow.

Some cases of exception handling are shown in the **Status reason** field:

- **Missing Dataverse connection** – The current user hasn't created at least one **Microsoft Dataverse** connection reference.
- **Not found** – The flow that is linked to the channel has been deleted in flow management. The channel should be saved again to create a new channel.
- **Deactivated in flow management** – The flow has been deactivated in flow management, and the status of the channel differs from the status of the flow.
- **Activated in flow management** – The flow has been activated in flow management, and the status of the channel differs from the status of the flow.
- **An unexpected error occurred** – The user must confirm that the site is a "Communication site," and that the folder is "Document library."
