---
# required metadata

title: Manage channels in the Invoice capture solution
description: This article provides information about how to manage channels in the Invoice capture solution.
author: sunfzam
ms.date: 04/05/2023
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

# Manage channels in the Invoice capture solution

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

This article describes what a channel is and how to create one in Invoice capture. 

## Definition of channel 

Customers receive supplier invoices from different external sources. To collect the invoices in one location, channels are available in Invoice capture. Administrators can define multiple channels based on different triggers in various connectors in Power automate.  

When invoices are sent via predefined channels, they are captured and displayed on **Received files** page. 

## Default channel for file upload

In invoice capture, a default channel is used to upload the invoice in Invoice capture and can be reviewed on the **Received files** page. New channels can be created to replace the default channel on the **System preference** page. 

## Deactivate and activate the channel 

Administrators can use **Activate/Deactivate** to receive the invoice document from the channel. If a channel is assigned as the **Channel for file upload** in the **System preference** page and is **Inactive**, the file upload in the **Received file** page won't work.  
 

## Use managed flow  
Administrators can decide how they want to integrate the document receive API. 
On the XXX, select the **Use managed flow** option:
 - **Yes** - The flow will be automatically generated based on the flow setting
 - **No** -  The user needs to integrate the received API and bind current channel ID into the API parameter 


When the **Use managed flow** is set to **Yes**, the flow setting is enabled. The user will select the **Flow template**. By default, the flow template is set to “Microsoft Outlook 365”. 

The following templates are available: 

 - Outlook.com 
 - Microsoft Outlook 365 
 - OneDrive 
 - SharePoint 
 - OneDrive for business 

The following additional properties need to be defined to generate flows: 

|Flow template |  Properties|   Meaning|
|---------------|-----------|----------|
|Outlook.com or Microsoft Outlook 365 | Folder |Email folder under root directory, default: Inbox (Subfolder is not supported) |
|SharePoint |Site address |Example: https://contoso.sharepoint.com/sites/sitename |
|           |Library |SharePoint library name| 
|           |Folder|  Select a folder, or leave blank for the whole library |
|OneDrive or OneDrive for business |Folder| Directory name| 

If the **Use managed flow** option is set **Yes**, when saving the channel, the flow will be generated automatically and will be turned **On**. 

If flow is generated successfully, a custom control is available. The **Manage flow** pane allows the following operations: 
 - Turn the flow On/Off  
 - **Edit** - allows the user to edit the flow and either customize or fix the flow. 
 - **View** - users can view the running details of flow and other flow related information. 

The flow lifecycle management allows users to update channels. 
 - When there’s no flow associated with current channel: 
      - **Generate** - available when the first channel generation failed. 
 - When there’s a flow associated with current channel: 
     -   **Sync** - Syncs the parameters when users update the flow. 
     -   **Unlink** - Unlink the associated flow and keep it in the environment. 
     -   **Delete** - Delete the associated flow. 

The flow is generated based on the selected template and prefilled required parameters. But a flow owner with advanced flow knowledge can update the flow for more advanced functions. 

There are various errors that can appear: 

**Generate flow failed** - The flow will be generated successfully except for system reasons. It may fail due to timeout or lack of licenses. 
Solution - Error messages will provide details and **Generate flow** will generate temporary errors or the system level fixes. 

**Turn on flow failed** - There are potentially multiple reasons when turning on a flow. 
As flow connects operations together and different operations require different connections and credentials to different applications. The connection is reusable artifacts, but if the user doesn’t have any connections created yet, when the flow is turned on, it will fail. 

For different flow templates, it requires various parameters. For example, Microsoft 365 Outlook requires to select the email folder that triggers the flow. Incorrect parameters may also lead to failure.
Solution - Error messages display **Fix it** in the message bar to assist administrators to the flow editing UI. If the message is closed, click **Edit** in the **Manage flow** pane which opens the flow editing UI. 

### Use managed flow option  

The **Use managed flow** option on the **Channel** page should only be used by professional users, the document receive API should be integrated manually. The channel ID will need to be filled in the API payload. Channel ID can be found in the URL after it is saved.  

When calling the “vis_ExternalDocumentReceiver” API without a valid channel ID, the system will treat it as an invalid call. The invoice file can't be captured and will be displayed in the **Received files** page. 


### Document Receiver API 

Document receiver API vis_ExternalDocumentReceiver is a Dataverse unbound custom API. 

Input parameters: 

|Parameter name  |   Type   |  Is required|    Description| 
|----------------|----------|-------------|---------------|
|vis_ExternalDocumentReceiver_FileSetId_In | string |        |Optional| 
|vis_ExternalDocumentReceiver_FielName_In |string | X |File name with extension| 
|vis_ExternalDocumentReceiver_FileContent_In |string |X   |Base64 encodeded file| 
|vis_ExternalDocumentReceiver_ChannelType_In |string |  X   |One of [Direct, Email, API, FileSystem] |
|vis_ExternalDocumentReceiver_ChannelInfo_In |string | X   |Stringified object, see Channel Info |

Channel type decides if it’s interactive or silent scenarios. 
 - Interactive: Direct 
 - Silence: Email, API, FileSystem 

Output parameters 

|Parameter name |type|Is required   |Description| 
|-------------|------|-----------|--------------|
|vis_ExternalDocumentReceiver_Data_Out |string |    |Succeeded file Id in Received files (vis_externaldocumentinfo) |

Channel Info 

|Parameter name |type |Is required |Description| 
|-------------|------|-----------|--------------|
|ChannelId |string |X  |The identifier of the channel that needs to be bound. |
|SendFrom |string|     |Additional information to track sender. |

A sample payload is below: 

{ "ChannelId": "xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx", 
    "SendFrom": "xxxx.xxx@contoso.com" } 

### Create a new channel using managed flow example 
1. In the navigation panel, go **Manage channels**. 
2. On the action pane, select **New**. 
3. Fill in the **Name**, **Description**, **Use manage flow** is **Yes** and select a **low template**. 
4. Click **Save**. The new channel page will display. 
5. It will take some time to create the flownes.  
 - If the flow is successfullly generated and activated, the **Manage flow** status will be **On**.  
 - If the flow is generated but not activated, administrators can click **Edit** to setup the flow.  


