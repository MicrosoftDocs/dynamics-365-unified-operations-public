---
# required metadata

title: Customize application startup by using delegates
description: This topic explains how you can add new data sources to existing forms by using extensions.
author: jorisdg
manager: AnnBe
ms.date: 11/03/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 


# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: rhaertle
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.custom: 268724
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: jorisde
ms.search.validFrom: 2017-07-01
ms.dyn365.ops.version: Platform update 4

---

# Customize application startup by using delegates

[!include [banner](../includes/banner.md)]

In Dynamics AX 2012, there were customization points that allowed you to subscribe to events (Application.Startup delegates) that were raised when the client was initializing. These events were deprecated because there is no concept of a rich client. On the server, only server sessions are considered, however because you can migrate logic from previous releases, new events have been added to the **ApplicationStartupEventManager** class. 

The following sections highlight the new data sources that you can add to existing forms by using extensions.

## static delegate void onSystemStartup()
- This event occurs when the system starts up. 
- It is raised once per AOS upon startup.

## static delegate void onFirstTimeUserInteractiveSessionCreated()
- This event occurs when the system is creating an interactive session for the first time for a user. 
- It is raised once per user per AOS.

## static delegate void onFirstTimeUserNonInteractiveSessionCreated()
- This event occurs when the system is creating a non-interactive session for the first time for a user. 
- It is raised once per user per AOS.

## static delegate void onInteractiveSessionCreated()
- This event occurs when an interactive session is created and ready for use. 
- It is raised once per interactive session creation for any user.

## static delegate void onSessionCreated(boolean _isBatch, boolean _isInteractive)
- This event occurs when the session is created and ready for use. 
- It is raised once per interactive session creation for any user.
- *_isBatch* specifies whether the system is running a batch job.
- *_isInteractive* specifies whether the session is interactive.

