---
# required metadata

title: Batch and license plate confirmation
description: This topic describes how to set up and apply batch and license plate confirmation from a mobile device.
author: Mirzaab
manager: AnnBe
ms.date: 05/26/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  WHSRFAutoConfirm
audience: Application User
# ms.devlang: 
ms.reviewer: bis
ms.search.scope: Core, AX 7.0.0, Operations, UnifiedOperations
# ms.tgt_pltfrm: 
ms.custom: 269384
ms.search.region: Global
# ms.search.industry: 
ms.author: mirzaab
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Batch and license plate confirmation

[!include[banner](../includes/banner.md)]

Batch confirmation allows you to confirm that the correct batch is being picked from the mobile device. On the initial pick of work for batch above-items only, where batch above indicates that batch ranges higher than location in the search hierarchy, you must verify that the batch that is picked matches the batch on the work line. 

License plate confirmation allows you to confirm that the correct license plate is being picked from the mobile device. When picking work from a stage location, you must verify that the license plate that is picked matches the license plate that is associated with the work. If the work is started by scanning a license plate, this confirmation step will be skipped.

## Where it applies
Confirmation applies in the following scenarios:

- Batch confirmation applies to the initial picks of work for batch above-items.
- License plate confirmation applies to picks from stage locations.

## Set up batch and license plate confirmation
You can configure batch and license plate confirmation from the mobile device menu items.  
1.	From the mobile device menu items, enter the work confirmation setup.  
2.	Select the option for either batch or license plate confirmation. Both options are available for work type picks that do not have automatic confirmation enabled.  
