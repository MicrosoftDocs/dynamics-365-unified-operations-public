---
# required metadata

title: Configure the Invoice capture solution 
description: This article provides information about configuring the Invoice capture solution. 
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

# Configure the Invoice capture service

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

After the Invoice capture service is installed, there is some configuration in the environment: 
1. [Mandatory] Synchronize the legal entities from the Dynamics 365 Finance environment. This configuration is used to set up the organization structure in 
Power Platform. 
2. [Mandatory] Configure the importing channels for invoice images. 
The solution supports the following channels: 
 - Office 365 Outlook (Default) 
 - Outlook.com
 - OneDrive
 - SharePoint 
3. [Optional] Define additional configuration groups for the OCR service. 
4. [Optional] Define mapping rules for the legal entity, vendor account, item and procurement type. 

### Manage legal entity

Dynamics 365 Finance defines legal entities as organizations that are identified through registration with legal authorities. Business activities are performed and recorded in separate legal entities. In Power Platform, business units, security roles, and users are linked together that conforms to the role-based security model. Business units are used together with security roles to control data access, user will see the information they need to do their jobs. The solution provides a configuration space to load basic information from existing legal entities in Dynamics 365 Finance and managing those created manually. The legal entities are used in vendor invoices and security control. When a legal entity is created and shown in the list view, the default business unit and team with the same name will be created automatically. The team will be granted the security role of “AP Clerk”. When legal entities are imported, basic master data from Dynamics 365 Finance is imported. It identifies the nonexistent items by legal entity and adds them into the solution. New legal entities will be assigned with the default configuration group. 


#### Sync legal entities

To sync legal entities, go to **Setup > System setup > Manage legal entities**. 
Click **Sync legal entities > OK** in the confirmation dialog. 

The number of new legal entities will be displayed after the sync is complete. The new legal entities will display in the list view. 
The default configuration group is applied to new legal entities. You can't create legal entities directly but you can sync legal entities from Dynamics 365 Finance. 

#### Invoice import channel
Invoices are sent from different channels (email, file workspace, invoice portal) via different formats (paper, image) by vendors. The solution can handle different channels and formats via flexible configuration. The following types are supported: 
 - Office 365 Outlook 
 - Outlook.com 
 - SharePoint 
 - OneDrive 

Upon creating a channel for a specific account, an automated flow with pre-defined template will be constructed to monitor the coming emails/files in the inbox/space. Any file with a valid invoice can be recognized and sent to the invoice area, waiting for the AP clerk to process. The format of the attachment should be PDF or image.  Invoices can be loaded into our solution according to channel configuration. 

1) Create a channel 
If you've imported the addition solution package (Invoice capture installation tools), the default connection for Office 365 Outlook is ready to use. If you want to create more connections for different email account or other channel types, see how to define connections in Create connections for channels. 
To create a channel, go to **Setup > System setup > Config channels**, click **New**. 

Fill in the following fields:
 - **Channel name** 
 - **Description** 
 - **Type** 
 - **Connection** 
 
Only emails or files that match the criteria can be imported into the solution. 

2) Active the channel 
When a flow is saved, fields will be displayed to show the status of the channel and created time. Initially, the **Status** will be **Inactive**. 
The **Status reason** field displays that the channel is initialized and ready to be activated.

Click **Activate**, the **Status** and **Status reason** fields will be updated.

A channel can be deactivated if it is not needed. Click **Deactivate**, the channel will be disabled. The **Status** and **Status reason** fields will be updated. 

### Manage flow in flow management

The channel can be viewed on **Config channels**, or in flow management. To see more details, go to **Admin system > Default solution > Cloud flows**.

Select the target flow to see more details, such as linked connections, owners, and run histories.

To sync the status, select **Check** to confirm the status of the channel is the same status as in the flow. 

There are some cases of exception handling that are shown in the **Status reason** field: 
 - **Missing Dataverse connection**: This displays when current user doesn't create at least one connection reference of **Microsoft Dataverse**.  
 - **Not found**: This displays when the flow linked to the channel has been deleted in flow management. The channel should be saved again to create a new channel. 
 - **Deactivated in flow management**: This displays when the flow has been deactivated in flow management and the status of channel is different than the flow. 
 - **Activated in flow management**: The displays when the flow has been activated in flow management and the status of channel is different than the flow.




