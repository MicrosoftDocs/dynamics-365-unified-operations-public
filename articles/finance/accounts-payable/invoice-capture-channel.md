---
title: Manage channels in the Invoice capture solution
description: Learn about how to manage channels in the Invoice capture solution, including an outlining defining channels and documents reeiving APIs.
author: sunfzam
ms.author: zezhangzhao
ms.topic: overview
ms.date: 07/28/2026
ms.reviewer: twheeloc
ms.collection: get-started
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2022-09-28
ms.search.form: VendorInvoiceWorkspace, VendInvoiceInfoListPage
ms.dyn365.ops.version: 
ms.assetid: 0ec4dbc0-2eeb-423b-8592-4b5d37e559d3
---

# Manage channels in the Invoice capture solution

[!include [banner](../includes/banner.md)]
[!INCLUDE [lcs-freeze-banner](../../includes/lcs-freeze-banner.md)]

This article explains what a channel is and provides information about how to manage channels in the Invoice capture solution.

## Definition of channel

Customers receive supplier invoices from different external sources. The Invoice capture solution provides channels to collect the invoices in one location. Administrators can define multiple channels, based on different triggers in various connectors in Microsoft Power Automate. When invoices are sent through predefined channels, they appear on the **Received files** page.

## Default channel for file upload

Use the **Default** channel to upload invoices into the Invoice capture solution. You can view the invoice on the **Received files** list page. You can create a new channel to replace the **Default** channel on the **System preference** page.

## What is the Document receive API?

The Document receive API, **vis\_ExternalDocumentReceive**, is a Dataverse unbound custom API. It's used to receive the invoice documents. Administrators follow the API standards and provide the correct input parameters to confirm that the API is correctly called.

### Input parameters

