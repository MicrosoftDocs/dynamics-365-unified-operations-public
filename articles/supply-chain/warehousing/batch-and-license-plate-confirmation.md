---
title: Batch, serial, and license plate confirmation
description: This article describes how to set up and apply batch, serial, and license plate confirmation from a mobile device.
author: adesypri
ms.author: adesypri
ms.reviewer: kamaybac
ms.search.form: WHSRFAutoConfirm
ms.topic: how-to
ms.date: 08/03/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Batch, serial, and license plate confirmation

[!include [banner](../includes/banner.md)]

Batch confirmation allows workers using a mobile device to confirm that the correct batch is being picked. For *Batch-above\[location\]* items (where batch-above indicates that batch is placed higher than location in the search hierarchy) the worker must verify that the batch that is picked matches the batch on the work line.

Serial confirmation allows workers using a mobile device to confirm that the correct serial number is being picked. For *Serial-above\[location\]* items (where the serial-above indicates that serial is placed higher than location in the search hierarchy) the worker must verify that the serial that is picked matches the serial on the work line.

License plate confirmation allows workers using a mobile device to confirm that the correct license plate is being picked. When picking work from a stage location, the worker must verify that the license plate that is picked matches the license plate that is associated with the work. If the work is started by scanning a license plate, this confirmation step is skipped.

## Where it applies

Confirmation applies in the following scenarios:

- Batch confirmation applies to the initial pick work for *Batch-above\[location\]* items.
- Serial confirmation applies to the initial pick work for *Serial-above\[location\]* items.
- License plate confirmation applies to picks from stage locations.

> [!IMPORTANT]
> Replenishment is not supported for license plate confirmation. When executing replenishment work, no license plate confirmation step is created.

## Set up batch, serial, and license plate confirmation

You can configure batch, serial and license plate confirmation from the **Mobile device menu items** page.

1. Open the **Mobile device menu items** page.
1. On the list pane, select the menu item that you want to set up.
1. On the Action Pane, select **Work confirmation setup**.
1. The **Work confirmation setup** page opens.
1. Use the buttons on the Action Pane to add rows for each work type as required. For rows with a **Work type** of *Pick*, select the check box for each type of confirmation that should be required by the current menu item. You can only select these confirmation options for rows that don't have **Auto confirm** enabled.  

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
