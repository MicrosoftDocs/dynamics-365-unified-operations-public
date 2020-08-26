---
# required metadata

title: Collections process automation
description: This topic describes how to set up collections process strategies that automatically identify customer invoices that require an e-mail reminder, collection activity (such as a phone call), or a collection letter to be sent to the customer. 
author: panolte
manager: AnnBe
ms.date: 08/26/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form:  CustomerCollectionManagerWorkspace
audience: Application User, IT Pro
# ms.devlang: 
ms.reviewer: roschlom
ms.search.scope: Core, Operations 
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: shpandey
ms.search.validFrom: 2017-08-26 
ms.dyn365.ops.version: 10.0.13 
---

# Collections process automation

[!include [banner](../includes/banner.md)]

This topic describes how to set up collections process strategies that automatically identify customer invoices that require an e-mail reminder, collection activity (such as a phone call), or a collection letter to be sent to the customer. 

Organizations spend a significant amount of time researching aged balance reports, customer accounts and open invoices to determine which customers need to be contacted about an open invoice or account balance.  This research takes times away from a collection agent’s time spent communicating with customers to collect past due balances or resolving invoice disputes.  Collections process automation lets you set up a strategy-based approach to your collection process. This approach helps you apply collection activities consistently byproviding customized e-mail reminders, or programmed process for sending collection letters. 

## Collections process setup
You can use **Collections process setup** (**Credit and collections > Setup > Collections process setup**) to create an automated collections process that will schedule activities, send email messages, and create and post customer collection letters.  The process steps are based off the leading or oldest open invoice.  Each step uses this invoice to determine what communication or activity should take place with a specific customer.  

