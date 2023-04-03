---
# required metadata

title: Manage channels in Invoice capture solution
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

# Manage channels in Invoice capture solution

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

This article describes what a channel is and how to create one in Invoice capture. 

## Definition of channel 

Customers receive supplier invoices from different external sources. To centrally collect the invoices, the concept of a channel was introduced in Invoice capture. Admins can define different channels based on different triggers in various connectors in Power Automate.  

When invoices are sent via pre-defined channels, they can be captured and displayed on **Received files** page. 

## Default channel for file upload: 

In invoice capture, the default channel is used to upload the invoice in Invoice capture. The invoice can be reviewed on the **Received files** page in Invoice capture. 
New channels can be created to replace the default channel on the **System preference** page. 

## Deactivate and activate the channel 

Admin can use the button Activate/Deactivate in the ribbon to decide whether the invoice document should be received from the channel.  
If the channel is assigned as the Channel for file upload in Setup system > System preference and set inactive, the file upload in Received file cannot be working.  
 

## Use managed flow  

This is an important option for Admins to decide how they want to integrate the document receive API. 
Yes: let system generate flow automatically based on the flow setting. 
No: by select this option, user will need to integrate the receive API themselves and bind current channel Id into the API parameter. 


When the toggle “Use managed flow” is set as “Yes” 
The flow setting will be enabled, and it will ask you to select the “Flow template”. By default, the flow template is set to “Microsoft Outlook 365”, which is the most widely used. Meanwhile, it predefines the following templates: 

 - Outlook.com 
 - Microsoft Outlook 365 
 - OneDrive 
 - SharePoint 
 - OneDrive for business 

Additional properties have to be defined to ensure success of the flow generation. 

|Flow template |  Properties|   Meaning|
|---------------|-----------|----------|
|Outlook.com or Microsoft Outlook 365 | Folder |Email folder under root directory, default: Inbox (Subfolder is not supported) |
|SharePoint |Site address |Example: https://contoso.sharepoint.com/sites/sitename |
|           |Library |SharePoint library name| 
|           |Folder|  Select a folder, or leave blank for the whole library |
|OneDrive or OneDrive for business |Folder| Directory name| 

By set using managed flow = Yes and fulfill all necessary fields, when saving the channel, flow will be generated automatically and will be turned to ON if possible. 

If flow is generated successfully, there’s custom control - Manage flow pane introduced which provides simple operations on the flow. 
 - Turn On/Off flow. 
 - Edit: will lead user to the flow editing UI to do fixing or advanced customizations. 
 - View: will lead user to flow overview UI, user can see the running details of flow and other flow related information. 

There’s a ribbon button group which provides the flow lifecycle management: 
 - When there’s no flow associated with current channel: 
      - Generate: only visible, this is useful when the first generation is failed. 
 - When there’s a flow associated with current channel: 
     -   Sync: Sync back parameters when user made some changes in the flow directly. 
     -   Unlink: unlink the associated flow but keep it in the environment. 
     -   Delete: delete the associated flow. 

The flow is generated based on the selected template and prefilled required parameters. But flow owner with advanced flow knowledge could still make change to the flow for more advanced functions. 

Caution: by editing the flow, make sure the file receive node unchanged. 

There’re could be different reasons leading to the situation below: 

Generate flow failed. 
Reason: Generally, the flow will be generated successfully except for system reasons. For example, it may fail due to timeout or lack of license for flow usage. 
Solution: There will be error messages raises with details. And there’s Generate flow button in the ribbon, so user could retry generate for temporary errors or system level fixtures. 

Turn on flow failed. 
Reason: there’re could be multiple reasons when turning on flow. 

As flow connects operations together and different operations require different connections which wrap credentials to different applications. The connection is reusable artifacts, but if the user doesn’t have any connections created yet, the turn on will always fail. 

For different flow templates, it requires value on various parameters. For example, Microsoft 365 Outlook requires to indicate which Folder arrives the email shall trigger the flow. Incorrect parameters may also lead to failure. 

Solution: There will be error messages with a “Fix it” button in the message bar to lead Admins to the flow editing UI to check. If the message is closed, they could still click edit in manage flow pane which will also lead to the flow editing UI. 

### When the toggle “Use managed flow” is set as “No” 

This option should only be used by professional users, the document receive API should be integrated manually, and channelId will need to be filled in the API payload. ChannelId can be found in the URL after it is saved.  

When it is calling the “vis_ExternalDocumentReceiver” API without a valid channelId, the system will treat it as an invalid call. The invoice file cannot be captured and displayed in Manage invoices > Received files. 


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

Channel type decides whether it’s for interactive or silent scenarios. 
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

A sample payload in below, need to stringify before post. 

{ 

    "ChannelId": "xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx", 

    "SendFrom": "xxxx.xxx@contoso.com" 

} 

### Create a new channel using managed flow example 
1. In the navigation panel, go to Setup system > Manage channels. 
2. On the action pane, select New. Give the name, description, keep Use manage flow as Yes and selecting the correct ‘Flow template’. Click the button “Save”. The new channel page will display. 
3. It will take some time to create the flow behind the scenes.  
 - If flow is successful generated and activated, the manage flow will turn on the status toggle.  
 - If flow is generated but not activated, admin can click the Edit button to navigate the flow to do the setup.  

### Security 

AP admin with assigned Environment maker is allowed to create the channels.  

