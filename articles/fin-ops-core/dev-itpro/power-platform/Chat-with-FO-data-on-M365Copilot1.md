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
With a M365 copilot license, an authorized user can enter into a natural language conversation with F&O data and ask questions like "what is the overdue balance for the customer forest wholesales?", "summarize the collection status", "what is the on-hand inventory for product Southridge Video Laptop16 M1601 in Silver color?". M365 Copilot summarizes the information spread across emails, chats, and documents and reconciles it with the relevant data residing inside F&O apps. The reconciled summary is presented as the response to the user.  

## What types of data are supported? 
Data residing inside tables are referred as structured data. Data present in a static document like word, pdf, publicly available contents etc. are referred as unstructured data. M365 Copilot supports data inquiry against both structured and unstructured data. However, for this release the F&O scope is limited to structured data only.

## What are the supported customer scenarios?
Finance scenario - <embed the recording>
Supply Chain scenario - <embed the recording>

## What is happening behind the scenes?
User question is translated into a FetchXML query and executed against F&O database through virtual entities. The results are summarized and responded to the user. Here is the architecture that works behind the scenes.
<include the detailed architecture diagram>

## Are we limited to the supported scenarios?
No, we are not limited to the above supported scenarios. Think of these scenarios as patterns which M365 Copilot can process. All F&O entities which follow these pattern can be enabled for copilot as they are supported by virtual entities.  Here is the list of entities eligible for virtualization - <include link to santhosh's spreadsheet list>

## How can I setup M365 copilot for my F&O data?
For this you need F&O version <> and Dataverse version <> and F&O virtual entity solution provider version <>.
Once you upgrade, <copy page the steps from admin doc>

## Best practices 
While chatting with M365 Copilot, follow these best practices: 
<add details from Hua's doc>
