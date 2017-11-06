---
# required metadata

title: Perform business actions throughout the lifecycle of a table record
description: This topic provides information about business actions that you can perform throughout the lifecycle of a table record.
author: ivanv-microsoft
manager: AnnBe
ms.date: 07/11/2017
ms.topic: index-page
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 


# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: robinr
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.custom: 268724
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: ivanv
ms.search.validFrom: 2017-07-01
ms.dyn365.ops.version: Platform update 4

---

# Perform business actions throughout the lifecycle of a table record

As part of your business workflows, records are regularly inserted, updated, and deleted. To customize the system behavior, you can hook into some of the record operations that are most often used. For example, you can fill additional fields on the record, perform additional data validation, or insert additional data into related tables. Several events that are available on the table let you achieve those customizations through extensions. Your code can subscribe to these events, and can insert your logic before or after the event is run.

For a list of the events that you can subscribe to, see the "Table extensions" section in [Customize with extensions and overlayering](customization-overlayering-extensions.md#table-extensions).