| Parameter name | Type | Required | Description |
|----------------|------|----------|-------------|
| ChannelId | string | Yes | Channel id  |
| FileName | string | Yes | A file name with extension. |
| FileContent | string | Yes | A Base64-encoded file. |
| FileSetId | string | No | An optional parameter. |
| AdditionalInfo | string | Yes | A stringified object. For more information, see the [Channel information](#channel-information) section. |

Enter a valid channel ID. If you call the Document receive API without a valid channel ID, the request is ignored, and the invoice document isn't captured or available on the **Received files** list page.

#### Channel information

| Parameter name | Type | Required | Description |
|----------------|------|----------|-------------|
| ChannelId | string | Yes | The identifier of the channel that must be bound. |
| SendFrom | string | No | Additional information to track the sender. |

Here's an example of a payload.

```
{ "ChannelId": "xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx", 
"SendFrom": "xxxx.xxx@contoso.com" }
```

### Output parameters

| Parameter name | Type | Required | Description |
|----------------|------|----------|-------------|
| Data | string | No | The file ID of a successful file on the **Received files** page (**vis\_externaldocumentinfo**). |

### Generate the channel with a flow

Administrators decide how to integrate the Document receive API. On the **Channel** page, you can enable the **Use managed flow** parameter.

When you set the **Use managed flow** parameter to **Yes**, you enable the flow setting. You can then select a flow template. A flow template helps build the flow by providing the necessary parameters. The following templates are available:

- Outlook.com
- Microsoft Outlook 365
- Microsoft Outlook 365 shared mailbox
- SharePoint
- OneDrive
- OneDrive for business

By default, the flow template is set to **Microsoft Outlook 365**.

The following table describes the additional properties that you must define to generate flows.

| Flow template | Property | Description |
|---------------|----------|-------------|
| **Outlook.com** or **Microsoft Outlook 365** | Folder | The email folder under the root directory. The default folder is **Inbox**. (Subfolders aren't supported.) |
| **Microsoft Outlook 365 shared mailbox** | Mailbox address and folder | The mailbox address is the shared mailbox address, and the default folder is **Inbox**. |
| **SharePoint** | Site address | The address of the SharePoint site, such as `https://contoso.sharepoint.com/sites/sitename`. |
| | Library | The name of the SharePoint library. |
| | Folder | Select a folder, or leave the property blank to use the whole library. |
| **OneDrive** or **OneDrive for business** | Folder | The directory name. |

When you save the channel and set the **Use managed flow** option to **Yes**, the system automatically generates the flow and shows the flow details pane. This pane allows for the following operations:

- Turn the flow on and off.
- Edit the flow, and either customize the flow or fix it.
- View the running details of the flow and other flow-related information.

The **Manage flow** action helps you manage the flow lifecycle:

- If no flow is associated with the current channel:

  - **Generate** – This option is available if the first attempt to generate the channel failed.

- If a flow is associated with the current channel:

  - **Sync** – Sync the parameters when users update the flow.
  - **Unlink** – Unlink the associated flow, and keep it in the environment.
  - **Delete** – Delete the associated flow.

The flow is generated based on the selected template and preset required parameters. However, a flow owner who has advanced flow knowledge can update the flow for more advanced functions.

### Generate the channel without a flow

If you set the **Use managed flow** option to **No**, the Document receive API is called without using a flow template. Only administrators should use this approach. You must specify the channel ID in the API payload. You can find the channel ID in the URL after you save it.

## Create a new channel

To create a new channel, administrators can follow these steps:

1. In the navigation pane, select **Manage channels**.
1. On the Action Pane, select **New**.
1. Enter a name and description, set the **Use managed flow** option to **Yes**, and select a flow template.
1. Select **Save**. The new channel page appears.

    Creation of the flows takes some time.

    - If the flow is successfully generated and activated, the **Manage flow** status is **On**.
    - If the flow is generated but isn't activated, an administrator can select **Edit** to set up the flow.

## Deactivate and activate a channel

Administrators can use **Activate**/**Deactivate** to specify whether the invoice document should be received from the channel.

If you assign the channel as the **Channel for file upload** at **Setup system \> System preference**, but deactivate it, file upload on the **Received file** page doesn't work.

## Legal entity or group assignment

Administrators can create distinct channels for different levels in the company organization.

1. In the Power Platform admin center, go to **Environment**, and select the desired environment.
1. Go to **Business units** to create new business units and assign existing ones as child nodes. These business units can act as group levels for multiple legal entities. Use security roles to manage data access. This setup ensures that only users with the appropriate privileges can access the received invoice files and their corresponding captured invoices when the business unit is assigned to the channel.

When you assign a legal entity to a channel, the corresponding business unit automatically sets the access level when an invoice file is received through that channel. During the invoice capture process, the legal entity is automatically assigned. Therefore, no additional derivation logic is required.

## Create a new channel by using an unmanaged flow

To create a channel by using an unmanaged flow in Invoice capture, follow these steps:

1. Select **New** to create a channel.
1. Enter a channel name, and set the **Use Manage channel** option to **No**.
1. Save your changes, and record the **channel id** value from the URL in the browser's address bar.
1. Sign in to Power Apps, and select **Flow**.
1. Select **New flow**, and then select **Automated cloud flow** in the dropdown list.
1. Enter a name for the flow, and select **When a new email arrives in a shared mailbox** as the trigger.
1. Select **Create** to create the automated flow.
1. In the **Original MailBox Address** field, enter the address of the shared mailbox.
1. Set the **Only with Attachments** and **Include Attachments** options to **Yes**.
1. Add other criteria to meet your business requirements.
1. Select the plus sign (**\+**) to insert a new step.
1. Select **Add an action** \> **Microsoft Dataverse**, and then select **Perform an unbound action**.
1. Select the ellipsis (**&hellip;**), and then select **Rename** to enter a new name for the step.
1. In the **Action name** field, select **vis\_ExternalDocumentReceiver**.
1. Update **channel id** to **ChannelId**.
1. In the **FileName** field, select **Attachments name**.
1. In the **FileContent** field, select **Attachment content**.
1. Select the ellipsis (**&hellip;**), and then select **Peek code**.
1. Copy the value for **item/FileContent**. This value looks like **@items('xxx')?\['contentBytes'\]**. Wrap the value in a string function so that it looks like **string(items('xxx')?\['contentBytes'\])**. Then paste the final value into the **Attachment content** field.
1. In the **AdditionalInfo** field, enter the following value:

    additionalInfo:{<br>
    &nbsp; &nbsp; "SendFrom": @\{triggerOutputs()?\['body/from'\]\}<br>
    \}

> [!NOTE]
> If you have Invoice capture solution version 1.1.0.10 or later, you can select **Microsoft Outlook 365 Shared Mailbox** as the flow template.
