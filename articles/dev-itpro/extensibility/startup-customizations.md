---
# required metadata

title: Use delegates for startup customizations
description: This topic explains how you can add new data sources to existing forms by using extensions.
author: robadawy
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
ms.reviewer: robinr
ms.search.scope: Operations, Platform
# ms.tgt_pltfrm: 
ms.custom: 268724
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: ivanv
ms.search.validFrom: 2017-07-01
ms.dyn365.ops.version: Platform update 4

---

# Use delegates for startup customizations

Some overlayering patterns for code in AX2012 have been replaced by delegates. Many applications are hooking up to the startup and shutdown sequence through customizing specific methods. Automatically transforming these to use the delegate instead would move these customizations out of ApplicationPlatform and contribute to eventually prohibiting customizations to it without creating extra work for the developer.

From Dynamics AX 2012, there were customization points to allow subscribing to events (through Application.Startup delegates) raised when the client is initializing.
In Rainier, we deprecated these events as there is no notion of a rich client. In the server only server sessions are considered.

To assist migrating logic from previous release, we have incorporated new events in the  ApplicationStartupEventManager class.

## static delegate void onSystemStartup()
    /// Event that occurs when the system starts up.
    /// The event is raised once per AOS upon startup.

## static delegate void onFirstTimeUserInteractiveSessionCreated() {}
    /// Event that occurs when the system is creating an interactive session for the first time for a user.
    /// The event is raised once per user per AOS.

## static delegate void onFirstTimeUserNonInteractiveSessionCreated() {}
    /// Event that occurs when the system is creating a non interactive session for the first time for a user.
    /// The event is raised once per user per AOS.

## static delegate void onInteractiveSessionCreated() {}
    /// Event that occurs when an interactive session is created and ready for use.
    /// The event is raised once per interactive session creation for any user.

## static delegate void onSessionCreated(boolean _isBatch, boolean _isInteractive) {}
    /// Event that occurs when the session is created and ready for use.
    /// <param name="_isBatch">Whether the system is running a batch job.</param>
    /// <param name="_isInteractive">Whether the session is interactive.</param>
    /// The event is raised once per user session creation for any user.

