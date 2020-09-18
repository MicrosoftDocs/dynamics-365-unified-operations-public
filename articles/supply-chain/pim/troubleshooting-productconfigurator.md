---
# required metadata

title: Troubleshoot Product Configurator
description: This topic describes how to fix issues that you might encounter while working with Product Configurator.
author: SmithaNataraj
manager: tfehr
ms.date: 05/07/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: smnatara
ms.search.validFrom: 2020-5-7
ms.dyn365.ops.version: AX 10.0.14

---
# Troubleshoot Product Configurator
This topic describes how to fix common issues that you might encounter while working with Product Configurator.

## Salesline configurator overwrites item text 
This issue happens when a sales order line for a configurable item is created and the item text is modified. When the item is configured and the ok is selected, the text is overwritten with the standard text.

**Resolution**
This is working as expected. The text field includes the variant name that is populated only after the line is configured. Therefore, if the text needs to be changed, it must be done after the line is configured and not before.
