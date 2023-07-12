---
# required metadata

title: Manage channels in the Invoice capture solution
description: This article provides information about how to manage channels in the Invoice capture solution.
author: sunfzam
ms.date: 07/12/2023
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

# Manage channels in the Invoice capture solution

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

This article explains what a channel is and provides information about how to manage channels in the Invoice capture solution.

## Definition of channel

Customers receive supplier invoices from different external sources. Channels are available in Invoice capture to collect the invoices in one location. Administrators can define multiple channels, based on different triggers in various connectors in Microsoft Power Automate. When invoices are sent via predefined channels, they're captured and appear on the **Received files** page.

## Default channel for file upload

A **Default** channel is used to upload invoices into Invoice capture. The invoice can then be viewed on the **Received files** list page. A new channel can be created to replace the **Default** channel on the **System preference** page.

## What is the Document receive API?

The Document receive API, **vis\_ExternalDocumentReceive**, is a Dataverse unbound custom API. It's used to receive the invoice documents. Administrators follow the API standards and provide the correct input parameters to confirm that the API is correctly called.

The Document receive API must be integrated with a valid channel ID. If it's called without a valid channel ID, the call is invalid. In this case, the invoice document can't be captured and doesn't appear on the **Received files** list page.

### Input parameters

| Parameter name | Type | Required | Description |
|----------------|------|----------|-------------|
| ChannelId | string | Yes | Channel id  |
| FileName | string | Yes | A file name with extension. |
| FileContent | string | Yes | A Base64-encoded file. |
| FileSetId | string | No | An optional parameter. |
| AdditionalInfo | string | Yes | A stringified object. For more information, see the [Channel information](#channel-information) section. |

### Output parameters

| Parameter name | Type | Required | Description |
|----------------|------|----------|-------------|
| Data | string | No | The file ID of a successful file on the **Received files** page (**vis\_externaldocumentinfo**). |

### Channel information

| Parameter name | Type | Required | Description |
|----------------|------|----------|-------------|
| ChannelType | string | Yes | The channel type can be Direct, Email, API, or FileSystem. |
| SendFrom | string | No | Additional information to track the sender. |

The channel type determines whether the scenario is interactive or silent. 

| Channel type | Scenario |
|--------------|----------|
| Direct | Interactive  |
| Email | Silent |
| API | Silent |
| FileSystem | Silent |

## Channel with/without a flow template 

Administrators can decide how they want to integrate the Document receive API. On the **Channel** page, set the **Use managed flow** option to one of the following values:

- **Yes** – The flow is automatically generated based on the flow setting.
- **No** – The user must integrate the received API and bind the current channel ID to the API parameter.

#### With a flow template

If the **Use managed flow** option is set to **Yes**, the flow setting is enabled, and the user selects a flow template. The following templates are available:

- Outlook.com
- Microsoft Outlook 365
- SharePoint
- OneDrive
- OneDrive for business

By default, the flow template is set to **Microsoft Outlook 365**.

The following table describes the additional properties that the user must define to generate flows.

| Flow template | Property | Description |
|---------------|----------|-------------|
| **Outlook.com** or **Microsoft Outlook 365** | Folder | The email folder under the root directory. The default folder is **Inbox**. (Subfolders aren't supported.) |
| **SharePoint** | Site address | The address of the SharePoint site, such as `https://contoso.sharepoint.com/sites/sitename`. |
| | Library | The name of the SharePoint library. |
| | Folder | Select a folder, or leave the property blank to use the whole library. |
| **OneDrive** or **OneDrive for business** | Folder | The directory name. |

When the channel is saved, if the **Use managed flow** option is set **Yes**, the flow is automatically generated, and the flow details pane is shown. This pane allows for the following operations:

- Turn the flow on and off.
- Edit the flow, and either customize the flow or fix it.
- View the running details of the flow and other flow-related information.

Flow lifecycle management lets users update channels.

- If no flow is associated with the current channel:

    - **Generate** – This option is available if the first attempt to generate the channel failed.

- If a flow is associated with the current channel:

    - **Sync** – Sync the parameters when users update the flow.
    - **Unlink** – Unlink the associated flow, and keep it in the environment.
    - **Delete** – Delete the associated flow.

The flow is generated based on the selected template and preset required parameters. However, a flow owner who has advanced flow knowledge can update the flow for more advanced functions.

Various errors can appear:

- "Generate flow failed."

    **Cause:** The flow would have been successfully generated. However, generation failed because of a time-out, a lack of licenses, or other system reasons.

    **Solution:** Error messages provide details, and **Generate flow** generates temporary errors or the system-level fixes.

- "Turn on flow failed."

    **Cause:** There are multiple reasons why a flow might fail when it's turned on:

    - A flow connects operations together, and different operations require different connections and credentials to different applications. A connection is a reusable artifact, but if the user hasn't yet created any connections, the flow will fail when it's turned on.
    - Different parameters are required for different flow templates. For example, the **Microsoft 365 Outlook** template requires that the user select the email folder that triggers the flow. Incorrect parameters can cause the flow to fail when it's turned on.

    **Solution:** To help administrators access the flow editing UI, the message bar that shows the error message includes a **Fix it** button. If the message has already been closed, select **Edit** in the **Manage flow** pane to open the flow editing UI.

### Without a flow template

If the **Use managed flow** option is set **No**, the Document receive API is called without using a flow template. We recommend that only administrators use this approach. The channel ID must be specified in the API payload. The channel ID can be found in the URL after it's saved.

## Create a new channel by using managed flow

1. In the navigation pane, select **Manage channels**.
2. On the Action Pane, select **New**.
3. Enter a name and description, set the **Use managed flow** option to **Yes**, and select a flow template.
4. Select **Save**. The new channel page appears.

    Creation of the flows will take some time.

    - If the flow is successfully generated and activated, the **Manage flow** status will be **On**.
    - If the flow is generated but isn't activated, an administrator can select **Edit** to set up the flow.

## Create a new channel by using unmanaged flow
A shared mailbox can be used by a group of people, like a support team, to receive and send email from the same email address. Select a shared mailbox to add or remove members, set up automatic replies, manage aliases, and more. 

In invoice capture, follow theese steps to create a channel that will use a shared mailbox to receive an email from the supplier:
1.	Create a channel by clicking the **+ New** button. 
2.	Enter a channel name. Set the **"Use Manage channel"** field to **No**.
3.	Save and record the **channel id** from the browser url.
4.	Log into Power Apps and select **Flow**.
5.	Click **+ New flow**. Select **Automated cloud flow** from the dropdown list.
6.	Enter a name for the flow. Select the trigger **When a new email arrives in a shared mailbox**. 
7.	Click **Create** to create the power automated flow
8.	Enter the shared mailbox address in **Original MailBox Address**.
9.	Set **Only with Attachments** and **Include Attachments** fields to **Yes**. 
10.	Add additional criterias to meet business requirements.
11.	Click **+** to insert a new step.
12.	Select **Add an action > Microsoft Dataverse**. Select **Perfom an unbound action**.
13.	Click **...** and select **Rename** to enter a new name for the step.
14.	In **Action name**, select **vis_ExternalDocumentReceiver**.
15.	Update **channel id** to **ChannelId**.
16.	In the **FileName** field, select **Attachments name**.
17.	In the **FileContent** field, select **Attachment content**.
18.	Select **... > Peek code**. Copy the value for **item/FileContent**. This looks like **@items('xxx')?['contentBytes']**. Wrap with string function **string(items('xxx')?['contentBytes'])** and paste the final value into the **Attachment content** field.
19.	Fill **AdditionalInfo** with the following: 

   	additionalInfo:{
   	    "SendFrom": @{triggerOutputs()?['body/from']}
   	}


## Deactivate and activate the channel

Administrators can use the **Activate**/**Deactivate** button to specify whether the invoice document should be received from the channel. 

If the channel is assigned as the **Channel for file upload** at **Setup system \> System preference**, but it's deactivated, file upload on the **Received file** page doesn't work.
