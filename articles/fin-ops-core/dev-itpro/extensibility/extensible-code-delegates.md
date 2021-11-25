---
title: Delegates
description: This topic provides information about how to write extensible code and delegates.
author: MichaelFruergaardPontoppidan
ms.date: 09/09/2018
ms.topic: article
ms.prod: 
ms.technology: 


# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: tfehr
# ms.tgt_pltfrm: 
ms.custom: 268724
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: mfp
ms.search.validFrom: 2018-09-09
ms.dyn365.ops.version: Platform update 20
---


# Delegates
[!include [banner](../includes/banner.md)]

Although you can subscribe to existing delegates, don't create new delegates. The Chain of Command (CoC) provides a richer, more robust, and more concise extension mechanism that supersedes delegates.

Instead of creating new delegates, structure your code in small methods that have good names, as described in the [guidelines for writing extensible methods](extensible-methods.md).

If you decide to use delegates, consider ensuring no more than one response where applicable. For more information, see [EventHandlerResult classes in request or response scenarios](../dev-tools/event-handler-result-class.md).


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
