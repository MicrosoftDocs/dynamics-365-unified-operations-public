---
# required metadata

title: Batch, serial and license plate confirmation
description: This article describes how to set up and apply batch, serial and license plate confirmation from a mobile device.
author: adesypri
ms.date: 03/08/2023
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form:  WHSRFAutoConfirm
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.custom: 269384
ms.search.region: Global
# ms.search.industry: 
ms.author: mirzaab
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Batch, serial and license plate confirmation

[!include [banner](../includes/banner.md)]

Batch confirmation allows you to confirm that the correct batch is being picked from the mobile device. On the initial pick of work for *Batch-above\[location\]* items only, where batch-above indicates that batch is placed higher than location in the search hierarchy, you must verify that the batch that is picked matches the batch on the work line.

Serial confirmation allows you to confirm that the correct serial number is being picked from the mobile device. On the initial pick of work for *Serial-above\[location\]* items only, where the serial-above indicates that serial is placed higher than location in the search hierarchy, you must verify that the serial that is picked matches the serial on the work line.

License plate confirmation allows you to confirm that the correct license plate is being picked from the mobile device. When picking work from a stage location, you must verify that the license plate that is picked matches the license plate that is associated with the work. If the work is started by scanning a license plate, this confirmation step will be skipped.

## Where it applies

Confirmation applies in the following scenarios:

- Batch confirmation applies to the initial picks of work for batch above-items.
- Serial confirmation applies to the initial picks of work for serial above-items.
- License plate confirmation applies to picks from stage locations.

> [!IMPORTANT]
> Replenishment is not supported for license plate confirmation. When executing replenishment work, no license plate confirmation step is created.

## Set up batch, serial and license plate confirmation

You can configure batch, serial and license plate confirmation from the mobile device menu items.

1. From the mobile device menu items, enter the work confirmation setup.  
1. Select the option for either batch, serial or license plate confirmation. All options are available for work type picks that do not have automatic confirmation enabled.  


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
