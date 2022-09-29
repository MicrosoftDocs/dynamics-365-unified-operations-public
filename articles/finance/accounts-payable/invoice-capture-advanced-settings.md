---
# required metadata

title: Invoice capture solution advanced settings
description: This article provides information about the advanced settings in the Invoice capture solution. 
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

# Invoice capture solution advanced settings

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

This article provides information about advanced settings in the Invoice capture solution. 

## Create additional connections for channels  

The connections to email or file storage need to be created for monitoring incoming invoices from different channels. It is necessary to register connections at the 
beginning to grant access for automated flows used in the solution.  

To import invoices, the following connection types are used:  
 - Office 365 Outlook 
 - Outlook.com
 - OneDrive
 - SharePoint 

The **Channel for invoice importing** will utilize the connections in further configuration steps. Before creating a channel of a specific connection, the user needs to
be granted the security role of admin and create connections below.  

1. To create a connection to Microsoft Dataverse, go to **Admin system > Default solution**, click **New** and select **Connection Reference**. 
2. Enter information in the **Display name** field 
3. Select **Microsoft Dataverse** as the connector. The first time setting up the connection, click **New connection**. 
4. The new popup page will let the user create a Microsoft Dataverse connection, click **Create**.
5. Enter the Dataverse account and password. 
6. After validation, go to the connection page, click **Refresh**, select the account, then **Create**. 


To create an email/file storage connection, follow these steps:
1. Go to the **Connection creation** page, select the **Connection type** as “Office 365 Outlook” instead.
2. The email connection can be **Outlook.com** or **Office 365 Outlook** as the connector. 
3. The file storage connections contain either **OneDrive** or **SharePoint**. 

Existing connections can be checked in **Default solution > Objects > Connection References**. The user that creates channels should have at least one Microsoft 
Dataverse connection and the specific email/file connections. The owner of the connection should be the same as the creator of the new channel. 





