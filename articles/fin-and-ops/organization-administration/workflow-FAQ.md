---
# required metadata

title: Workflow FAQ
description: This topic answers frequently asked questions about the workflow system in Microsoft Dynamics 365 for Finance and Operations.
author: sericks007
manager: AnnBe
ms.date: 02/28/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User, IT Pro
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 56381
ms.assetid: 20b78595-e1d9-439a-ae1c-a776a3438919
ms.search.region: Global
# ms.search.industry: 
ms.author: tjvass
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Workflow system

[!include [banner](../includes/banner.md)]

This topic describes the workflow system in Microsoft Dynamics 365 for Finance and Operations.

## Notifications

### Why are double notifications received when a work item is rejected?
When a work item is rejected, that work item is completed as rejected and another work item is created and assigned to the originator. 
There is a notification to the originator for the rejected work item and a separate notification to the user assigned to the new "change requested" work item. 
Each notification is for a different work item, but the similarity can cause confusion. We are looking at ways to improve this story in the future.
