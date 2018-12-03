---
# required metadata

title: System administrator network printers
description: This topic provides information about using the System administrator network utility to set up network printers.
author: tjvass
manager: AnnBe
ms.date: 12/03/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 62333
ms.assetid: 6135bcf7-bf8f-42ae-b2c6-458f6538e6a4
ms.search.region: Global
# ms.search.industry: 
ms.author: tjvass
ms.search.validFrom: 2018-12-04
ms.dyn365.ops.version: AX 7.0.0

---

# System administrator network printers

[!include [banner](../includes/banner.md)]

[!include [banner](../includes/private-preview-banner.md)]

> [!IMPORTANT]
> Access to the new System administration utility is managed by the Carbon Flighting Service. Platform Update 23 includes the **System network printers management** form for System administrators. 

Domain Administrators register the network printers with the Dynamics 365 for Finance and Operations service using the Document Routing Agent (DRA). After the printers are registered, it’s the responsibility of the Organization administrator to make printers available to end users. These settings are managed in the **Network printers** form (**Organization administration** > **Setup** > **Network printers**).   
 
Because the settings presented in this form are intended for Organization administrators, the data is restricted to the active legal entity. System administrators can't manage network printer settings across legal entities. This makes it difficult to update settings across Legal Entities in response to network printer changes. 
SCENARIOS 
System administrator needs to Delete a network printer instance – this is common for cases where the network printer path is updated or hardware has been replaced 
Organization wants to purge all documents in the printer queue – documents rendered by service that are waiting to be printed can be deleted using options available in the System network printers form 
Quickly toggle availability of network printers for multiple legal entities – manage the printer properties including the Active state for a printer in multiple Legal Entities using a single view (Coming soon…!) 
Provide friendly names for network printers for multiple legal entities – establish friendly names and descriptions for printers the makes sense to the users associated with individual Legal Entities (Coming soon…!) 
This is both a recovery tool for inadvertent print instructions and a means of simplifying the task of managing network printer settings including access from specific Legal Entities. 

Page Break
 
How do I access the feature? 
Once the feature has been enabled through Feature Flighting, a Preview link will appear in the Organization administration > Setup > Network printers form 
 
Click on the System network printers link 
This navigates you directly into the System network printers form.  After registering network printers with the service using the DRA, you will see the configuration information for each Legal Entity in the organization. 
 
What options do I have? 
Currently, the administration tool is limited to support Delete operations only.  However, we will be lighting up the ability to Edit settings for individual Legal Entities using this form in a future update.   
Deleting network printers using the management form triggers the following events: 
All documents in the printer queue directed at the printer are deleted 
Network printer is deleted for all Legal Entities in the organization 
Domain admins may register devices using the old printer name 
Organization admins may continue to use the existing tools to manage network printer settings for a single Legal Entity 
 


