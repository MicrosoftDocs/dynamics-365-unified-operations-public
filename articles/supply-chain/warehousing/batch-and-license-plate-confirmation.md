---
title: Batch, serial, license plate, and location confirmation
description: Learn how to set up and apply batch, serial, license plate and location confirmation from a mobile device.
author: Mirzaab
ms.author: mirzaab
ms.topic: how-to
ms.date: 02/23/2025
ms.custom: bap-template
ms.reviewer: kamaybac
ms.search.form: WHSRFAutoConfirm
---

# Batch, serial, license plate, and location confirmation

[!include [banner](../includes/banner.md)]

Batch confirmation allows workers using a mobile device to confirm that the correct batch is being picked. For *Batch-above\[location\]* items (where batch-above indicates that batch is placed higher than location in the search hierarchy) the worker must verify that the batch that is picked matches the batch on the work line.

Serial confirmation allows workers using a mobile device to confirm that the correct serial number is being picked. For *Serial-above\[location\]* items (where the serial-above indicates that serial is placed higher than location in the search hierarchy) the worker must verify that the serial that is picked matches the serial on the work line.

License plate confirmation allows workers using a mobile device to confirm that the correct license plate is being picked. When picking work from a stage location, the worker must verify that the license plate picked matches the license plate that is associated with the work. If the work is started by scanning a license plate, this confirmation step is skipped.

Location confirmation allows workers using a mobile device to confirm that the correct location is being used when performing any of the work types available. During these tasks, the worker must verify that the location matches the one associated with the work. The worker is prompted to enter the check digit for the location, but if no check digit is associated with the location, this step is skipped.

## Where it applies

Confirmation applies in the following scenarios:

- Batch confirmation applies to the initial pick work for *Batch-above\[location\]* items.
- Serial confirmation applies to the initial pick work for *Serial-above\[location\]* items.
- License plate confirmation applies to picks from stage locations.
- Location confirmation only applies when the location is filled automatically by the system.

> [!IMPORTANT]
> Replenishment isn't supported for license plate confirmation. When executing replenishment work, no license plate confirmation step is created.
>
> For location confirmation, the location confirmation step is skipped if the location is manually entered on the mobile device. For example, during the manual inventory movement process, the location isn't confirmed even if it's enabled in the menu item.

> [!IMPORTANT]
> If the entire quantity from a location or license plate is picked, the worker isn't asked to confirm the batch or serial numbers, regardless of how many batch or serial numbers are available on hand. This is standard tracking behavior that can't be overridden. For more information, see [Warehouse mobile device tracking dimensions and license plate  picking behavior](warehouse-mobile-device-tracking-dimensions-license-plate-picking-behavior.md).

## Set up batch, serial, license plate and location confirmation

You can configure batch, serial, license plate, and location confirmation from the **Mobile device menu items** page.

1. Go to **Warehouse management \> Setup \> Mobile device \> Mobile device menu items**.
1. On the list pane, select the menu item that you want to set up.
1. On the Action Pane, select **Work confirmation setup**.
1. The **Work confirmation setup** page opens.
1. To add rows for each work type, use the buttons on the Action Pane. Select the check box for each type of confirmation required by the current menu item.
    - For rows with a **Work type** of *Pick*, you can only select the batch, serial, license plate confirmation options, and location confirmation.
    - For rows with any other **Work type**, you can select the location confirmation option, but the batch, serial, and license plate confirmation options aren't available.

> [!IMPORTANT]
> If the **Auto submit** option is enabled, the other options can't be activated.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
