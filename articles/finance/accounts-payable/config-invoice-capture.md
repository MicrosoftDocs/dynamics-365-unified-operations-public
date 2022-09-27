---
# required metadata

title: Configure the Invoice capture service 
description: This article provides information about configuring the Invoice capture service. 
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
1. [Mandatory] Syncronize the legal entities from Dynamics 365 finance and operations environment. This configuration is used to set up the organization structure in 
Power Platform. 
2. [Mandatory] Configure the importing channels for invoice images. 
The solution supports the following channels: 
 - Office 365 Outlook (Default) 
 - Outlook.com
 - OneDrive
 - SharePoint 
3. [Optional] Define additional configuration group for the OCR service. 
4. [Optional] Define mapping rules for the legal entity, vendor account, item and procurement type. 

### Manage legel entity

Dynamics 365 finance and operations define legal entities as organizations that are identified through registration with legal authorities. Business activities are performed and recorded
in separate legal entities. In Power Platform, business units, security roles, and users are linked together that conforms to the role-based security model. 
Business units are used together with security roles to control data access, user will see the information they need to do their jobs. The solution provides a 
configuration space to load basic information from existing legal entities in Dynamics 365 finance and operations, as well as managing those created manually. The legal
entities are used in vendor invoices and security control. When a legal entity is created and shown in the list view, the default business unit and team with the same
name will be created automatically. The team will be granted the security role of “AP Clerk”. When legal entities are imported, basic master data from Dynamics 365
finance and operations is imported. It identifies the nonexistent items by Legal entity and add them into the solution. New legal entities will be assigned with the 
default configuration group, to individualize the settings during invoice processing. Section 3.3 describes more details on the Configuration Group. 
