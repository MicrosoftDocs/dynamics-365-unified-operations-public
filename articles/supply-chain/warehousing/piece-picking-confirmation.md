---
title: Piece picking confirmation
description: Piece picking allows workers to use a mobile device to confirm each piece of inventory during picking or counting work.
author: Mirzaab
ms.author: mirzaab
ms.topic: how-to
ms.date: 05/26/2017
ms.reviewer: kamaybac
ms.search.form:  WHSRFAutoConfirm, WHSRFMenuItem
---

# Piece picking confirmation

[!include [banner](../includes/banner.md)]

*Piece picking* allows workers to use a mobile device to confirm each piece of inventory during picking or counting work. For picks, you can confirm the quantity of work to be processed up to the quantity that is specified on the work to be picked. For counting work, you can scan the inventory you're counting and track the total amount.

When you enable piece picking, product confirmation is also required. For picking work, you can set the maximum number of pieces that workers can be required to confirm while doing picking work. The maximum quantity is based on the current work unit that is being processed. The counting work type doesn't allow a maximum.

You can also use the quantity and unit of measure (UOM) that is associated with a scanned bar code. This works for receiving on inbound flows including mixed license plate receiving, purchase order item, transfer order item, and load item. It also works for piece picking, where scanning the bar code adds the quantity to the total number of confirmed pieces converting between the UOM on the bar code and the work unit. When counting the UOM on the bar code, if it's confirmed that the quantity is allowed for counting on the sequence group, the quantity is added to the total count.

> [!IMPORTANT]
> To allow workers to scan bar codes to confirm a product, make sure the **Scanning** option is enabled. You can do this by opening the bar code configuration and selecting the checkbox on the **General** tab.

## Where it applies

Piece picking works for all counting work and for the initial pick for any type of work. Piece picking doesn't apply for items that are controlled by serial numbers or for production or kanban picks from a license plate location where the item is set to staging.

## Set up piece picking

To set up piece picking, follow these steps:

1. Go to **Warehouse management** \> **Setup** \> **Mobile device** \> **Mobile device menu items**.
1. Find and select the mobile device menu item that you want to configure.
1. On the Action Pane, select **Work confirmation setup**.
1. Use the buttons on the Action Pane, to add, remove, or edit confirmation settings for each work type as needed. For rows with a **Work type** of *Pick* or *Counting*, make the following settings:
    - **Piece picking confirmation** – Select this check box to allow workers to confirm each piece of inventory from the mobile device. While this box is selected, the **Product confirmation** checkbox is also selected automatically.
    - **Maximum number of pieces** – Enter the maximum number of pieces that workers can be required to confirm while doing picking work. For example, if the **Maximum number of pieces** is set to *1*, the system will only prompt the worker to confirm one product. After that, the worker must manually enter the remaining quantity. This setting is only available when **Work type** is *Pick* and **Piece picking confirmation** is enabled.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
