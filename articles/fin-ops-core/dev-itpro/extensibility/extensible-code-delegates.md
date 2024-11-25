---
title: Delegates
description: Learn about how to write extensible code and delegates. If you decide to use delegates, consider ensuring no more than one response where applicable.
author: MichaelFruergaardPontoppidan
ms.author: mfp
ms.topic: article
ms.date: 09/09/2018
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2018-09-09
ms.dyn365.ops.version: Platform update 20
---


# Delegates
[!include [banner](../includes/banner.md)]

Although you can subscribe to existing delegates, don't create new delegates. The Chain of Command (CoC) provides a richer, more robust, and more concise extension mechanism that supersedes delegates.

Instead of creating new delegates, structure your code in small methods that have good names, as described in the [guidelines for writing extensible methods](extensible-methods.md).

If you decide to use delegates, consider ensuring no more than one response where applicable. For more information, see [EventHandlerResult classes in request or response scenarios](../dev-tools/event-handler-result-class.md).


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
