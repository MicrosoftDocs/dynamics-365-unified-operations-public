---
title: Customize application startup by using delegates
description: Learn about how to customize application startup by using delegates, including overviews of various event types.
author: josaw1
ms.author: josaw
ms.topic: article
ms.date: 03/27/2026
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2017-07-01
ms.dyn365.ops.version: Platform update 4
---

# Customize application startup by using delegates

[!include [banner](../includes/banner.md)]

In Dynamics AX 2012, customization points allowed you to subscribe to events (Application.Startup delegates) that the client raised when initializing. These events are deprecated because there's no concept of a rich client. On the server, only server sessions are considered. However, because you can migrate logic from previous releases, new events are added to the **ApplicationStartupEventManager** class.

The following sections highlight the new data sources that you can add to existing forms by using extensions.

## static delegate void onSystemStartup()

- This event occurs when the system starts up.
- It raises once per AOS upon startup.

## static delegate void onFirstTimeUserInteractiveSessionCreated()

- This event occurs when the system creates an interactive session for the first time for a user.
- It raises once per user per AOS.

## static delegate void onFirstTimeUserNonInteractiveSessionCreated()

- This event occurs when the system creates a non-interactive session for the first time for a user.
- It raises once per user per AOS.

## static delegate void onInteractiveSessionCreated()

- This event occurs when an interactive session is created and ready for use.
- It raises once per interactive session creation for any user.

## static delegate void onSessionCreated(boolean _isBatch, boolean _isInteractive)

- This event occurs when the session is created and ready for use.
- It raises once per interactive session creation for any user.
- *_isBatch* specifies whether the system is running a batch job.
- *_isInteractive* specifies whether the session is interactive.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
