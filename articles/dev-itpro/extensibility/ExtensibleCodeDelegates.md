---
# required metadata

title: Writing extensible code & delegates
description: This article describes usage of delegates..
author: mfp
manager: AnnBe
ms.date: 09/09/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 


# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.custom: 268724
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: ivanv
ms.search.validFrom: 2018-09-09
ms.dyn365.ops.version: Platform update 20
---


# Delegates

Do not create new delegates; but feel free to subscribe to existing delegates.  

Chain-of-command provides a richer, more robust and more concise extension mechanism that supersedes delegates.

Instead structure your code in small methods with good names following the [guidelines for writing extensible methods](Extensiblemethods.md).
