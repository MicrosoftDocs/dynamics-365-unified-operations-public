---
title: Batch, serial, license plate and location confirmation
description: Learn how to set up and apply batch, serial, license plate and location confirmation from a mobile device with an outline on where it applies.
author: Mirzaab
ms.author: mirzaab
ms.topic: how-to
ms.date: 08/03/2023
ms.custom: bap-template
ms.reviewer: kamaybac
ms.search.form: WHSRFAutoConfirm
---

# Batch, serial, and license plate confirmation

[!include [banner](../includes/banner.md)]

Batch confirmation allows workers using a mobile device to confirm that the correct batch is being picked. For *Batch-above\[location\]* items (where batch-above indicates that batch is placed higher than location in the search hierarchy) the worker must verify that the batch that is picked matches the batch on the work line.

Serial confirmation allows workers using a mobile device to confirm that the correct serial number is being picked. For *Serial-above\[location\]* items (where the serial-above indicates that serial is placed higher than location in the search hierarchy) the worker must verify that the serial that is picked matches the serial on the work line.

License plate confirmation allows workers using a mobile device to confirm that the correct license plate is being picked. When picking work from a stage location, the worker must verify that the license plate that is picked matches the license plate that is associated with the work. If the work is started by scanning a license plate, this confirmation step is skipped.

Location confirmation allows workers using a mobile device to confirm that the correct location is beign used when performing any of the work types available. During these tasks, the worker must verify that the location matches the one associated with the work. The user will be prompted to input the check digit setup in the location, if there is no check digit associated with the location, this step will be skipped.

## Where it applies

Confirmation applies in the following scenarios:

- Batch confirmation applies to the initial pick work for *Batch-above\[location\]* items.
- Serial confirmation applies to the initial pick work for *Serial-above\[location\]* items.
- License plate confirmation applies to picks from stage locations.
- Location confirmation only applies when the location is filled automatically by the system. 

> [!IMPORTANT]
> Replenishment is not supported for license plate confirmation. When executing replenishment work, no license plate confirmation step is created.
>
> For location confirmation, if the location is manually entered on the mobile device, the location confirmation step will be skipped. For example, during the manual inventory movement process, the system will not prompt for location confirmation even if it is enabled in the menu item.

## Set up batch, serial, license plate and location confirmation

You can configure batch, serial, license plate and location confirmation from the **Mobile device menu items** page.

1. Go to **Warehouse management \> Setup \> Mobile device \> Mobile device menu items**.
1. On the list pane, select the menu item that you want to set up.
1. On the Action Pane, select **Work confirmation setup**.
1. The **Work confirmation setup** page opens.
1. Use the buttons on the Action Pane to add rows for each work type as required, select the check box for each type of confirmation that should be required by the current menu item:
    - For rows with a **Work type** of *Pick*, you can only select the batch, serial and license plate confirmation options, as well as the location confirmation.
    - For rows with with any other **Work type**, you can select the location confirmation option, but the batch, serial and license plate confirmation options are not available.

> [!IMPORTANT]
> If the **Auto submit** option is enabled, the other options cannot be activated.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]