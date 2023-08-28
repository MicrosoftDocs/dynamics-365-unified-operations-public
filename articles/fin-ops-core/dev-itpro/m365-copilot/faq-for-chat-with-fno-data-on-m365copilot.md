---
# required metadata

title: Chat with finance and operations data on Microsoft 365 Copilot
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

# Chat with finance andoOperations data on Microsoft 365 Copilot 

[!include[banner](../includes/banner.md)]

This article explains how to chat with finance and operations data with Microsoft 365 Copilot using virtual entities in Microsoft Dataverse.

## Overview
With a Microsoft 365 Copilot license, an authorized user can enter into a natural language conversation with finance and operations data and ask questions like:

* What is the overdue balance for the customer forest wholesales?
* Summarize the collection status.
* What is the on-hand inventory for product Southridge Video Laptop 16 M1601 in Silver color?

Microsoft 365 Copilot summarizes the information spread across emails, chats, and documents, and reconciles it with the relevant data residing inside finance and operations apps. The reconciled summary is presented as the response to the user.  

## What types of data are supported? 
Data residing inside tables are referred as structured data. Data present in a static document like word, pdf, and publicly available contents, are referred as unstructured data. Microsoft 365 Copilot supports data inquiry against both structured and unstructured data. For this release, the finance and operations scope is limited to structured data only.

## What are the supported customer scenarios?

Finance scenario - Inquire collection status on Microsoft 365 Copilot

[!VIDEO https://learn-video.azurefd.net/vod/player?id=2ea4ece0-c783-4410-8042-55569c5bb9f1] 

Supply Chain scenario - Inquire on hand inventory on Microsoft 365 Copilot

[!VIDEO https://learn-video.azurefd.net/vod/player?id=7f051a6f-0d45-41b4-b4c7-cd5d4166b38d] 

## What is happening behind the scenes?
The user's question is translated into a FetchXML query and executed against finance and operations database through virtual entities. The results are summarized and responded to the user. The following graphic shows the architecture that works behind the scenes.

[A graphic image that shows the data flow between finance and operations apps and Microsoft 365 Copilot](media
/finops-structured-data-architecture.png)

## Are we limited to the supported customer scenarios?
No, we aren't limited to the supported customer scenarios. Think of these scenarios as patterns which Microsoft 365 Copilot can process. All finance and operations entities that follow these patterns can be enabled for Copilot and support virtual entities.  Here's the list of entities eligible for virtualization.

However, the language translation support for preview is “en-us”. 

## How can I set up Microsoft 365 Copilot for my finance and operations data?

Before you can set up Microsoft 365 Copilot for your finance and operations data, you need to have the following software versions installed:

- Finance and operations version 10.0.35 PU59 (10.0.1627.75) or later.
- Dataverse version 9.2 or later, and finance and operations virtual entity solution provider version 2.8.7 or later. 

If you wish to try built-in scenarios, install two app source packages:
- Finance package: [Copilot in Microsoft Dynamics 365 Finance](https://appsource.microsoft.com/product/dynamics-365/mscrm.d365-financeai-preview?flightCodes=9b882e82e59c4f35a1b0a5368d42ea92&tab=DetailsAndSupport)
- Supply chain package 

If you want to try your entities, enable them as virtual entities. For more information on enabling virtual entities, see [Enable Microsoft Dataverse virtual entities](../power-platform/enable-virtual-entities.md). 

Configure the following properties at the entity level.

* ChangeTrackingEnabled=1
*	CanEnableSyncToExternalSearchIndex=1
*	SyncToExternalSearchIndex=1

Configure the following properties at the entity field level:

*	IsSearchable=1


## Best practices 
While chatting with Microsoft 365 Copilot, follow these best practices: 
*	If your question is about a customer, then use the **customer** keyword in your question. For example, instead of asking "what is the amount due for forest wholesales?", ask "what is the amount due for customer forest wholesales?". 
*	In case you want the results to be displayed in table format, use the **in table format** keyword." For example, ask "what is the availability of surface pro 128 GB? Give me the details by site, warehouse and color in table format."
*	If you remember the name or label associated with the given data inside finance and operations apps, use that name while searching to make the search easy. For example, what customers owe is displayed in finance and operations forms in the **Balance due** column. So, instead of asking "how much does the customer forest wholesales owe?", ask "what is the outstanding balance of customer forest wholesales?"


