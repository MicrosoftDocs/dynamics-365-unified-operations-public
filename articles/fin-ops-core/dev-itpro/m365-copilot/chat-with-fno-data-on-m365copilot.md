---
# required metadata

title: Chat with Finance and Operations data on Microsoft 365 Copilot
description: This article explains how to chat with finance and operations data with Microsoft 365 Copilot using virtual entities in Microsoft Dataverse.
author: ramasri
ms.date: 08/15/2023
ms.topic: article
ms.prod:
ms.technology: 

# optional metadata

# ms.search.form:
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: johnmichalak
# ms.tgt_pltfrm: 
# ms.custom: NotInToc
ms.search.region: Global
# ms.search.industry:
ms.author: ramasri
ms.search.validFrom: 09/01/2023
ms.dyn365.ops.version: 10.0.35 PU59
---

# Chat with Finance and Operations data on Microsoft 365 Copilot 
[!include[banner](../includes/banner.md)]

## Overview
With a Microsoft 365 Copilot license, an authorized user can enter into a natural language conversation with finance and operations data and ask questions like "what is the overdue balance for the customer forest wholesales?", "summarize the collection status", "what is the on-hand inventory for product Southridge Video Laptop16 M1601 in Silver color?". Microsoft 365 Copilot summarizes the information spread across emails, chats, and documents and reconciles it with the relevant data residing inside finance and operations apps. The reconciled summary is presented as the response to the user.  

## What types of data are supported? 
Data residing inside tables are referred as structured data. Data present in a static document like word, pdf, publicly available contents etc. are referred as unstructured data. Microsoft 365 Copilot supports data inquiry against both structured and unstructured data. However, for this release, the finance and operations scope is limited to structured data only.

## What are the supported customer scenarios?
Finance scenario 

![Inquire collection status on Microsoft 365 Copilot](media/Inquire-collection-status.mp4)

Supply Chain scenario

![Inquire onhand inventory on Microsoft 365 Copilot](media/Inquire-onhand-inventory.mp4)

## What is happening behind the scenes?
User question is translated into a FetchXML query and executed against finance and operations database through virtual entities. The results are summarized and responded to the user. Here's the architecture that works behind the scenes.

## Are we limited to the supported customer scenarios?
No, we aren't limited to the supported customer scenarios. Think of these scenarios as patterns which Microsoft 365 Copilot can process. All finance and operations entities that follow these patterns can be enabled for Copilot as they're supported by virtual entities.  Here's the list of entities eligible for virtualization.

However, the language translation support for preview is “en-us”. 

## How can I set up Microsoft 365 Copilot for my finance and operations data?
For this you need finance and operations version 10.0.35 PU59 (10.0.1627.75) or above and Dataverse version 9.2 or above and finance and operations virtual entity solution provider version 2.8.7 or above. 

If you wish to try built-in scenarios, install two appsource packages namely – <finance package link> and <supply chain package link>. 

If you wish to try your entities, [enable them as virtual entities](https://learn.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/power-platform/enable-virtual-entities). 

Configure the following properties at the entity level.
+	ChangeTrackingEnabled=1
+	CanEnableSyncToExternalSearchIndex=1
+	SyncToExternalSearchIndex=1

Configure the following properties at the entity field level:
+	IsSearchable=1


## Best practices 
While chatting with Microsoft 365 Copilot, follow these best practices: 
1.	If your question is about a customer, then use "customer" keyword in your question. For example, instead of asking "what is the amount due for forest wholesales?", you should be asking "what is the amount due for customer forest wholesales?". 
2.	In case you want the results to be displayed in table format, use the keyword "in table format.". For example, "what is the availability of surface pro 128 GB? Give me the details by site, warehouse and color in table format.
3.	If you remember the name or label associated with the given data inside finance and operations apps, use that name while searching. This makes the search easy. For example, what customer owe is displayed in finance and operations forms under "balance due" column. So, instead of asking "how much the customer forest wholesales owe?", you can ask "what is the outstanding balance of customer forest wholesales?".


